## 1. leetcode 98  验证二叉搜索树 <br>
注意：不仅是判断左右子节点的值和根节点的关系，而是整棵左右子树都是有这个关系：[10,5,12,null,null,6,13] <br>
因此引入上下界
```
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:

        def helper(root,lower=float('-inf'),upper=float('inf')):
            
            if not root:
                return True
            if root.val<=lower or root.val>=upper:
                return False
            if not helper(root.left,lower,root.val):
                return False
            if not helper(root.right,root.val,upper):
                return False
            return True
        return helper(root)
```
