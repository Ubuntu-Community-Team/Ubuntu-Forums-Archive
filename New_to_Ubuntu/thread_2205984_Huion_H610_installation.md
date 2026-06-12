---
title: "Huion H610 installation"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by darkroast2 on 2014-02-16
Hi everyone,

I'm new to Linux. I've installed Kubuntu 13.10 today. So far, I'm very confused. I don't really know how to do anything yet.

The forums had some information about installing the Huion H610 tablet drivers that were a bit too advanced for me. I've installed wizardpen 0.8.1 following a set of instructions I've found for installing software on Linux. It seems it went okay. No errors after installing all dependencies/prerequisites. I've also tried a couple of commands I found on that advanced thread I mentioned.

Here is what **lsusb** gives me for my Huion H610 tablet: 
**Bus 001 Device 011: ID 256c:006e  **

**xinput list** gives the following for my tablet (note that it's only 1 result, not 3; the user in the advanced thread had 3 results):
**&#8627; HUION HuionH610                           id=12   [slave  pointer  (2)]**

And finally, **xinput list-props 12** returns:
[B]Device 'HUION HuionH610':
        Device Enabled (132):   1
        Coordinate Transformation Matrix (134): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (255):     0
        Device Accel Constant Deceleration (256):       1.000000
        Device Accel Adaptive Deceleration (257):       1.000000
        Device Accel Velocity Scaling (258):    10.000000
        Device Product ID (249):        9580, 110
        Device Node (250):      "/dev/input/event14"
        Evdev Axis Inversion (259):     0, 0
        Evdev Axis Calibration (260):   <no items>
        Evdev Axes Swap (261):  0
        Axis Labels (262):      "Abs X" (280), "Abs Y" (281), "Abs Z" (282), "Abs Rotary X" (283), "Abs Pressure" (284)
        Button Labels (263):    "Button Left" (135), "Button Middle" (136), "Button Right" (137), "Button Wheel Up" (138), "Button Wheel Down" (139)
        Evdev Middle Button Emulation (264):    0
        Evdev Middle Button Timeout (265):      50
        Evdev Third Button Emulation (266):     0
        Evdev Third Button Emulation Timeout (267):     1000
        Evdev Third Button Emulation Button (268):      3
        Evdev Third Button Emulation Threshold (269):   20
        Evdev Wheel Emulation (270):    0
        Evdev Wheel Emulation Axes (271):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (272):    10
        Evdev Wheel Emulation Timeout (273):    200
        Evdev Wheel Emulation Button (274):     4
        Evdev Drag Lock Buttons (275):  0[/B]



The issue I'm having is that the cursor has a huge delay and is very slow to move when I'm using the tablet. Furthermore, the buttons don't work properly. For example, the tip doesn't even touch the tablet and it acts as if it is touching (left click). The barrel buttons don't seem to work either. They should be left and right click (or customizable).

Could anyone give me instructions aimed at a Windows pro/Linux newbie?

I don't know if it makes any difference, but I've tried this with GIMP. When I try with Krita,  I get dots instead of a line. The movement of the cursor isn't slow, but there's clearly a delay in responsiveness (works fine with a mouse), and I'm still having the issue of the pen tip not touching the pad yet it still registers as if it is touching.


Thanks in advance!

---

### Post by steve5139 on 2014-02-18
Hang in there roastie! I'm just setting mine up and when I'm happy I will show you how to do it. ;)

---

### Post by steve5139 on 2014-02-19
My system is a bit different from yours (different DE): Linux Mint 16 (Petra) with MATE desktop, kernel version 3.11 running on a Dell D620 laptop.

I consulted these pages (as probably you have too):
[Main wizardpen HowTo page]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen") 
[Stuff about xinput & friends here]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev#X.org_configuration")
And [wizardpen at launchpad]("http://wizardpen at launchpad") just to make sure I got the latest version (which I did and so did you: 0.8.1)

Note that my basic text editor in MATE is pluma. Just replace pluma in the code below with whatever text editor you prefer (kate ...?). You've probably done a lot of this already but here is what I did step-by-step (at the terminal):


[LIST]
[*]Download wizardpen, install packages it requires, compile & install: 
[/LIST]
[INDENT][FONT=courier new][SIZE=2]mkdir huion.tmp
[/SIZE][/FONT][/INDENT]
[INDENT][FONT=courier new][SIZE=2] cd huion.tmp
wget [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+files/xserver-xorg-input-wizardpen_0.8.1-0ubuntu3.tar.gz](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+files/xserver-xorg-input-wizardpen_0.8.1-0ubuntu3.tar.gz)
tar xzvf xserver-xorg-input-wizardpen_0.8.1-0ubuntu3.tar.gz
sudo apt-get install build-essential xutils-dev xutils libx11-dev libxext-dev xautomation xinput xserver-xorg-dev autoconf libtool pkg-config
cd xserver-xorg-input-wizardpen-0.8.1/
./autogen.sh --prefix=/usr
make
sudo make install[/SIZE]
[/FONT][/INDENT]

