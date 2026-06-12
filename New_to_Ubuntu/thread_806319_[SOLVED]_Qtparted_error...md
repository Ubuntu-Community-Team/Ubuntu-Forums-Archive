---
title: "[SOLVED] Qtparted error.."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-24
I've just installeed Qtparted on my ubuntu 8.4 machine and tried to start it but i get the error

```
Could not launch menu item

Failed to execute child process "qtparted-root" (No such file or directory)
```

But if i run in from terminal with

```
Sudo qtparted
```

it appears to run fine:confused:

---

### Post by kamitsukai on 2008-05-24
Also do i need to be using the live cd to resize my windows partition?

---

### Post by Shazaam on 2008-05-24
1. Just like gparted it needs to be run as root. Check the launcher to see if   it has the correct code. gparted is "gksu gparted" according to the launcher.
2. Not Vista= Boot to Windows. Defrag a couple of times. Reboot to either the Ubuntu livecd or the gparted livecd to resize Windows. When you are done and you boot Windows it will say it needs to do a disk check. Let it run.

If you have Vista AFAIK you can use it to do the resizing. Search the forums on how to do it.

---

