---
title: "resolution problem after upgrade to 10.04"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by agramahisi on 2011-09-15
Hi!

I just upgraded from Ubuntu 9.10 to 10.04, and everything is more or less fine, except for the screen resolution.. everything is really too big. I went to 'appearances', 'fonts', 'details' and changed the dots per inch, but that only solves part of the problem (it only makes some words smaller, icons and windows are still too big)
the problem is that in 'monitors', the highest resolution I can find is 800x600
would it be possible to add resolutions?

or is there another solution?

thanks!

---

### Post by P05TMAN on 2011-09-15
> **agramahisi said:**
> Hi!

I just upgraded from Ubuntu 9.10 to 10.04, and everything is more or less fine, except for the screen resolution.. everything is really too big. I went to 'appearances', 'fonts', 'details' and changed the dots per inch, but that only solves part of the problem (it only makes some words smaller, icons and windows are still too big)
the problem is that in 'monitors', the highest resolution I can find is 800x600
would it be possible to add resolutions?

or is there another solution?

thanks!

Haven't had that issue myself, but I did find this wiki that may suffice to help you out in your situation: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by agramahisi on 2011-09-16
hm.. creating the new resolution works fine (I think, the terminal doesn't give any answer after the last command, but I suppose that's not necessary?), but when I want to add it, he says he doesn't find the output:

madelief@madelief-desktop:~$ cvt 1440 960
# 1440x960 59.98 Hz (CVT) hsync: 59.74 kHz; pclk: 113.75 MHz
Modeline "1440x960_60.00"  113.75  1440 1528 1672 1904  960 963 973 996 -hsync +vsync
madelief@madelief-desktop:~$ xrandr --newmode ^C
madelief@madelief-desktop:~$ xrandr --newmode "1440x960_60.00" 113.75 1440 1528 1672 1904 960 963 973 996 -hsync +vsync

madelief@madelief-desktop:~$ xrandr --addmode S-video 1440x960
xrandr: cannot find output "S-video"

--> any suggestion?

---

### Post by agramahisi on 2011-09-16
I'm not sure about the resolution neither actually, I just wanted a bigger one and found this as a possible resolution on the internet...

---

### Post by realzippy on 2011-09-16
> **agramahisi said:**
> 
xrandr: cannot find output "S-video"

--> any suggestion?
..what does 
```
xrandr -q
```
show ?

---

### Post by agramahisi on 2011-09-16
something else that is worrying me, is that it says that the maximum resolution is 800x600... but I know my screen can do better than that!:

madelief@madelief-desktop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   720x576        60.0  
   800x480        60.0  
   720x480        60.0  
  1440x960_60.00 (0x9d)  113.0MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   59.3KHz
        v: height  960 start  963 end  973 total  996           clock   59.6Hz

(PS; the last resolution of 1440x960 is the result of my try-outs of before, it wasn't there originally, and if I go to the institutions of my computer it still isn't there neither)

I will stop trying now, and wait for an answer, before I create an even bigger mess..

---

### Post by agramahisi on 2011-09-16
> **realzippy said:**
> ..what does 
```
xrandr -q
```
show ?
madelief@madelief-desktop:~$ xrandr -q
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   720x576        60.0  
   800x480        60.0  
   720x480        60.0  
  1440x960_60.00 (0x9d)  113.0MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   59.3KHz
        v: height  960 start  963 end  973 total  996           clock   59.6Hz
madelief@madelief-desktop:~$

---

### Post by realzippy on 2011-09-16
> **agramahisi said:**
> something else that is worrying me, is that it says that the maximum resolution is 800x600...

...correct,you will not be able to run added modes bigger than the maximum xrandr reports.
So you have some trouble to solve first.
Show

```
lspci | grep VGA
```

---

### Post by agramahisi on 2011-09-16
> **realzippy said:**
> ...correct,you will not be able to run added modes bigger than the maximum xrandr reports.
So you have some trouble to solve first.
Show

```
lspci | grep VGA
```
madelief@madelief-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)

---

### Post by realzippy on 2011-09-16
> **agramahisi said:**
> madelief@madelief-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
..VIA,that is bad.
Anyway,did you have bigger resolutions available before upgrading?

---

### Post by agramahisi on 2011-09-16
> **realzippy said:**
> ..VIA,that is bad.
Anyway,did you have bigger resolutions available before upgrading?
yes, but I don't remember the exact numbers.. I do remember I've had to bring my computer to somebody to arrange a whole lot of things after installing ubuntu though, and resolution was only one of the problems.. 
and now that person isn't here anymore.
can I do something, although VIA is bad?

---

### Post by realzippy on 2011-09-16
We will try.
Did you run a system upgrade or did you make a fresh install ?

---

### Post by agramahisi on 2011-09-16
a system upgrade, from within the upgrade manager

---

