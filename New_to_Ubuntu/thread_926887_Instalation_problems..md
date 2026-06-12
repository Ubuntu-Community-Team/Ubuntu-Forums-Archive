---
title: "Instalation problems."
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Noxn on 2008-09-22
I wanted to install Ubuntu on a friends laptop, sound easy, doesn't it?

Well, the cd-drive is broken, it just doesn't work!

Any ideas how to install Ubuntu a different way? :confused:

---

### Post by superprash2003 on 2008-09-22
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by northern lights on 2008-09-22
Is there another OS installed on the laptop already?

If so, it's probably easiest to invoke a net install with [unetbootin]("http://lubi.sourceforge.net/unetbootin.html")

---

### Post by jrothwell97 on 2008-09-22
Hmm... obvious things first: is the machine set to boot from the CD first? If it's a disk burned from the Internet, did you burn it as a disk image instead of simply dragging it to the CD Burn queue and press Burn?

As for alternative solutions, you can try Wubi if the machine is running Windows, or you can use unetbootin to write the image to a removable disk.

---

### Post by Noxn on 2008-09-22
> **jrothwell97 said:**
> Hmm... obvious things first: is the machine set to boot from the CD first?



Yeah...

It already has windows, but it is laggy as hell, even opening a folder takes 1 hour (his windows is pretty ****** up).


So UNetbootin makes the thing instalable from the Usb?
Good, gonna try that.

---

### Post by northern lights on 2008-09-22
> **Noxn said:**
> So UNetbootin makes the thing instalable from the Usb?
It may, nut it can do more. From within Windows, download the Windows installer executable and run it. For the distro select Ubuntu, for the version "8.04 NetInstall" select the laptops primary hdd. Press "OK" and exit. Reboot. The a new bootmenu will appear. Select the unetbootin entry, let it work its magic.

> **Noxn said:**
> It already has windows, but it is laggy as hell, even opening a folder takes 1 hour (his windows is pretty ****** up).
For this purpose it should still suffice.

---

### Post by Noxn on 2008-09-22
I don't know...

Can wubi overwrite windows?
If not im going to try the this with UNetbootin...

---

### Post by dodle on 2008-09-22
My laptop's cd drive is broken as well.  I had to use an external cd drive to install.  I never could figure out how to install from a usb stick.

Wubi won't overwrite Windows, unless I'm wrong, Wubi is dependant on Windows.

---

### Post by northern lights on 2008-09-22
> **Noxn said:**
> Can wubi overwrite windows?
If not im going to try the this with UNetbootin...
Wubi can't overwrite Windows.

> **dodle said:**
> My laptop's cd drive is broken as well.  I had to use an external cd drive to install.  I never could figure out how to install from a usb stick.
NExt time you've gotta reinstall, check out unetbootin. No USB required, really powerful.

---

### Post by Noxn on 2008-09-22
Hmm, This laptop isnt new, btw...
[EDIT: yeah, its more old then new]
I just noticed it only has 250 (or something) mb of ram.
And looks like the cd drive itself works, but cant read the cd (Error while reading boot disk, or something like that, on other the computers the cd works).


And the windows is really LAGGY AS HELL.



I dont think this will work...


Thanks anyway :D :popcorn:

---

### Post by northern lights on 2008-09-22
Choose Xubuntu instead, same procedure.

---

### Post by dodle on 2008-09-22
If you want a fresh install of Windows, get nLite and make yourself an installation cd from the i386 folder in your C:\Windows directory.

---

### Post by Noxn on 2008-09-22
Guys, thanks but stop, i dont think it will work, this thing is really laggy and i dont think it will even START the damn UNetbootin.



/thread

---

