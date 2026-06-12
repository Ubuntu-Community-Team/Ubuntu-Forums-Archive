---
title: "Is it Normal to have a Folder Documents in the File System?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Papenco on 2008-06-22
Ok, I went into the File System, System Files or however it's called; the equivalent to c:/ in Windows and realized there was a folder named documents. Is it normal to have it there?
If it's not, how do I remove it?

---

### Post by erfahren on 2008-06-22
you're talking about the root file system (simply written with a slash "/")

no, it wouldn't be normal to have a "documents" directory in there (like "/documents") - is there anything in it?

there is, however, a /usr/share/docs --- it contains documentation (manuals and the like) for installed programs.

If that "documents" directory you're talking about is empty you can remove it but you might want to first just rename it for awhile

easiest way is to just press Alt+F2 and type in "gksu nautilus" (if you're using Ubuntu) and you'll be promted for your password -- Nautilus is the name of the file browser so you'd be opening it with root (or "admin") permissions - so BE CAREFUL!

browse to that directory and just rename it "documents_bak" (or whatever) for awhile. If you don't have any problems you can go back in and delete it the same way.

---

### Post by jpkotta on 2008-06-22
If there is a Documents directory in /, then no, it is not normal to have that.  I can't imagine any program creating such a directory, and whatever did create it would have had to be root.  That said, I bet it's actually somewhere else, like your home directory, and the menu you're using is hiding that fact.

Assuming you want it gone and it is in /, you can remove it with 
```
sudo rm -rf /Documents
```
BIG FAT WARNING: be extremely careful with the above command.  In particular, if there is a space between "/" and "Documents", it will nuke the whole system.

---

### Post by Papenco on 2008-06-22
Thanks and thanks for the warning.

---

### Post by vonroeder on 2008-06-22
Hi,

Ubuntu puts a few directories in your home directory, like music, videos and documents. They are there for your convenience, but tey are not essential. I guess it was done to make it more like windows. I have immediately removed them, since I like to control what goes in my filesystem.

---

### Post by cariboo on 2008-06-22
Gee I always thought a folder called documents was a good place to hold documents:). Mind you there are six sub folders in there to further making things easier to find.

Jim

---

### Post by Papenco on 2008-06-22
But the folder isn't with Videos or Music, it's with bin, boot and that folders. It's not in my home directory, it's in the System Files.

---

### Post by philinux on 2008-06-22
There are no folders in bin and only one in boot and thats the grub folder, in a standard install.

How did this folder get created? Have you installed anything lately using sudo?

---

