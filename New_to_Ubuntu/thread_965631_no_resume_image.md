---
title: "no resume image"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by limptwiglet on 2008-10-31
Hello,

After installing 8.10 and updating (gfx drivers and ubuntu updates) I rebooted my computer to be shown a prompt with "No resume image", and I cant start gnome.

I have seen posts with people trying to do xserve repair through grub but this didnt work for me.

I was just wondering if anyone could help me get it working.

Thanks for your help.

---

### Post by ezramorris on 2008-10-31
> **limptwiglet said:**
> Hello,

After installing 8.10 and updating (gfx drivers and ubuntu updates) I rebooted my computer to be shown a prompt with "No resume image", and I cant start gnome.

I have seen posts with people trying to do xserve repair through grub but this didnt work for me.

I was just wondering if anyone could help me get it working.

Thanks for your help.

What other people have said is that it hangs for 2-3 minutes, but then continues to boot.

Try leaving it for a few minutes, then if not, press Ctrl-Alt-Del and see if it continues.

If/when you get logged on, follow these instructions to resolve the problem:
> 1. Make sure you[r system is up-to-date]
2. sudo blkid
3. Check that swap line UUID from /etc/fstab matches swap UUID from step 2, if not change fstab.
4. Check that the UUID in /etc/initramfs-tools/conf.d/resume matches the swap UUID from step 2, if not change resume file.
5. sudo update-initramfs -uk all
6. Restart
[RIGHT]from [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/205990](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/205990)[/RIGHT]

Hope this helps.

---

### Post by limptwiglet on 2008-10-31
Hi,

Tried that and didnt work.
My UUID was the same in all of those places, tried sudo update-initramfs -uk all restated and the same thing again.

I should have said that when it comes up with the prompt about no resume image it also drops to a bash prompt (I think thats right).

Sorry I'm still really green to Ubuntu.

---

### Post by ezramorris on 2008-10-31
> **limptwiglet said:**
> Hi,

Tried that and didnt work.
My UUID was the same in all of those places, tried sudo update-initramfs -uk all restated and the same thing again.

I should have said that when it comes up with the prompt about no resume image it also drops to a bash prompt (I think thats right).

Sorry I'm still really green to Ubuntu.

Hi, would you mind pasting the output of all those things, just to make sure?

---

### Post by limptwiglet on 2008-10-31
sudo blkid
b22a70f4-1bc1-457c-b711-473e1e5c31e5

conf.d/resume
b22a70f4-1bc1-457c-b711-473e1e5c31e5

fstab
b22a70f4-1bc1-457c-b711-473e1e5c31e5

---

### Post by ezramorris on 2008-10-31
> **limptwiglet said:**
> sudo blkid
b22a70f4-1bc1-457c-b711-473e1e5c31e5

conf.d/resume
b22a70f4-1bc1-457c-b711-473e1e5c31e5

fstab
b22a70f4-1bc1-457c-b711-473e1e5c31e5

I actually meant the whole files ;-)

Basically, because I made the mistake of missing out the UUID= in 'resume'.
I.e. it should be **RESUME=UUID=**b22a70f4-1bc1-457c-b711-473e1e5c31e5

---

### Post by limptwiglet on 2008-10-31
Im working on a laptop while my main machine is borxed. So I'm not sure I can paste the files to you :D.
The resume file does have RESUME=UUID=b22a.......

---

### Post by limptwiglet on 2008-10-31
Can anyone offer any advice?
It will not resume if I just leave it, this is the output:

```

Loading, please wait...
19+0 records in
19+0 records out
kinit: trying to resume from /dev/disk/by-uuid/b22a70f4-1bc1-457c-b711-473e1e5c31e5
kinit: No resume image, doing normal boot...

Ubuntu 8.10 skabot tty1

skabot login:

```

---

### Post by ezramorris on 2008-10-31
> **limptwiglet said:**
> Can anyone offer any advice?
It will not resume if I just leave it, this is the output:

```

Loading, please wait...
19+0 records in
19+0 records out
kinit: trying to resume from /dev/disk/by-uuid/b22a70f4-1bc1-457c-b711-473e1e5c31e5
kinit: No resume image, doing normal boot...

Ubuntu 8.10 skabot tty1

skabot login:

```

hmm. Try logging in at that prompt with your usual username and password, then running
```
sudo /etc/init.d/gdm start
```
and seeing what you get.

---

### Post by OlorinIWas on 2008-10-31
^did not work for me...kdm is already running.

