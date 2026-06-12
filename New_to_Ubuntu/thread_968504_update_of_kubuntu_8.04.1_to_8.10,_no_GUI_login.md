---
title: "update of kubuntu 8.04.1 to 8.10, no GUI login"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by gregphil on 2008-11-02
After the kubuntu 8.10 update I can not do a normal GUI login.  The graphical kdm login screen accepts the password and seems to be starting (clears the screen and starts to paint a box in the upper left, but then repaints the login screen with the "login failed" message.  It never starts the fancy fading in driver loading box centered on the screen like a normal KDE 4.1 GUI login.

I can logon both as a normal user or as root from a console screen (CTRL-ALT-F2)

Any idea how to fix the graphical screens (which were working right up to the 8.10 "upgrade")?  Issuing "startX" from a console seems to start-X briefly, the screen clears and the X cursor is painted, but then it returns to the console prompt with an error message (something about no NI).  I am booted into another distribution to send this, so I can't look at the message right now.

Before the "upgrade" I did have the real 3rd party Nvidia drivers loaded, but I disabled them and rebooted before starting the kubuntu 8.10 "upgrade"

It looks to me like this "upgrade" just gave me a real good reason to give up on Linux for another year or two and boot back into trusty old WinXp.  At least it never fails to support normal hardware, and has always been able to drive my video screens (for the last 20 years or so)

---

### Post by brandoncolorado on 2008-11-02
Possibly:

After pressing ALT-F2 which gets you to the command line type in the
following commands.
sudo /etc/init.d/gdm restart
See if that gets you in, otherwise type in this command
sudo /etc/init.d/gdm stop
then type in startx
Hope this helps

[https://answers.launchpad.net/ubuntu/+question/6130](https://answers.launchpad.net/ubuntu/+question/6130)

---

### Post by gregphil on 2008-11-02
I like the picture of your cat.

I will give your advice a try once I reboot, but I don't think it stands much of a chance of working.

This is kubuntu, not ubuntu and as such it defaults to using kdm instead of gdm.  I suspect gdm is not even installed (for kubuntu)

Thanks for the post.

---

### Post by brandoncolorado on 2008-11-02
> **gregphil said:**
> I like the picture of your cat.

I will give your advice a try once I reboot, but I don't think it stands much of a chance of working.

This is kubuntu, not ubuntu and as such it defaults to using kdm instead of gdm.  I suspect gdm is not even installed (for kubuntu)

Thanks for the post.

Whoops!  Sorry.  Try this one.

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

---

