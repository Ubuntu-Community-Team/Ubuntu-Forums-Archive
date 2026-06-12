---
title: "How can I monitor the 'free store'?"
date: 2007-10-22
forum: Programming Talk
---

### Post by rgeddes on 2007-10-22
I'm using some trees dynamically, while monitoring memory usage using top.  I can see memory usage go up (in top) as I fill the tree with data, but when I delete the tree (using the delete operator) top doesn't report a reduction in memory usage for that particular process.  

I know that memory is going back to the free store because I fill the tree up with data (1.5GB), delete the allocated memory, fill it up again with the same data set, and the memory usage stays at 1.5 GB... doesn't go up to 3GB.

Is there a way of monitoring, through top or some other means, the memory that gets returned to the free store after it has been freed?

Thanks
Richard

---

### Post by duff on 2007-10-22
Massif --
[http://valgrind.org/docs/manual/ms-manual.html](http://valgrind.org/docs/manual/ms-manual.html)

---

### Post by ilautar on 2007-10-23
> **rgeddes said:**
> I'm using some trees dynamically, while monitoring memory usage using top.  I can see memory usage go up (in top) as I fill the tree with data, but when I delete the tree (using the delete operator) top doesn't report a reduction in memory usage for that particular process.  

I know that memory is going back to the free store because I fill the tree up with data (1.5GB), delete the allocated memory, fill it up again with the same data set, and the memory usage stays at 1.5 GB... doesn't go up to 3GB.

Is there a way of monitoring, through top or some other means, the memory that gets returned to the free store after it has been freed?

Thanks
Richard

There is no 'right' way to do this, as OS is caching data in RAM etc., so you will usually never get accurate reading. Its better to design your program so you do not have to read (for example, expect ram allocation failure) or use memory debugging tool as suggested to confirm you do not have memory problems.

Regards,

---

### Post by bigboy_pdb on 2007-10-23
It sounds as though you're keeping a total in the root node. When the delete method is called and a leaf is deleted successfully, return the amount of memory that the leaf consumed and then subtract that amount from the total memory in the root node.

**[EDIT]**I think I might have read your post incorrectly, but, yes you should be able to keep track of the memory in the root node or you could store the tree in a structure that keeps track of the memory that a structure or variable uses.**[/EDIT]**

---

### Post by rgeddes on 2007-10-23
> **bigboy_pdb said:**
> It sounds as though you're keeping a total in the root node. When the delete method is called and a leaf is deleted successfully, return the amount of memory that the leaf consumed and then subtract that amount from the total memory in the root node.

**[EDIT]**I think I might have read your post incorrectly, but, yes you should be able to keep track of the memory in the root node or you could store the tree in a structure that keeps track of the memory that a structure or variable uses.**[/EDIT]**

Yes, you are correct in the idea... the tree is a series of linked (with pointers) nodes.  To free the memory taken up by the tree, I run a tree traversal function, deleting every node that is 'traversed'... caution, however, the function has to be declared static, as it will eventually delete the object (the last node in this case) that contains the function deleting the object.

I was looking for more of a real time monitor that would take into account all memory...kind of like top.  

Thnx for the input though

---