[LIST]
[*]Edit config files: 
[/LIST]
[INDENT][FONT=courier new]sudo pluma /usr/share/X11/xorg.conf.d/70-wizardpen.conf
[/FONT][/INDENT]
[INDENT=2][FONT=courier new]# comment out MatchIsTablet line (put a # at the beginning of it). Save, Quit.
[/FONT][/INDENT]
[INDENT][FONT=courier new] xinput list     # Look for the line that looks like referring to your tablet, for me it's this:
[/FONT][/INDENT]
[INDENT=2][FONT=courier new]&#9116;   &#8627; HUION H610                                  id=12    [slave  pointer  (2)]
[/FONT][/INDENT]
[INDENT][FONT=courier new]sudo mkdir /etc/X11/xorg.conf.d
sudo pluma /etc/X11/xorg.conf.d/52-tablet.conf
[/FONT][/INDENT]
[INDENT=2][FONT=courier new]# cut and paste the generic template from the **Custom tablet .conf** section of sourceforge Tablet HowTo linked above
[/FONT][/INDENT]
[INDENT=2][FONT=courier new]# change "keyword" to "HUION H610". Save, Quit.[/FONT]
[/INDENT]

[LIST]
[*]Restart X (or just reboot) 
[*]Pull up a terminal again and check that wizardpen is in control of the H610: 
[/LIST]
[INDENT][FONT=courier new]grep wizardpen /var/log/Xorg.0.log    # something like this:
[/FONT][/INDENT]
[INDENT=2][FONT=courier new]...
[/FONT][/INDENT]
[INDENT=2][FONT=courier new][    10.781] (II) Using input driver 'wizardpen' for 'HUION H610'[/FONT]
[/INDENT]

[LIST]
[*]Tweaking / Calibrating 
[/LIST]
[INDENT][FONT=courier new]sudo apt-get xinput-calibrator
xinput_calibrator --list | grep H610  # you should see something like this (note the id No.):
[/FONT][/INDENT]
[INDENT=2][FONT=courier new]Device "HUION H610" id=12
[/FONT][/INDENT]
[INDENT][FONT=courier new]xinput_calibrator --device 12      # just let it do its thing, don't click on the crosshairs; you'll get sthg like:
[/FONT][/INDENT]
[INDENT=2][FONT=courier new]Calibrating standard Xorg driver "HUION H610"
    current calibration values: min_x=2000, max_x=38000 and min_y=1250, max_y=23750
    If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).[/FONT]
[/INDENT]

[LIST]
[*]Take note of min_x, max_x, min_y, max_y. These will correspond to values you'll need to put in config file /etc/X11/xorg.conf.d/52-tablet.conf, which after 
[/LIST]
[INDENT=2][FONT=courier new]sudo pluma /etc/X11/xorg.conf.d/52-tablet.conf    # Edit, Save, Quit.[/FONT]
[/INDENT]
[INDENT]for me looks like this:

[/INDENT]
[INDENT=2]Section "InputClass"
        Identifier "Tablet on WizardPen"
        MatchIsTablet "on"
        MatchProduct "HUION H610"
        MatchDevicePath "/dev/input/event*"
        Driver "wizardpen"
        # Apply custom Options below.
   Option "TopX" "2000"
   Option "TopY" "1250"
   Option "BottomX" "38000"
   Option "BottomY" "23750"
   Option "ButtonMapping" "1 3 0"
   Option "TopZ" "0"
   Option "BottomZ" "2047"
EndSection
[/INDENT]

[LIST]
[*]Another reboot and the thing works okay, except the ButtonMapping line above did not work. I have to do it manually every time I reboot: 
[/LIST]
[INDENT][FONT=courier new]xinput set-button-map "HUION H610" 1 3 0[/FONT]
[/INDENT]

