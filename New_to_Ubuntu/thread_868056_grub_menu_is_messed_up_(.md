---
title: "grub menu is messed up :("
date: 2008-07-23
forum: New to Ubuntu
---

### Post by fwaokda on 2008-07-23
I tried editing my grub menu and screwed it up :( can someone correct it for me?  I'm trying to get the windows installation under "other os" and the ubuntu above that. I thought all I had to do was change the default number but that also gave me an error 11 when booting up. -- [http://pastebin.com/m2fc6db6a](http://pastebin.com/m2fc6db6a)

---

### Post by drs305 on 2008-07-23
If you didn't change anything else, I see you changed the default number to 1. Menu.lst starts with 0 being the first 'title' entry. So the second 'title' would be 1. In your menu.lst, the second instance of 'title' is 'other operating system', which really isn't an option. Change the default number to 0 for windows or 2 for ubuntu.

I highly recommend changing menu.lst with StartUp-Manager rather than manually editing it, which can cause problems as you have discovered. You can use it to set the default OS or kernel, menu display time, number of kernels to view, and much more.

Here is a tutorial on Startup-Manager:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by sonicskywalker on 2008-07-23
If your grub seems irreparable, try out the Super Grub Disk:
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")
It helped me out with dual-booting. :)

---

### Post by weaver4 on 2008-07-23
You have default pointing to to "1" which is this one:

[I]#
# This is a divider, added to separate the menu items below from the Debian
#
# ones.
#
title           Other operating systems:
#
root[/I]

Select default = 0 for Windows:

[I]title		Windows Vista/Longhorn (loader)
root		(hd0,0)[/I]

or set Default = 2 for Ubuntu.

[I]title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)[/I]

---

