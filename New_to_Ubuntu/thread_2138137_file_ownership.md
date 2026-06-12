---
title: "file ownership"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by Artanis.ro on 2013-04-23
Hi Guys,

I want to install on an pretty old pc (not very old, 2009) the latest version of ubuntu (12). I want to use 2 old HDD to backup some data I have.
I am worried that once I install ubuntu on that PC it will claim ownership of the files on the 2 HDDs and if something is to happen with the Ubuntu OS 
I will loose everything I have because my files will belong to the OS that could become dead or damaged. This scenario happens particularly when I add new files while using the Ubuntu OS.

Now, cam someone tell me please if Ubuntu has some kind of claim ownership so that those files will be used on a new OS or Windows?
This scenario happened to me once while using Ubuntu 11, lucky for me I had no critical files, so it was ok to loose them. 

Thank you

---

### Post by Lars Noodén on 2013-04-23
You shouldn't lose the files even if the ownership permissions are different from what you have on the new machine.  You can always use 'sudo chown' to change the owner to the right one so that you don't lose any.  Alternately, you can change the uid for your account on the new machine to match that of the old machine, but that is a little more complicated, but not much.

---

### Post by 3rdalbum on 2013-04-23
No operating system will "take ownership" of files on another disk. It doesn't work that way. The files on any other disks will stay on the other disks, untouched, until you modify them. When you modify files, they stay in the same format they were before and can still be used on any operating system.

If you put files onto the other two hard disks they will still be usable on other operating systems of course.

Can you describe the symptoms of this "claim ownership" thing that you said happened on Ubuntu 11.04/11.10?

---

### Post by Artanis.ro on 2013-04-23
The symptoms are:
I typed in console for the respective folder sudo chmod 777 "path to directory" and when I tried to copy those files to my external usb drive it triggered a ownership error message (I don't recall the exact message); My ubuntu installation was damaged and I booted from a ubuntu cd in order to transfer my files to my external HDD. 
The weird thing is that it was able to copy some files, but not all; it couldn't copy some executable files, some pictures (some pictures were copied though) and other files. I believe that the files written by the damaged Ubuntu installation were not copied, but I am not sure, because I don't know by hard when I created each file :).

---

