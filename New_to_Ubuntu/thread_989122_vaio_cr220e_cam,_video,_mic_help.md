---
title: "vaio cr220e cam, video, mic help"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by campbuds on 2008-11-21
:

He is what I need help with. I have a vaio vgn-cr220e...

1. I cannot get my screen to display in 1280x800. a 1/4 of
it goes fuzzy when I do. My current resolution is blurry though because it is not a wide screen resolution.

2. I cannot get my webcam to come on. I am using skype and have no video

output of my xorg.conf and lsusb are below

I am pretty much a newb and would really appreciate your help.

---

### Post by stoogiebuncho on 2008-11-21
I'm probably not knowledgeable enough to help you out, but I can suggest some additional things you can post to give the experts better information once they get here.

1) Display.  You might be able to find a fix for this yourself with a little help from Google.  Screen resolution is a pretty common problem and there are a lot of posts devoted to it already.

Most fixes seem to involve editing the /etc/X11/xorg.conf file.  If you want to play around with this yourself and see if you can figure something out, you should make a backup first:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

(that copies the xorg.conf file to a new xorg.conf.backup file)

Then open the xorg.conf file with a text editor:

```
sudo gedit /etc/X11/xorg.conf
```

I'm sure someone else would have better advice for you than I do on this matter.

2)  Webcam.  I'm assuming this is a USB webcam, right?  What's the make and model?  Open up a terminal, and enter
```
lsusb
```
Paste the output back here.

3)  Mic.  Again, what's the make and model?  Does it plug into the microphone jack on your computer, or is it a USB mic?  Have you tried it in more than one program?

---

### Post by campbuds on 2008-11-22
Here is the output from the "lsusb"

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by campbuds on 2008-11-22
Also is the output for my xorg.conf file

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 1552
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

