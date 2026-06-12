---
title: "Screen resolution in virtual box"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Jim_in_Germany on 2008-08-11
Hi,

I installed Ubuntu Hardy Heron as a guest OS in Virtualbox.
I have installed the guest additions.
When I attempt to change the screen resolution I however only have the choice between 800 x 600 and 640 x 480.
This means that the Ubuntu guest OS window is tiny on my 21 inch monitor.

Can anyone help me sort this out??
Thanks very much in advance

---

### Post by fahadsadah on 2008-08-11
What is the host OS, and it's screen res?

---

### Post by null byte on 2008-08-11
```
gksudo gedit /etc/X11/xorg.conf
``````

Subsection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480" <=====
ViewPort 0 0
EndSubsection
EndSection
```You should have something like that in your xorg.conf file.
---

Well, also notice that any virtual machine doesn't provide access to the host's graphic card.

---

### Post by Jim_in_Germany on 2008-08-11
Hi,

host is also Ubuntu Hardy 8.04
(I wanted a Hardy within a Hardy for experimentation purposes)
It's res is 1600 x 1200

Here is the /etc/X11/xorg.conf file from the guest Hardy:

Adding the following lines to the screen section of the file:

	DefaultDepth 24
	SubSection “Display”
	Modes “1280×800&#8243; “1024×768&#8243; “800×600&#8243;
	EndSubSection

makes ubuntu prompt me with a configuration dialogue on boot (Ubuntu is running in low graphics mode ....). In this dialogue I can choose my monitor (generic 1600 x 1200) but no matter what I choose in this configuration, once I logon to my desktop I only have the choices of the two resolutions.



Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
    Driver      "vboxmouse"
    Option      "CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by Novus on 2008-08-11
have you tried running
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Jim_in_Germany on 2008-08-11
Hi, 

yup, tried that.That revers my xorg.conf file to the state described above (where there are no options for screen resolution).

I have the feeling that the virtual box additions aren't installed properly as the mouse pointer gets trapped in the guest os window and I have to press right ctrl to free it.

Is there any way I can check this?

---

### Post by Sirron on 2008-08-11
Are you sure the guest additions work with hardy?

---

### Post by Jim_in_Germany on 2008-08-11
No, not at all.
How can one check this?

---

### Post by Jim_in_Germany on 2008-08-11
Problem solved.
I found the solution on a German page. 
Here's the summarized translation:

type: sudo /etc/X11/xorg.conf

Add the following line to the section "Device":
Driver "vboxvideo"

Add the following to the section "Screen":
SubSection "Display"
        Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

(obviously choosing the appropriate resolutions)

Restart the virtual OS and then you're done.

If on reeboot you don't have a mouse pointer any more (I didn't) make sure the section "Input Device" looks like this (and restart again).

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vboxmouse"
EndSection

---

### Post by Elfy on 2008-08-11
The guest addition do work with hardy, at least they do with the PUEL version I don't know about the OSE - but as you say the mouse is getting captured - so it's not at the moment :)

Go back into the vm hardy and reinstall the guest additions. Edit - ok don't then :D

---

