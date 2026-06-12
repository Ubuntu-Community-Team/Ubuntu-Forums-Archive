---
title: "two hardrives"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Caldronis on 2012-03-05
I fear that installing windows on the primary drive and ubuntu on the secondary drive may be making the responces to my keyboard and mouse so slow that it seems to be doing nothing.  Could it be this arrangement, grub2 is on the primary drive.  Ubuntu has some really serious slow down problems and one task I am doing is ordering more ram for my intel motherboard.  But more than likely I don't under stand how the terminal looks these upgrades, is it from a server.  I tried installing nautilus earlier today and it basically told me that I needed permission from my administrator.  Thank you for your time!

---

### Post by Daveth on 2012-03-05
Hallo. Welcome to the ubuntu Forums. Can you tell us what version of ubuntu you are running, and what sort of slow downs you are experiencing? Does it boot up OK, then run slowly afterwards? Is it sharing common data with Windows? A bit more info will help folk work through it better.

---

### Post by JayKay3OOO on 2012-03-05
You don't make much sense, but here is what I gleamed.

Installing RAM won't require any user changes. The operating system (linux) will just 'see' the extra RAM. Remember that 32 bit Linux can see up to 3GB and to see more than 3GB you either need to switch to 64bit or install PAE in the 32 bit version. Simples.

If you install nautilus you need to input your user password that you entered when you installed the Linux otherwise if you use terminal you need to use *sudo apt-get install nautilus* it will then prompt for password. You only need to install nautilus if working from Ubuntu version *Server*.

Not sure why it's so slow because you did not post computer specifications.

You can install Ubuntu inside Windows using Wubi that is supplied within the disk image (.iso) so you can uninstall it like any other app from windows.

---

### Post by QIII on 2012-03-05
Can you tell us exactly how you installed Ubuntu?

---

