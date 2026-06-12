---
title: "How can I edit xorg.conf as supervisor without using command prompt"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by newby9119 on 2008-08-27
I am running xubuntu in virutual box on a xp host.  The xubuntu screen inside the vbox window does not resize to the full screen when I select full screen from the vbox window.  I think it is a problem with xubuntu not reading my video card/ native screen resolution, which is 1024 x 768.  The relevant part of my xorg.conf file is:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

I need to edit this to use the virtual box driver.  My problem is that it will not let me save changes when to the xorg.conf file.  I have read posts that explain how to do this with the command prompt.  I CANNOT USE THE COMMAND PROMPT.  If this is the only way I will abandon my attempt to run linux.  Is there any other way to this?

---

### Post by shane19174 on 2008-08-27
If you install UbuntuTweak, there's an option to add "edit as root" to the right-click options. (Though I'm sure not everyone supports UbuntuTweak, it's certainly made a few things easier for me.)

---

### Post by Elfy on 2008-08-27
You can open the file as root with this command, do Alt+F2 first - you will get a run dialogue

```
gksudo mousepad /etc/X11/xorg.conf
```

that should allow you to edit the file as root.

Why can you not use the command line.

---

### Post by quinnten83 on 2008-08-27
did you install the virtualbox guest additions?
If that is not installed you can't change the resolution.
try installing that and see if it works.

---

### Post by kellemes on 2008-08-27
> **newby9119 said:**
> I am running xubuntu in virutual box on a xp host.  The xubuntu screen inside the vbox window does not resize to the full screen when I select full screen from the vbox window.  I think it is a problem with xubuntu not reading my video card/ native screen resolution, which is 1024 x 768.

Like previous poster said, install the VirtualBox guest-additions.
You need to understand it's a **virtual** box, it will never use your videocard since it using it's own **virtual** videocard.

> If this is the only way I will abandon my attempt to run linux.
If you think anyone cares, you're wrong. You want to run Linux, you need to work for it, otherwise stay with Pokemon XP.

---

### Post by cardinals_fan on 2008-08-28
> **newby9119 said:**
> I CANNOT USE THE COMMAND PROMPT.
Why not?  Do you not have a keyboard?

---

