---
title: "Help installing wine"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by Hanketsu7787 on 2012-10-21
I'm brand new to the linux operating system and I need a bit of help. I'm running Ubuntu 12.10 on my laptop and I want to access the files from my Windows side. Whenever I try to install it I get this error.
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

Help please! Thanks in advance!

---

### Post by Mark Phelps on 2012-10-21
Not sure what you're asking ...

Wine will NOT let you access your Ubuntu files from the Windows side.  Windows can't read Linux filesystems; Wine has nothing whatsoever to do with that.

However, if you want to access the Windows files from Ubuntu, once again, Wine has nothing whatsoever to do with that.  Simply click on the Home icon, select the partition containing the Files, and open them with the Nautilus file manager.

---

### Post by micoli on 2012-10-22
Hi Hanketsu7787

I have exactly the same problem, also on a laptop. I can run wine on Ubuntu 12.04 on my desktop PC but I get the same message as you when I try to install Wine on my Laptop.

I've also been to Wine HQ and followed all their instructions without any luck. I get a similar message when I try to install through Terminal.

Can anyone help?

Thanks.

---

