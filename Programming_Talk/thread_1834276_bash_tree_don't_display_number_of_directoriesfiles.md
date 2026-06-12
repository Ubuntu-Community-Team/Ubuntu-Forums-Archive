---
title: "bash: tree: don't display number of directories/files"
date: 2011-08-27
forum: Programming Talk
---

### Post by CryptKeeper777 on 2011-08-27
The command tree shows the folder/file structer of a folder. Beneath the tree structure, it displays the number of directories and files (e.g. "3 directories, 7 files"). Is there any way to suppress this last output?

I looked over the man page but didn't find anything, there doesn't seem to be a direct way. Any idea how to solve this problem indirectly?

PS: Short explanation of what I want to do: I loop through some folders and display the tree structure of each folder. IMO the output looks better this way than just displaying the tree structure of the parent folder, because there's some space between the individual trees, but the number of directories beneath each tree sucks.

---

### Post by ofnuts on 2011-08-27
Did you try 
```
tree | grep -v "directories,"
```

---

### Post by CryptKeeper777 on 2011-08-27
> **ofnuts said:**
> Did you try 
```
tree | grep -v "directories,"
```
No, I'm not really beyond the bash basics... But it works perfectly, thanks!

Edit has to add: I had to change it to ```
tree | grep -v "**director**"
``` to cover both the bases with only one ("directory") or with more ("directories") directories. Now it really works perfectly.

---

### Post by gmargo on 2011-08-27
Reading the fine man page for **tree(1)** ...
> 
--noreport
              Omits printing of the file and directory report at the end of the tree listing.
And don't forget that **tree(1)** omits "hidden" dot-files, so use "tree -a" to see everything.

---

### Post by ofnuts on 2011-08-27
> **gmargo said:**
> Reading the fine man page for **tree(1)** ...

Yep, better

---