### Post by realzippy on 2011-09-16
Ok,maybe there was a xorg.conf file before you upgraded,which is still around as backup.
Show output from:

```
locate xorg.conf
```

---

### Post by agramahisi on 2011-09-16
> **realzippy said:**
> Ok,maybe there was a xorg.conf file before you upgraded,which is still around as backup.
Show output from:

```
locate xorg.conf
```
/etc/X11/xorg.conf
/etc/X11/xorg.conf.bak
/etc/X11/xorg.conf.dist-upgrade-201109151901
/etc/X11/xorg.conf:bqk~
/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz
/var/lib/x11/xorg.conf.md5sum

---

### Post by realzippy on 2011-09-16
You have a current xorg.conf ....
show it's content please

```
gedit /etc/X11/xorg.conf
```

---

### Post by agramahisi on 2011-09-16
> **realzippy said:**
> You have a current xorg.conf ....
show it's content please

```
gedit /etc/X11/xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#Identifier "Generic Keyboard"
#Driver "kbd"
#Option "XkbRules" "xorg"
#Option "XkbModel" "pc105"
#Option "XkbLayout" "es"
#EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#Identifier "Configured Mouse"
#Driver "mouse"
#EndSection

Section "Device"
Identifier "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
Driver "openchrome"
BusID "PCI:1:0:0"
Option "DisableIRQ"
Option "XAANoOffscreenPixmaps" "true"
Option "DRI" "true"
EndSection


Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
HorizSync 30-107
VertRefresh 48-120
EndSection
Section "Screen"
Identifier "Default Screen"
Device "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
Monitor "E151FP"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
Load "dbe"
EndSection

Section "DRI"
Group "video"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by realzippy on 2011-09-16
...no idea if the openchrome driver (which should be started with your xorg.conf) still works in 10.04...
We can try a simple xorg.conf calling the vesa driver,or test
without any xorg.conf...
Let's 1rst have a look at your log file

/var/log/Xorg.0.log

attach that file,might be too big for posting

---

### Post by agramahisi on 2011-09-16
hm, but where do I past that command? if I want to close the terminal to open a new one, it says that there's still a command in process, and if I paste it underneath, it doesn't answer:

madelief@madelief-desktop:~$ gedit /etc/X11/xorg.conf

/var/log/Xorg.0.log

---

### Post by agramahisi on 2011-09-16
ok, I opened a new one, with the other still open, and this is the result:

madelief@madelief-desktop:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied

---

### Post by realzippy on 2011-09-16
It is no command,it is a path.
Open nautilus (file browser) and navigate to the folder
/var/log

there you will find Xorg.0.log ....

---

### Post by agramahisi on 2011-09-16
ok 

there are three files, one I copied, and it's in attachment, it's the one you asked.
beside that one, there is also a Xorg.1.log, do you want that one too?
and there's also a Xorg.0.log.old, but he can't open it, he needs a special application to open backups (or something like that)

---

### Post by realzippy on 2011-09-16
This was the right file,thanks.

```
Not using default mode "1024x768" (vrefresh out of range) 
```

..this is from your log.
Since Vrefresh (48-120) clearly is not out of range,I have no idea
why this mode is refused.
Which monitor do you use ?
Is it that DELL E151FP  (from xorg.conf) ?

---

### Post by agramahisi on 2011-09-16
Which monitor do you use ?
Is it that DELL E151FP  (from xorg.conf) ?[/QUOTE]

--> I don't know, how can I find out?..

---

### Post by realzippy on 2011-09-16
If it is a separate monitor,there will be something written on it's back.
If it is a laptop, which one?

---

### Post by agramahisi on 2011-09-16
yes, packard bell easynote R1931

---

### Post by realzippy on 2011-09-16
And you do not use a separate monitor?
Asking because your current xorg.conf is made for a DELL Monitor
(although Vrefresh and Hsync values are wrong,means for a CRT display).

If it is [this laptop]("http://www.onyougo.com/packard-bell-easynote-r1931-pb42b01790-notebookslaptops-features_pi733611e2"),
your screen resolution should be 1280x800.

---

### Post by agramahisi on 2011-09-16
it is exactly that laptop, and I don't use any other seperate monitor..
screen resolution is not like that, unfortunately.. :(

---

### Post by realzippy on 2011-09-16
Ok,suggest we use a minimal xorg.conf:

run
```
gksudo gedit /etc/X11/xorg.conf
```

delete everything (backup not needed,we have one here in this thread).
Then paste into the (now) empty file:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync 31-60
        VertRefresh 56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Then reboot..

---

### Post by agramahisi on 2011-09-16
sorry, but eh.. how do I reboot?
(I prefer to ask it than to do something stupid)
does it mean saving it?

---

### Post by realzippy on 2011-09-16
When you shut down your computer,there is also a restart option.
Or shutdown,then turn it on again  ;-)

...or run

```
sudo reboot now
```

---

### Post by madjr on 2011-09-16
just wondering...

would a fresh install detect the resolutions or he would had add the monitor config manually anyway?

---

### Post by agramahisi on 2011-09-16
but then I have to save the whole thing first, no?
I know it might be a stupid question, but I'm afraid of saving something so delicate, I'm not used to changing the 'essence' of my computer myself...

---

### Post by realzippy on 2011-09-16
> **madjr said:**
> just wondering...

would a fresh install detect the resolutions or he would had add the monitor config manually anyway?

I don't think there would be a difference between fresh install and upgrade.
The problem seems to be that the newer kernel /Xserver has a problem with that openchrome driver.
Next suggest will be starting without any xorg.conf,if the minimal xorg.conf
doesn't work.
Feel free to make suggestions,since all I can do is trial and error,since
I don't have a VIA graphics device (which is something to avoid if possible ;-) )

---

### Post by realzippy on 2011-09-16
> **agramahisi said:**
> but then I have to save the whole thing first, no?
I know it might be a stupid question, but I'm afraid of saving something so delicate, I'm not used to changing the 'essence' of my computer myself...

Yes,of course,close file saving changes you made.
Btw,don't worry,it not is the "essence"...

---

### Post by agramahisi on 2011-09-16
yuhuw!! realzippy you did it!! cool, thanks! :)
hm... so if I have the same problems the next time I update, should I just do exactly the same then?
'cause I was thinking of upgrading until the latest version, but I'm seriously reconsidering it already...

---

### Post by rolnics on 2011-09-16
I keep a working xorg file and have done since hardy, as I have resolution with my dodgy hardware!

So just keep a backup of xorg.conf and a note of where it should be (/etc/x11) and that should be it.

---

### Post by agramahisi on 2011-09-16
uy.. that's too difficult for me.. don't understand of what I have to take a backup (the thing I just saved, or the contents it had before?) and the thing of where it should be is not so clear to me neither..

---

### Post by realzippy on 2011-09-16
> **agramahisi said:**
> yuhuw!! realzippy you did it!! cool, thanks! :)
Not exactly,we now use the vesa driver instead of openchrome.Honestly,
I don't think there is a big difference between those.You have to judge:
Everything working as it did formerly?If there is something not working,
we could try to use the openchrome driver with a different xorg.conf file,
or not using any xorg.conf at all and see how the kernel handles it...
> **agramahisi said:**
> 
hm... so if I have the same problems the next time I update, should I just do exactly the same then?
'cause I was thinking of upgrading until the latest version, but I'm seriously reconsidering it already...
I highly recommend to stay with 10.04 since it is a LTS version.
Also it might be possible that your card won't run unity...

---

### Post by agramahisi on 2011-09-16
ok, I won't update then.
I don't know, for the moment everything i'm doing is working out fine. movies seem to be ok, sound also.. what could go wrong? what could I check more then?

---

### Post by realzippy on 2011-09-16
The changes we made only affect graphics.
If you don't have any graphic glitches....then everything is ok.
I will keep subscribed to this thread,so if you should notice
a problem,just post again here and I will have a look.
Have fun!

...and set thread as solved (threadtools)

---

### Post by madjr on 2011-09-16
> **agramahisi said:**
> ok, I won't update then.
I don't know, for the moment everything i'm doing is working out fine. movies seem to be ok, sound also.. what could go wrong? what could I check more then?

i dont think anything would go wrong.

just stay with the this LTS, till the next one (unity 2d should be available by then and most probably run fine).

but next time test it on a live-cd and install to a **new separate testing partition**, so if there are problems with the new one, you have the old one to fall back to.

Enjoy!

---

### Post by agramahisi on 2011-09-16
ok, thanks a lot!!

---

### Post by realzippy on 2011-09-16
> **madjr said:**
> 
..install to a **new separate testing partition**, so if there are problems with the new one, you have the old one to fall back to.
Enjoy!
+1
It is always a good idea to have a few ubuntu versions on one machine
for testing purpose...

---

### Post by agramahisi on 2011-09-28
> **realzippy said:**
> The changes we made only affect graphics.
If you don't have any graphic glitches....then everything is ok.
I will keep subscribed to this thread,so if you should notice
a problem,just post again here and I will have a look.
Have fun!

...and set thread as solved (threadtools)
hm... 
well apparently there is a problem after all.. I have problems with youtube videos and grooveshark. the message grooveshark displays is the following:

We had a problem loading Flash. You may have a Flash blocker installed.
If so, please disable the blocker (or add an exception) and reload to
start listening.

the problem with the videos on youtube is that he opens them, but he doesn't play them well. They get stuck every second. And if there are video's on other webpages I'm just not able to open them...

any suggestion?...

---

