---
title: "gtk warning cannot open display"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by hutch23 on 2008-11-27
I just installed recommended driver for nvidia graphics card.  On  restart, after login, screen goes blank and monitor gives message "frequency out of range".  I understand I need to change ther horizsync and vertrefresh but on entering command "gksudo gedit /etc/X11/xorg.conf"  Iget the response gtk warning cannot open display.  THis is my first day with Linux.  It took me all night to find a way around hanging on "starting bluetooth" (noapic) and now I am stuck.  Thanks for your help.

---

### Post by Peter09 on 2008-11-27
You have no GUI, so apts with a gui don't work. Use the editor nano instead.

```
nano <filename>
```

---

### Post by hutch23 on 2008-11-27
I'm sorry but I am an "absolute beginner" and while I appreciate the response and understand what you are saying, I don't know how to proceed.  thank you.

---

### Post by Peter09 on 2008-11-27
To boot into recovery mode:
Hit the ESC key as soon as you see the grub prompt. This will stop the boot sequence. You can select recovery mode using the down arrows. Recovery mode is normally the second option of the list. Once selected hit the ENTER key and it should start to boot.

Boot into recovery mode and select 'xfix' from the menu, this may resolve it.

Otherwise select the 'drop to command shell' option and try the command I suggested.

---

### Post by hutch23 on 2008-11-27
Yes the "xfix" allowed solved the "frequncy out of range" but once again my only resolution choices are 800x600 and 640x480 while my monitor is 1440x900.

---

### Post by Peter09 on 2008-11-27
Can you post the output of the terminal command to confirm the driver that you are using.
```
lshw -C display
```

---

### Post by Peter09 on 2008-11-27
Also
Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers

---

### Post by philinux on 2008-11-27
gksudo gedit /etc/X11/xorg.conf

Using the above is 100% correct. Gedit is a graphical application. What exactly is the error message.
Unless gui is indeed borked.

However xorg tinkering is probably a last resort.

---

### Post by hutch23 on 2008-11-27
configuration: driver=nvidia latency=0 module=nvidia

when I enable nvidia accelerated graphics driver (version 177) [recommended] and restart i get the blank screen and "frequency out of range"

---

### Post by Peter09 on 2008-11-27
There are sections in the page below which may help you sort this out.

Basically you will need to edit your xorg file.

[http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)

---

### Post by philinux on 2008-11-27
> **hutch23 said:**
> configuration: driver=nvidia latency=0 module=nvidia

when I enable nvidia accelerated graphics driver (version 177) [recommended] and restart i get the blank screen and "frequency out of range"

Whats are your pc specs/graphics card.

---

### Post by hutch23 on 2008-11-27
Thanks for all the help.

It's an out of the box gateway dx 4720-03.  I'm dual booting vista and ubuntu 8.10.  nvidia geoforce 7100 graphics card, 19" widescreen gateway monitor.

Problem is when i attempt to edit xorg.conf i get "gtk warning cannot open display" message

---

### Post by philinux on 2008-11-27
Whats happens if you type

gedit

Does it open the text editor

---

### Post by hutch23 on 2008-11-27
no same response-gtk warning cannot open dsiplay

---

### Post by philinux on 2008-11-27
Try

metacity --replace

then try gedit again.

---

### Post by hutch23 on 2008-11-27
same result

---

### Post by hutch23 on 2008-11-27
on metacity --replace i get "unable to open x display"

---

### Post by philinux on 2008-11-27
Log out and login again.

you do have a desktop I take it with panels etc and menus.

---

### Post by hutch23 on 2008-11-27
ok. gedit still gets same response

---

### Post by philinux on 2008-11-27
Logout.

Click options
Select Session.
Then tick X client session

Proceed to login

Then try gedit.

---

### Post by hutch23 on 2008-11-27
same result.  i appreciate your persistence though

---

### Post by hutch23 on 2008-11-28
i still cannot access my xorg.conf to change my screen resolution.  This is more than frustrating.  I'm about to give up.

---

