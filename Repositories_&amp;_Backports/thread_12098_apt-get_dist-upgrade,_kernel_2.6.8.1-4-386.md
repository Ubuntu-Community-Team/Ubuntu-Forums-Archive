---
title: "apt-get dist-upgrade, kernel 2.6.8.1-4-386"
date: 2005-01-21
forum: Repositories &amp; Backports
---

### Post by bstil on 2005-01-21
Hello, please explain the difference between kernel 2.6.8.1-3-386 and kernel 2.6.8.1-4-386.  Is -4 hoary instead of -3 warty?

I ran apt-get update and then apt-get upgrade from the root console.  The results said two packages were kept back.  I believe most of the installed packages were security.  Then I ran apt-get dist-upgrade and those two were installed.

The process altered my /boot/grub/menu.lst for dual boot.  I had to edit it to get WinXP back on the menu.  But now I also have two Ubuntu choices (plus two recovery mode choices):

Ubuntu, kernel 2.6.8.1-4-386
Ubuntu, kernel 2.6.8.1-3-386

Does this mean that I upgraded to hoary from warty?  What exactly are the differences between the two kernels.  Should I boot to the original Ubuntu, kernel 2.6.8.1-3-386 instead?  Please advise.

---

### Post by mendicant on 2005-01-21
I imagine it's related to the security issue over here:
[http://www.ubuntulinux.org/support/documentation/usn/usn-60-0](http://www.ubuntulinux.org/support/documentation/usn/usn-60-0)

Boot into the new one, and if it works okay for you, you can delete the old one (which has the security issue).

---

### Post by mendicant on 2005-01-21
If you are concerned about this kind of thing, you should subscribe to ubuntu-security.  In general, though, if your apt sources.list only contains warty, and only contains main, restricted and universe entries, the only possible updates you can have are security ones.  If you have any non-Ubuntu official repositories, then you may get non-security updates.

---

