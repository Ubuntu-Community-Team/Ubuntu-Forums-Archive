---
title: "Resolution problems, Ubuntu, fx5200"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by FlashStock on 2008-08-09
Hi, I can't seem to get the resolution I want on ubuntu, I'm using an FX5200 and I installed the drivers Ubuntu recommended for me, now the thing is, the resolution won't go higher than 800x600, this is a pain in the *** since I use a 22'' widescreen monitor, I downloaded drivers from Nvidia, but they say I must run them in ''root'' what hell the that is, I'm very new to this.

Thanks for the help.
:(

---

### Post by nathaniel.porter45 on 2008-08-09
I´m fairly new to this also, but to use root, become root, whatever you use the command:

sudo -i  

Good luck on your conquest.

---

### Post by FlashStock on 2008-08-09
I am root now, but how do i run it? It's on the desktop.

---

### Post by pi.boy.travis on 2008-08-09
Is the file you downloaded source code, or is it a .deb packeage?

Is the extension .deb or .tar.gz?

---

### Post by FlashStock on 2008-08-09
.run

---

### Post by russ02j30 on 2008-08-09
I had the same problem and solved it with ENVY- Download all three files from the synaptic package manager when you reboot go to the apps- upper left menu and get ENVY open it and follow it. Good luck- keep it simple. russ:)

---

### Post by pi.boy.travis on 2008-08-09
> **FlashStock said:**
> .run

Hmmmm. . . not sure what to do with a .run, but you can run any app as root by opening a terminal (Applications-Accessories-Terminal) and typing:

sudo (app here)

BTW Root is like the administrator.  Root can do anything, and is the "owner" of the system.  That's right, in Linux, you don't own every file, root does, except for your home directory.  It's safer that way.

---

### Post by FlashStock on 2008-08-09
okey, I installed the drivers, BUT, nvidia panel says that my monitor is a crt and only supports 640x480, what the hell!? and i tried to detect monitor/display w/e but it still says the same thing. ''CRT bla bla bla''... DAMN!

---

### Post by pi.boy.travis on 2008-08-09
What does Applications-Other-Screens and Graphics have to say?

It may be hidden by default, in that case right click on the main menu, edit menus, and check the box next to Screens and Graphics.

---

### Post by FlashStock on 2008-08-09
> **pi.boy.travis said:**
> What does Applications-Other-Screens and Graphics have to say?

It may be hidden by default, in that case right click on the main menu, edit menus, and check the box next to Screens and Graphics.

Thanks! It works now!

---

### Post by pi.boy.travis on 2008-08-09
Second line of my sig.  Words to live by!

---