I cannot get the third button working at all and the second button (the one closest to the tip) repeats if held down. I cannot get any pressure sensitivity either. (That's what the TopZ and BottomZ options above are meant to be for.) Also, after I put the computer into hybernation it stops working until I reboot.

Hope this helps. If anyone knows how to get pressure sensitivity working please let us know.

---

### Post by darkroast2 on 2014-02-24
Thanks Steve!

I just checked on this and found your reply, and have just tried out the steps you provided. I think I may have messed it up by trying other things in the past few days. Instead of wizardpen being in control of my tablet, it's evdev (as per /var/log/Xorg.0.log). What did I do wrong, and how can I fix it?

---

### Post by darkroast2 on 2014-02-24
I found something that works!

According to this site: [http://libregraphicsworld.org/blog/entry/krita-gets-support-for-huion-graphic-tablets](http://libregraphicsworld.org/blog/entry/krita-gets-support-for-huion-graphic-tablets)
"Nikolai Kondrashov, leader of the [DIGImend]("http://libregraphicsworld.org/blog/entry/digimend-makes-low-budget-graphic-tablets-just-work-on-linux") project, reviewed the driver's code and ended up writing [his own one]("https://github.com/DIGImend/huion-driver")."

I tried it out. Instructions are in the same link as the download (just scroll down). It works perfectly, barrel buttons, tip, and all!
Well, I haven't tested the pressure yet. Testing...
Krita: failed. (keep in mind, I didn't take the time to see if there's a setting I need to change in Krita yet)
Gimp: Worked, but not as much as the tablet is capable of. The pressure option was turned off by default, I had to go in Edit> Input Devices> Huion H610> Pressure and set to Screen instead of Disabled. There are other options to change.

Anyway, I think with a bit of tweaking, it should be working perfectly in no time. Fantastic! With this working, I can say goodbye to Windows for good!

---

### Post by darkroast2 on 2014-02-24
Oh, where are my manners... Thank you! I appreciate your help!

---

### Post by darkroast2 on 2014-02-24
Hrm... That's weird... After installing the drivers and using it for a bit, the same issue with the pen came back. The pen seems to seem it's making contact without actually making contact. This is a new pen, because the old pen was doing that and I couldn't get it to stop (even in Windows 7!). I thought the pen was defective. Well, this is a brand new pen, used it for under a half hour. After installing the tablet on Kubuntu and testing for a few minutes, the issue is back. Tested on Windows 7, same thing! Is this happening to you as well? You mentioned the second button repeats. How about the tip? Does it repeat without even touching the tablet (just needs to be close to it)?

---

### Post by darkroast2 on 2014-02-25
A quick update on the issue - The driver should be fine. The problem I have is with the tablet itself. It wasn't the pen.

Apparently, Linux allows you to use any pen on any tablet. This wouldn't work on Windows. Anyway, I tried my Huion pen on my Monoprice tablet. It works fine. I tried my Monoprice pen on my Huion tablet and I get the same issue, where it registers left-mouse-clicks without there being any. It seems to do it every 3 seconds. I've contacted the company to replace the tablet. They were surprisingly fast with the pen replacement, it only took 3 business days from China! Anyway, I'll update this thread if I get the same issue with the replacement tablet.

---

### Post by steve5139 on 2014-02-27
Hey darkroast2, Thanks for the info re the other driver. THough I'm not clear on how to install it. Even which files I need. Downloading them is tedious. ("Save link as" just downloads a html page...) Am I blind? is there no package, a tar.gz or something? I can do it manually though, saving as text, one file at a time; just seems odd...

But more specifically, I am not sure what is meant by

  *To install the driver and the associated rebinding script run "make install" as root in the source directory.*

i.e. the "associated rebinding script", what is that?? Could you post the list of files you needed and the commands you ran for successful installation, including any rmmod and other funny business..? Also what version kernel are you using. (I'm on 3.11 so Thanks, help much appreciated.

The evdev issue I had too (not that it's an issue for you any more). I missed a step in the instructions (I forget what - but it seems to default to the evdev driver if you confuse it).

Issues with pen: sometimes after suspend the pen stops working properly. Then I need to unplug the USB cable from the tablet for a few seconds and plug it back in (once, sometimes twice) and then it starts working again. No big deal but :-?

---

### Post by darkroast2 on 2014-02-28
Hi Steve,

Here's the link: [https://github.com/DIGImend/huion-driver](https://github.com/DIGImend/huion-driver)
When you click it, you should see a list of files. On the right side, you'll see a button that says "Download Zip". Click it to download the .zip file. Extract it in a folder of your choice, and follow the instructions at the bottom of this same page.
Here they are, just in case:

*** THIS PART SHOULD HAVE BEEN FIRST*** If you run a v3.11 or later kernel you might need to unload the mainline driver with a "rmmod hid-huion" command so this driver can be loaded, first time you use the tablet. Then, (re-)plugging the tablet should be sufficient to make it work.

To build the driver run "make" in the driver's source directory.

  To install the driver and the associated rebinding script run "make install" as root in the source directory.

  


I don't know what that means, exactly. It just works, that's all I can say. :P

You know what, here's the direct link to the .zip file in case you can't see the Download Zip button: [https://github.com/DIGImend/huion-driver/archive/master.zip](https://github.com/DIGImend/huion-driver/archive/master.zip)


Let me know if it works for you.

---

### Post by darkroast2 on 2014-02-28
Hey, don't forget to "sudo make install". It requires root user. Simply using "make install" returns an error.

---

