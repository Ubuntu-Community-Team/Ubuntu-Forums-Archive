---
title: "Inorder successor or predecessor? deletion in AVL tree"
date: 2013-01-07
forum: Programming Talk
---

### Post by hatsoff on 2013-01-07
Ive to delete a root node,and inorder to do this ive to find inorder  successor or predecessor(red from wikipedia),now i dnt know how to,i  found inorder successor is leftmost of right tree but in my tree there  is no leftmost only has rightmost leaf node,now how to figure out  inorder successor if its not there(complete understanding of concept  require),and if we cant find inorder successor in sucha tree then is it  the second option to find inorder predecessor?then how to find inorder  precedessors.
Thanks for reading!!

---

### Post by ofnuts on 2013-01-07
> **hatsoff said:**
> Ive to delete a root node,and inorder to do this ive to find inorder  successor or predecessor(red from wikipedia),now i dnt know how to,i  found inorder successor is leftmost of right tree but in my tree there  is no leftmost only has rightmost leaf node,now how to figure out  inorder successor if its not there(complete understanding of concept  require),and if we cant find inorder successor in sucha tree then is it  the second option to find inorder predecessor?then how to find inorder  precedessors.
Thanks for reading!!
if it's an AVL tree, if you have nothing on the left you have at most one element on the right (and vice-versa), so you tree had at most two nodes and after deletion of its current root it is either empty or only contains the previously non-root element.

---

### Post by hatsoff on 2013-01-07
i didn't understand at all

---

### Post by hatsoff on 2013-01-07
its a 3rd level tree and root to be deleted is uppermost root.

---

### Post by lisati on 2013-01-07
> **hatsoff said:**
> its a 3rd level tree and root to be deleted is uppermost root.

You might find this article helpful: [http://en.wikipedia.org/wiki/AVL_tree](http://en.wikipedia.org/wiki/AVL_tree)

---

### Post by hatsoff on 2013-01-07
Thank you very much quite helpful :)
this is for you and others who replied=D>

---

### Post by hatsoff on 2013-01-07
so it means first i'll find inorder successor (smallest in the right subtree) and replace root value with, it delete inorder successor and after it if unbalance, rebalnce and call it a day! m i right?thats the algorithm?

---

