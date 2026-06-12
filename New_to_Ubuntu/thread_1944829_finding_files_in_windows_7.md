---
title: "finding files in windows 7"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by lenypl on 2012-03-22
i use both ubuntu11.10 and windows7 in my laptop.yesterday i download some photos from my googlemail account  and save on my main driveE in windows7. but  i cant find that photos on ubuntu. i can see other photos of the same drive in both os

---

### Post by 3rdalbum on 2012-03-22
If you installed Ubuntu through the Wubi program, your Windows drive is in /host. That is, in the file manager, go to Filesystem on the left side of the window and go to the "host" folder.

If you installed Ubuntu normally, your Windows drive will be listed on the left side of a file manager window.

Note that Windows 7 doesn't show you the actual exact layout of your hard disk, so it may look a little different on Ubuntu (as Ubuntu shows what is actually there) but your files will definitely be there and accessable.

---

### Post by Mark Phelps on 2012-03-22
When Vista came out, and continuing with Win7, MS stopped defaulting to the <user> directory inside [\Documents and Settings\] for storing things.  They kept the links there, but changed them to soft-links that now point elsewhere.

Now, when you download in Win7, the default is to store the files under C:\Users\<username>

Inside that, there is a Downloads folder (which may be where the files are).

Also, files get stored in either or both of the following:
C:\Users\<username>\AppData\Local or the same path, but ending in \Roaming.

AppData is now a hidden directory -- which should not prevent you from seeing it from inside Ubuntu.

---

### Post by lenypl on 2012-03-28
thank you for replay friends. i am new in ubuntu.so i dont understand your replay.can you pls tell me what exactly i have to do?i installed ubuntu normally

---

