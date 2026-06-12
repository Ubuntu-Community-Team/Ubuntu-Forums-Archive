---
title: "How to share folders when using Virtualbox"
date: 2011-11-23
forum: New to Ubuntu
---

### Post by gatgat23 on 2011-11-23
I don't know how to share folders when using Virtualbox. I want to know how to share folders in Virtualbox when Ubuntu as host and Windows XP as Guest OS. I have Ubuntu 11.10. Help me. Thanks!

---

### Post by wolfen69 on 2011-11-23
Just go into preferences in vbox for your xp install, and choose a folder on your ubuntu install that you want to share. Then start up xp and go to My Computer and at the top you will see Map Network Drive. Navigate to the shared folder. It will then show up in My Computer.

---

### Post by gatgat23 on 2011-11-23
Thanks. :)

BTW, I'll just post here so I will not make a new thread. Can a scanner work on XP when using XP as Virtualbox? If yes, how? My scanner is Canon CanoScan N640P ex. Thanks!

---

### Post by wolfen69 on 2011-11-23
> **gatgat23 said:**
> Can a scanner work on XP when using XP as Virtualbox? If yes, how?

Just go into the virtualbox settings when xp is loaded and then into USB settings and add the printer. Make sure printer is turned on first.

---

### Post by gatgat23 on 2011-11-23
Actually, it's not a USB printer. It's a scanner with a parallel port. I don't know how to setup the port. It's connected, but the application that handles the scanner doesn't detect the scanner. Help?

---

### Post by wolfen69 on 2011-11-23
> **gatgat23 said:**
> Actually, it's not a USB printer. It's a scanner with a parallel port. I don't know how to setup the port. It's connected, but the application that handles the scanner doesn't detect the scanner. Help?

In that case you will need a parallel to usb adapter.

---

### Post by gatgat23 on 2011-11-23
I can't seem to work with this scanner. I'll just then reinstall Windows for this ancient scanner work. But the main question is answered. Thanks for your help.

---

### Post by coldraven on 2011-11-23
> **wolfen69 said:**
> Just go into preferences in vbox for your xp install, and choose a folder on your ubuntu install that you want to share. Then start up xp and go to My Computer and at the top you will see Map Network Drive. Navigate to the shared folder. It will then show up in My Computer.


AFAIR XP has a bug, the network folders do not automatically expand, you have to keep double clicking to get where you need.
Once you have navigated to the folder in XP right click and make a desktop shortcut for it.

---

### Post by gatgat23 on 2011-11-23
That adds an information to me! Thanks. :)

---

### Post by gatgat23 on 2011-11-23
Wait a minute. Marking thread as unsolved...

I'm using only Ubuntu, because I can't dual-boot with Windows 7. When I try to boot up Windows, BSOD appears.

So, now, I installed Windows. (Leaving Ubuntu.) But thought of using Ubuntu with Virtualbox on Windows.

Now, how can I share folders with Windows as host and Ubuntu as Guest?

Thank you for your replies.

---

### Post by dhyan on 2011-11-23
Step by step tutorial is available in the following ink

[http://karmicdriver.blogspot.com/2011/11/how-to-use-shared-folders-in-virtual.html](http://karmicdriver.blogspot.com/2011/11/how-to-use-shared-folders-in-virtual.html)

[]("http://ubuntuforums.org/member.php?u=1498756")Thanks
~dhyan

---

