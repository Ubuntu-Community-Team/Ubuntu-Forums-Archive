---
title: "difficulty booting and more..."
date: 2008-05-08
forum: New to Ubuntu
---

### Post by mustard greens on 2008-05-08
I have been running ubuntu for several days now and have been having several intermitent problems.

1st) when booting (from CD or install) it can take several trys before a succesfull boot.  when unsuccesful it takes me to a command line which says: instramfs.  I have tried to look up this instramfs on the web and have found nothing.  also I am uninitiated/intimidated by the command line and have no interest in studying it at this time.

2nd) I often have trouble downloading apps.  the problem seems to be connection speed, though I am able to surf the web at full speed durring these times.

3rd) today multiple different apps disapeared from control panels on two seperate user accounts though noone had been using the machine.

these problems seem far from the stability I was promised with linux, and I am hoping someone can tell me how these things are my fault.
thanks,
aaron

---

### Post by garyedwardjohnston on 2008-05-08
Firstly, using the command line is part of Linux.  You WILL mess up once in a while but once you learn, it will become a welcome change to GUI's.

If you refuse to learn it then Linux is probably not for you.  Ubuntu has done a good job at avoiding it most of the time, but it is still part of the Linux experience.

Next, just let the downloads happen.  Ubuntu is being overwhelmed with downloads of the 8.04.  Have patience, it's FREE!

Lastly, when you talk about the control panel, I assume you are talking about Menus...I'm not sure why this would happen, but try:

System > Preferences > Main Menu

and reselect the items.

---

### Post by lemming465 on 2008-05-08
The first thing to check if you are having intermittent problems is how your memory is doing.  Try using the memory test option from the install CD or boot menu for about half an hour and see if it uncovers any errors.

The initramfs thing is the INITial RAMdisk FileSystem used early in the boot process just after the kernel starts, but before the root filesystems is mounted.  If things are wedging there, you don't have much option except trying a reboot.  My Toshiba laptop occasionally does that; my older desktop system never does.

---

### Post by bumanie on 2008-05-08
You could look at using the alternate install cd. If often works without any problems if the live cd won't work. Get it from here[http://www.ubuntu.com/GetUbuntu/download]("http://www.ubuntu.com/GetUbuntu/download") Just check the box under the green download here text.

---

