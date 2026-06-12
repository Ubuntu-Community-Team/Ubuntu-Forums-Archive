---
title: "boot up without screen switched on?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by blesbok on 2008-10-30
yes, in ubuntu 7.10 it's doable but i get the wrong resolution, i.e. 1024x800 (approx.) instead of 1280x1024(?).  Running a script to change the default depth doesn't work since the value seems to be read on start-up.  It might help to restart the x-server (gdm) but how do i do that (without a crash)? Please, while your help is appreciated, i'm using kde so gnomish options won't cut the mustard.  The real question seems to be, where is that lower resolution value read from and how do i edit it?

---

### Post by The Cog on 2008-10-30
You can do this by nailing down the monitor refresh rates in the file /etc/X11/xorg.conf, rather than letting them be autodiscovered (which is unlikely to work right if the monitor is switched off at the time). 
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by blesbok on 2008-10-30
thanks, i'll try that when back at my computer

---

### Post by blesbok on 2008-10-31
had a look at that .conf file. not sure how to go about 'nailing down' the resolution.  it's not clear where the instruction to  autodiscover the resolution is.  should i perhaps delete all the resolutions there except that of this screen?   :confused:

---

### Post by The Cog on 2008-11-02
As the link I gave says (in the first post), find the Monitor section in the file and enter the frequencies there. So it looks a bit like this:
```
Section "Monitor"
    Identifier    "CM752ET"
    HorizSync     31-101
    VertRefresh    60-160
EndSection
```
but put your own values in of course. They always say that you must read the monitor manual to get the values. I know there is a way to probe the monitor when it's plugged in - X uses it of course, but I haven't been able to find out what the command is with google.

---

### Post by blesbok on 2008-11-03
thanks, i hadn't followed your advice very closely; i now understand i have to enter the sync and refresh values in that file. don't know if i got a manual with my monitor (lg flatron 17119s) but found that data here

[http://whatsup.co.il/index.php?name=PNphpBB2&file=viewtopic&p=263256]("http://whatsup.co.il/index.php?name=PNphpBB2&file=viewtopic&p=263256")

i.e. HorizSync 30-83
     VertRefresh 56-75

with googling 17119s vertrefresh

also had interesting results with Identifier "None"  lol

i'll give it a try and let you know 

PS here:

[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7174/README.txt]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7174/README.txt")

i find something that could be relevant

Option "UseEdidFreqs" "boolean"
++                This option causes the X server to use the HorizSync
++                and VertRefresh ranges given in a display device's EDID,
++                if any.  EDID provided range information will override
++                the HorizSync and VertRefresh ranges specified in the
++                Monitor section.  If a display device does not provide an
++                EDID, or the EDID does not specify an hsync or vrefresh
++                range, then the X server will default to the HorizSync
++                and VertRefresh ranges specified in the Monitor section.

---

### Post by blesbok on 2008-11-04
my box doesn't seem to accept the .conf file.  perhaps if i hadn't been in a hurry and started with my backed up .conf file making just one change at a time it would have gone better.

the (now familiar) message appears that the machine's operating in low res mode.  when trying to edit .conf, the shell says it was externally modified.

Here's some of it:

```
Section "Device"
	Identifier	"Failsafe Device"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth	16
		Modes   "800x600"
	EndSubSection
EndSection

```

the settings i gave are of course gone.  just one question:
what should replace **"Default Screen"** as identifier?

thank you so far

bill blesbok

---

### Post by blesbok on 2008-11-05
well, i tried doing one change at a time after restoring the .conf file from its backup.  the moment i added the horizsynch and vertrefresh, i got the low res mode message on booting.  couldn't successfully configure the display there either.

tried a lot of things.  perhaps you're asking why do i want to do this?  well window$ can, so surely it's possible!  if anyone for whom this works  (boot with screen off) could post his /etc/X11/xorg.conf content, it would be much appreciated.

---

