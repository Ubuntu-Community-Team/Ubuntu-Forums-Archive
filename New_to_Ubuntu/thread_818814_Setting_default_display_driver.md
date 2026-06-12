---
title: "Setting default display driver"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by MrPickle on 2008-06-04
I need to set it to nvidia but I don't know how. The driver's installed, I had it earlyer today but the shutdown button wasn't showing so I went back to gdm. Now I don't know how to switch back.

---

### Post by iaculallad on 2008-06-04
Navigate to System->Administration->Login Window

In the "Local" tab of "Login Window Preferences", check if "Menu Bar"->
"Show Actions menu" is checked. (Put a check mark if not checked and close the form - Shutdown button should appear)

---

### Post by django0909 on 2008-06-04
If your shutdown button isn't there you can try re-adding it by right-clicking whichever panel you want it in, (top, bottom, or sides if thats where you have them), and clicking 'add to panel'. The 'quit' button is near the bottom and if you select that it will add it back in.

Edit: Ignore that, I misinterpreted what you were trying to do.

---

### Post by MrPickle on 2008-06-04
> **iaculallad said:**
> Navigate to System->Administration->Login Window

In the "Local" tab of "Login Window Preferences", check if "Menu Bar"->
"Show Actions menu" is checked. (Put a check mark if not checked and close the form - Shutdown button should appear)

I tried that whilst using nvidia but it told me to use GDM, now I need to switch back to nvidia.

---

### Post by JoshuaRL on 2008-06-04
Unless I'm misstaken, gdm isn't a driver.  It's the desktop manager that Xserver launches at X startup.  But if you need to adjust your drivers, you can use:
```

displayconfig-gtk

```
That is the GTK port of displayconfig from KDE.  You can use that to alter the video settings.

---

### Post by iaculallad on 2008-06-04
Or try to re-configure your xorg:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by MrPickle on 2008-06-05
I have got the resolution back to normal, but I don't have the special effects back. How do I make it use nvidia again?

---

### Post by MrPickle on 2008-06-05
I used the program on nvidia's site to set the x config file for nvidia but when it doesn't work, so I typed startx into the terminal and it says that it can't find the screen.

---

### Post by MrPickle on 2008-06-05
It also keeps starting up into the terminal.

Please help

---

### Post by Cap'n Redbeard on 2008-06-05
Hi MrPickle,

JoshuaRL is right.

Please have a go using displayconfig-gtk:

>  sudo displayconfig-gtk


This lets you select video cards, displays and drivers and remembers them next time you start up.

It worked on this machine.

:)

---

### Post by MrPickle on 2008-06-05
I've done that but it isn't remembering them.

---

### Post by MrPickle on 2008-06-05
I fixed the problem by deleting the nvidia packages and the nvidia kernel then re-installed my drivers.

Here's a guide for anyone else who is having this problem:
Open a terminal and type:
```
dpkg -l | grep nvidia
```
Now type
```
sudo apt-get remove **packages displayed in previous command**
```

Once they're removed go to etc/init.d and delete the nvidia-kernel, you might have other nvidia files, I'd delete them too, I only had the kernel though.
If you're having permission problems use:
```
sudo rm /etc/init.d/**name of file**
```
It'll delete the file, **BE CAREFUL WITH THIS COMMAND.**

One you've done that go System > Administration > Services.
Unlock it and disable "Graphical Login Manager"
This'll drop you into the terminal. Go to whatever directory you have the driver install in and type:
```
sudo sh **name of your driver install**
```
Let it do whatever it wants.

Type "startx" and be happy :P

You'll know it's worked because a nvidia logo will come up, well it did for me :P

---

### Post by MrPickle on 2008-06-05
:( I  switched off, then back on and the driver's disabled again. I don't really want to re-install the driver everytime.

---

### Post by MrPickle on 2008-06-05
Ok, I've worked out how to get it running again, but then all my effect settings go.

I need to do this:
```
sudo nvidia-xconfig
sudo /etc/init.d/gdm stop
startx
```

How can I make it do this automatically?

---

