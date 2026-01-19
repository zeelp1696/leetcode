spiral_matrix_problem_1.md# Spiral Matrix Problem 1

**LeetCode Problem Link**: [Spiral Matrix (LeetCode 54)](https://leetcode.com/problems/spiral-matrix/)

## Problem Description

Given an `m x n` matrix, return all elements of the matrix in spiral order.

### Example:
Input:

[
[ 1, 2, 3 ],
[ 4, 5, 6 ],
[ 7, 8, 9 ]
]

Output: `[1, 2, 3, 6, 9, 8, 7, 4, 5]`

### Constraints:
- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 10`
- `-100 <= matrix[i][j] <= 100`

---

## Approach

The problem involves traversing the matrix in a **spiral order** starting from the outermost layer and working inwards. The traversal follows the order:

1. **Left to Right** along the top row
2. **Top to Bottom** along the right column
3. **Right to Left** along the bottom row (if there’s still space)
4. **Bottom to Top** along the left column (if there’s still space)

This process is repeated until all elements are visited. The matrix is processed layer by layer, with boundaries shrinking after each direction.

### Steps:
1. **Initialize boundaries**:
   - `top = 0`, `bottom = len(matrix) - 1`
   - `left = 0`, `right = len(matrix[0]) - 1`
2. **While loop** continues until the boundaries converge (`top <= bottom` and `left <= right`):
   - Traverse **top row (left to right)**, then increment `top`
   - Traverse **right column (top to bottom)**, then decrement `right`
   - If there are rows remaining, traverse **bottom row (right to left)**, then decrement `bottom`
   - If there are columns remaining, traverse **left column (bottom to top)**, then increment `left`
3. **Repeat** until the whole matrix is covered.

---

## Time Complexity:
- **O(m * n)**: Every element is visited once.

## Space Complexity:
- **O(1)**: In-place traversal, no additional space used.

---

## Code

```python
class Solution(object):
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        
        top, bottom = 0, len(matrix) - 1
        left, right = 0, len(matrix[0]) - 1
        res = []
        
        while top <= bottom and left <= right:
            
            # Traverse top row (left to right)
            for i in range(left, right + 1):
                res.append(matrix[top][i])
            top += 1
            
            # Traverse right column (top to bottom)
            for i in range(top, bottom + 1):               
                res.append(matrix[i][right])
            right -= 1
            
            # Traverse bottom row (right to left)
            if top <= bottom:
                for i in range(right, left - 1, -1):               
                    res.append(matrix[bottom][i])
                bottom -= 1
            
            # Traverse left column (bottom to top)
            if left <= right:
                for i in range(bottom, top - 1, -1):               
                    res.append(matrix[i][left])
                left += 1
            
        return res

---

Final Thoughts

This problem is a great way to practice boundary manipulation and layer-based traversal. By understanding how to manage the shrinking boundaries, it can help in a variety of other matrix traversal problems.

---

Feel free to modify or extend the file as you keep solving problems. Let me know if you need any further adjustments!
This template organizes your problem solution in a **clear, structured manner** with:
- **Problem description and link**  
- **Approach explanation**  
- **Code solution**  
- **Time and space complexity analysis**

You can now use it for every problem you solve in this way! Just replace the problem title and description as you go along.