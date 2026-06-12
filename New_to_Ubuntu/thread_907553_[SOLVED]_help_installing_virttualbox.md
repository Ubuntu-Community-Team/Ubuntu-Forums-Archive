---
title: "[SOLVED] help installing virttualbox"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-09-01
It's always something when I try to install virtualbox on a computer.

This time it says "virtualbox-ose-modules-generic" depends on "virtualbox-ose-guest-modules-2.6.24-20-generic", when I try to install that package, it says "linux-image-2.6.24-20-generic  but it is not installable"

Off course it's not installable.

Why in hell does virtualbox-ose-modules-generic depends on a package for a kernel I don't have installed and can't be installed all together using the repos?

--

If a mod would be so kind to fix the spelling mistake in the title ...

---

### Post by Hazer on 2008-09-01
Hi, I had the same problem but I managed to work it out,
(for virtualbox-ose)

type in:
Code:

sudo apt-get install virtualbox-ose-modules-$(uname -r)

after that just go to system --> administration --> users and groups, click unlock and type in your password. Then press manage groups and find the group vboxusers, select it and click properties then just tick your username and root and click ok. now logout and log back in and virtualbox should work! :guitar:

---

### Post by eggdeng on 2008-09-01
Warning! The OSE is a limited version with no support for usb. You can download a .deb package of the PUEL version for Ubuntu from [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")
You will have to thrash around a bit for a good how-to but installation is simple and set-up is reasonably straightforward. And performnce is really impressive.

---

### Post by billgoldberg on 2008-09-01
> **Hazer said:**
> Hi, I had the same problem but I managed to work it out,
(for virtualbox-ose)

go to terminal and type in "uname -r" which will tell you your kernel version. so if my kernel was "2.6.24-19-generic" to get virtualbox working I would type:
Code:

sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic

after that just go to system --> administration --> users and groups, click unlock and type in your password. Then press manage groups and find the group vboxusers, select it and click properties then just tick your username and root and click ok. now logout and log back in and virtualbox should work! :guitar:

I figured that much.

I did it myself and it didn't worked.

After using apt-get do it, it did work. Strange.

I usually use the terminal to add new users, it's faster.

For virtualbox I used this:

```
sudo adduser username vboxusers
```

--

I know the difference between the open source version and the closed one. 

The open source on does all I need it to do.

---