---

### Post by ezramorris on 2008-10-31
> **OlorinIWas said:**
> ^did not work for me...kdm is already running.

Try replacing start with restart

---

### Post by limptwiglet on 2008-11-01
Tried start and restart and it said it started Gnome but there was no GUI and startx didnt work either.

---

### Post by limptwiglet on 2008-11-01
I've seen in other threads people talk of nvidia drivers causing problems so I tried installing envyng drivers but that didn't seem to make any difference.

Surley someone out here knows the answer :D.

Thanks

Mark

---

### Post by alienexplorers on 2008-11-01
I had the same problem and by changing my xorg.conf file I was able to straighten things out.
> terminator@terminator-desktop:~$ cat /etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder57)  Mon Oct 27 14:38:08 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA703 SERIES"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    ModeLine       "1280x1024_60.00" 108.9 1280 1360 1496 1712 1024 1025 1028 1060 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option	   "NoLogo"
    Option	   "AddARGBGLXVisuals"   "true"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by limptwiglet on 2008-11-01
I'm not sure what I would be changing but ill give it ago.

---

### Post by limptwiglet on 2008-11-01
Looked at my xorg.conf and it was very shot and only had the following:

Section "Device"
        Identifier      "Configured Video Device"
End Section

Section "Monitor"
        Identifier      "Configured Monitor"
End Section

Section "Screen"
        Identifier      "Default screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"


I'm total lost as to what I can do!
Please help

Thanks

---

