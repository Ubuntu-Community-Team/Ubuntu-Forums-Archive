---
title: "Finding my files"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by wadie on 2012-03-17
Hi,

I'm trying to access the files I have on Windows 7,but I can't find them!

I tried to go to root,but don't have permission to access it even though I'm using the admin user now. also tried to go through the hard disk but didn't find anything related to my users and files in Windows 7.

Where do I find them ?

---

### Post by Gone fishing on 2012-03-17
Firstly is your Windows partition mounted? if it is then you should see it mouted in Nautilus (The file manager) and your windows documents will be some where like:

/media/Win7/Documents and Settings/windowsusername.

If the Windows partition is not mounted post back but there is a GUI tool called Mount manager which can help

---

### Post by NikTh on 2012-03-17
Hi , 
Try to create a mountpoint for windows partition and mount it from terminal . 
Example. 
```
 sudo mkdir /media/windowsdata 
```now that you have create windowsdata inside media run in terminal 
```
 sudo fdisk -l 
``` and you will see what partition corresponding to windows. Suppose that windows its dev/sda2 then you will do 
```
sudo mount /dev/sda2 /media/windowsdata 
```you can access now your windows files from nautilus file manager or if you are familiar continue with terminal.
:)

---

### Post by Paqman on 2012-03-17
How did you install?

If you used Wubi then your Windows partition will be available at /host within the file manager. If you installed to a separate partition then you might need to mount it as suggested above.

---

### Post by wadie on 2012-03-17
I installed using Wubi.

Found the files at /host.

Thank you all! and sorry for my stupid question,still a newbie.. :)

---

### Post by Paqman on 2012-03-18
> **wadie said:**
> sorry for my stupid question,still a newbie.. :)

The only stupid questions are the ones you're too shy to ask! We were all newbies once, asking questions is how you learn.

Welcome to the forum, btw.

---

### Post by NikTh on 2012-03-18
> **wadie said:**
> I installed using Wubi.

Found the files at /host.


Glad you solved your problem. Allow me a suggestion that always giving when i see this word (Wubi). 
Install Ubuntu normally - regular. Without wubi. Dual boot if you want. 
Wubi is just a virtual install. To try ubuntu 1-2-3 weeks. And not reveals the potentials of ubuntu. :)

---

