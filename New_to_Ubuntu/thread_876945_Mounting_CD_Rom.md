---
title: "Mounting CD Rom"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by SonOfOdin on 2008-08-01
Hey peeps

While mucking around with Virtualbox, I noticed that Windows XP Professional and Windows 2000 Professional CD's will not mount.  Windows 98 SE, Windows ME, and Windows 95A, B, C all mount automatically.

Is there any reason for this, is my PC playing funny buggers or what?

Cheers for the help,

---

### Post by Thelasko on 2008-08-01
That's weird, do you have the cd drive enabled in the virtual machine.  Did you check the "pass through" box?

If that's not the problem, try playing with the boot order in the VM's "BIOS" it should work the same as a normal BIOS.  I forget what key you have to press to bring it up, but it should be out on the web someplace.  You can also try pressing random function keys.

P.S. there is a virtual machines section of the forum for questions like this.  I suggest you post there next time as your post is a little beyond beginner stuff.

---

### Post by SonOfOdin on 2008-08-01
The problem isnt Virtualbox, the problem is something that I dont understand :)

I have 98SE running in VB, its just that the 2000/XP discs wont mount under linux.  At first I thought perhaps it was the discs, but I ran them over to a neighbours place and they are working fine over there...

Sorry about the long winded nature of my question, It wasnt meant to be a virtualbox question...  I get carried away when I start a thread.

Edit:  The discs will boot when the system is reset too. :headscratch:

---

### Post by Thelasko on 2008-08-01
The disk won't even mount on the host system?  Did you try
```
sudo mount /media/cdrom0/ -o unhide
```
You may need to change the name of your cdrom in that command.

---