### Post by iSTRONG on 2008-11-01
i have the same problem as OP. no solution? :(

---

### Post by ezramorris on 2008-11-01
> **limptwiglet said:**
> I've seen in other threads people talk of nvidia drivers causing problems so I tried installing envyng drivers but that didn't seem to make any difference.

Surley someone out here knows the answer :D.

Thanks

Mark

Just try Alt-F7 after running the gdm start thing.

Otherwise you could try moving your xorg.conf, and letting Ubuntu work out your settings for you.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo /etc/init.d/gdm restart
Alt-F7 if necessary
```

If X starts, you will be prompted with a few menus. Choose to recover, then use generic settings. When it says you need to restart, just press Ctrl-Alt-Backspace, then
```
sudo /etc/init.d/gdm restart
```
Alt-F7 if necessary

If this doesn't help you can move your xorg.conf back with:
```
sudo mv -f /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by Banhammer on 2008-11-01
I have the same problem. Its caused by the NVIDIA driver installation.

---

### Post by limptwiglet on 2008-11-01
If it is the NVIDIA driver how can i remove it so I can at least get onto my desktop?

---

### Post by ezramorris on 2008-11-01
> **limptwiglet said:**
> If it is the NVIDIA driver how can i remove it so I can at least get onto my desktop?

```
sudo apt-get remove nvidia-glx*
sudo apt-get autoremove
```

---

### Post by limptwiglet on 2008-11-01
Right I have tried gdm restart and I have tried removing my xorg.conf, exactly the same problem.

I removed the nvidia-glx drivers and have now gotten back into my desktop.
Thank you so much for all your help!

I'm curious are these the official drivers? Or Ubuntu's own slant on them?
Would it be worth me trying the official drivers?

Thanks

Mark

---

### Post by MindRiot on 2008-11-01
Same problem as OP. Except with ati driver.

I require the proprietary driver, so I'll reinstall 8.04.

Hopefully, this issue will be resolved. Retry 8.10 next month.

---

### Post by ezramorris on 2008-11-01
> **limptwiglet said:**
> Right I have tried gdm restart and I have tried removing my xorg.conf, exactly the same problem.

I removed the nvidia-glx drivers and have now gotten back into my desktop.
Thank you so much for all your help!

I'm curious are these the official drivers? Or Ubuntu's own slant on them?
Would it be worth me trying the official drivers?

Thanks

Mark

Ubuntu's view is that it's preferable to use open source drivers, but you can use proprietary ones if you can't get an open source alternative to work or provide the features you need.

You only really need the proprietary ones if you want desktop effects or if you want to play graphics demanding 3D games.

---

### Post by ezramorris on 2008-11-01
> **MindRiot said:**
> Same problem as OP. Except with ati driver.

I require the proprietary driver, so I'll reinstall 8.04.

Hopefully, this issue will be resolved. Retry 8.10 next month.

It (ATI driver) worked straight out the box in intrepid for me.

---

### Post by limptwiglet on 2008-11-02
I would like it for the advanced desktop effects and I will be using GIMP so really need the drivers.
Any suggestions?
I have a 2 EVGA Geforce 8800 GTS's

---

### Post by Banhammer on 2008-11-02
> **limptwiglet said:**
> I would like it for the advanced desktop effects and I will be using GIMP so really need the drivers.
Any suggestions?
I have a 2 EVGA Geforce 8800 GTS's

I too have 2 8800 GTS's, and that seems to be the problem. If I take out the second card, Ubuntu boots like normal, all the desktop effects work etc.

But when I put both cards in, I get the "no resume image, doing normal boot thing"

This problem does not exist in Hardy so im rolling back to that. Glad I solved the problem though.

---

### Post by iSTRONG on 2008-11-02
i've found the solution!

The problem is that when you got 2 video cards, xserver needs to know which one is the primary.

So you need to add
BusID "XX:YY:Z"
in the device section of xorg.conf

To find XX:YY:Z run the command lspci and search for your PRIMARY GPU. you'll find 5 numbers at the beginning of the line. that's your busID.

Edit xorg.conf and add the line in the format above.

---

### Post by Banhammer on 2008-11-02
> **iSTRONG said:**
> i've found the solution!

The problem is that when you got 2 video cards, xserver needs to know which one is the primary.

So you need to add
BusID "XX:YY:Z"
in the device section of xorg.conf

To find XX:YY:Z run the command lspci and search for your PRIMARY GPU. you'll find 5 numbers at the beginning of the line. that's your busID.

Edit xorg.conf and add the line in the format above.

Cool.

But where exactly in xorg.conf do I need to put it? And how do I get the privileges to save it?
Can you post your part of the xorg.conf as an example?

---

### Post by limptwiglet on 2008-11-02
Okay I will try that later, should I add the busid to the xorg.conf after I have installed the nvidia-glx drivers?

Thanks for all your help with this.

---

### Post by MindRiot on 2008-11-02
> **iSTRONG said:**
> i've found the solution!

The problem is that when you got 2 video cards, xserver needs to know which one is the primary.



Yes, I have two Radeon 3870s. lspci returns these two lines under 8.04.

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
02:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device

However, in Hardy, there's no line containing 01:00:0 or 02:00.0. in xorg.conf, yet the proprietary ATI driver works. It is pecular, to say the least, that Hardy has no issue with dual graphic cards.

In any event, a solution, I hope, awaits an answer to Banhammer & limptwiglet's questions.

---

### Post by ezramorris on 2008-11-02
> **Banhammer said:**
> Cool.

But where exactly in xorg.conf do I need to put it? And how do I get the privileges to save it?
Can you post your part of the xorg.conf as an example?

You need to open it as root, i.e.
```
sudo gedit /etc/X11/xorg.conf
```
from a terminal.

And you need to put it somewhere under the heading
```
Section "Device"
```

---

### Post by Banhammer on 2008-11-02
Thank you.

I got it to work, the boot sequence takes maybe 15 seconds longer than normal but it works, which is all I really care about.

Here is how my xorg.conf looks: (**I have no idea if this is correct**, but like I said, it works)

> Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
        BusID   "**XX**:**YY**:**Z**"
EndSection

---

### Post by ezramorris on 2008-11-02
> **Banhammer said:**
> Thank you.

I got it to work, the boot sequence takes maybe 15 seconds longer than normal but it works, which is all I really care about.

Here is how my xorg.conf looks: (**I have no idea if this is correct**, but like I said, it works)

Looks OK to me, as long as you replaced XX:YY:Z with what it actually was.

---

### Post by guarnibl on 2008-11-02
Can we get this stickied?

This also fixed my issues (BusID "01:00:0") -- I've got 2 8800 GT cards (512 MB) in SLI.

---

### Post by ezramorris on 2008-11-02
By the way, in case anyone was wondering, the "no resume image" message has no relevance at all to this.

In reality, assuming you shut down rather than hibernated, this message would always appear, although in the normal case it is covered up with usplash (the ubuntu loading screen) or the logon screen.

All the message means is that it can't find an image saved from a hibernate, so it will do a normal boot instead.

With regards to it being a sticky, I would be very surprised if it would be allowed, since looking at the existing stickies, they are all very generic, rather than a specific hardware problem.

---

### Post by limptwiglet on 2008-11-02
Yay!

It worked for me putting the BusID in my xorg.conf

Thank you everyone who helped me out with this, I was beginning to loose hope :D.

---

### Post by HighCommander540 on 2008-11-05
> **ezramorris said:**
> By the way, in case anyone was wondering, the "no resume image" message has no relevance at all to this.

In reality, assuming you shut down rather than hibernated, this message would always appear, although in the normal case it is covered up with usplash (the ubuntu loading screen) or the logon screen.

All the message means is that it can't find an image saved from a hibernate, so it will do a normal boot instead.

With regards to it being a sticky, I would be very surprised if it would be allowed, since looking at the existing stickies, they are all very generic, rather than a specific hardware problem.

You are both wrong and right sir. While this is not the problem that is causing our computers to not boot as normal it is the symptom that shows what the problem is.

Without this exact sequence showing up on the computer, no one would know what is wrong.

---

### Post by ezramorris on 2008-11-05
> **HighCommander540 said:**
> You are both wrong and right sir. While this is not the problem that is causing our computers to not boot as normal it is the symptom that shows what the problem is.

Without this exact sequence showing up on the computer, no one would know what is wrong.

I partly agree, however, there are a fair number of causes/problems which would cause this to be shown. It could be a problem with X (as in this case), a problem with usplash, an incorrect boot parameter, or a number of other things.

---

### Post by HighCommander540 on 2008-11-07
> **ezramorris said:**
> I partly agree, however, there are a fair number of causes/problems which would cause this to be shown. It could be a problem with X (as in this case), a problem with usplash, an incorrect boot parameter, or a number of other things.

Lol, in my rush to post and get to my destination I forgot to elaborate a bit.  Sorry, yes you are right there are many things that could cause the "No resume image" to show, but what I meant was the sequence that myself and others were getting.

Most of the time except in this cause, the prompt will show it. After it will still boot normally. In this case it would just give us a prompt as thought it was Ubuntu Server edition, because X had no idea what to do about the screen and where to put everything.

---

### Post by raj9786 on 2008-11-07
Do you think this fix would work if I only have one video card installed? I am having the same problem. THe GUI will not start and instead i get the terminal. Thanks.

---

### Post by dgavenda on 2008-11-08
I have the same problem...well similar. It's on a HP laptop (dv2500t) with nVidia Corporation GeForce 8400M GS video card.   

I get the "kinit: no resume image doing normal boot" message for my swap.  All the UUID's are the same in the different files for swap space.  

I am able to get into gnome/xfce w/o problems but booting take ~30 seconds longer due to this.  I have played w/ nvidia drivers lately and have seen no affect upon this issue.  I have tried pretty much everything I have seen in the forum.    

I don't know what the solution is but mainly here to say "Me too".  I guess we can only hope for a fix once someone figures out what is causing it.

---

### Post by OlorinIWas on 2008-12-11
Still not able to get 8.10 going...any help would be great..

It does also say somewhere in there 'primary not pci'..not exactly sure what that means...

---

### Post by MindRiot on 2008-12-22
**If**, you have two or more **ATI** graphic cards installed in your system, you need to run aticonfig before you restart your system after installing the proprietary driver. It doesn't matter whether you activate the driver using the administrative application Hardware Drivers, or you downloaded and install the package from the ATI website.

At the terminal prompt, type:


```
sudo aticonfig --initial
```


Next, type:


```
gksudo gedit /etc/X11/xorg.config
```


Your xorg.config file should look something like below, if it doesn't, then manually edit the file.


```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Hope this was helpful.

---

### Post by gmiguel on 2008-12-31
> **MindRiot said:**
> 
At the terminal prompt, type:

```
sudo aticonfig --initial
```

Hope this was helpful.

Thank you a lot MindRiot. That solved my problem.

When I installed the ATI drivers, on the next boot I got the message
```
No resume image, doing normal boot
```
and didn't had graphical interface.
Then on the command line I typed
```
sudo aticonfig --initial
```
and voilá, on the next boot the problem was solved.

Thanks again MindRiot.

---

### Post by Cambiar on 2008-12-31
Hi,
 I have 2 Nvidia 7900 GT/GTO cards and was recieving this problem, I used lspci and got

02:00:0
03:00:0

but when i tried to use gedit to edit xorg.conf it replied with this:

(Gedit:7192): Gtk-WARNING **: Cannot open display

I tried to open it with nano but it was blank.

Any help on this would be greatly apreciated, I'm getting frustrated enough to reinstall vista.

---

### Post by Cambiar on 2009-01-01
Bump

---

### Post by insomnic on 2009-01-07
try editing with vim instead:D

---

