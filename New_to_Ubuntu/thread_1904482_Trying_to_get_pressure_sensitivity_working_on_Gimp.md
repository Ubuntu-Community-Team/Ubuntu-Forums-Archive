---
title: "Trying to get pressure sensitivity working on Gimp."
date: 2012-01-04
forum: New to Ubuntu
---

### Post by SonicNo2 on 2012-01-04
This topic can be moved if needed. But I am posting here because I am still new to the Ubuntu OS. (Using 11.10 by the way)

The problem is that I'm trying to get the pressure sensitivity to work on this OS (specifically Gimp.)

So I using a very old graphic tablet called "Acecad Flair USB."

So I went to their site which is this: [[Link]]("http://acecad.sourceforge.net/")

But I was stuck on step three though... I only know how to use the terminal so, am I missing something?

Then I thought maybe I should look for something else which I did: [[Link]]("https://help.ubuntu.com/community/TabletSetupWizardpen")

The thing is I don't know if its working or not, but as it turns out, the Tablet wasn't turned on in the Gimp. When I turned it on and used it I get this...

[IMG]http://i50.photobucket.com/albums/f339/SonicNo2/Screenshotat2012-01-04194342.jpg[/IMG]

Weird right? Want to know what is more odd? My pressure sensitivity works very well in MyPaint!

Also I hate to address another issue but I am also having a problem with the "out of the box" bug in my tablet. I don't even know how to fix this and I couldn't understand this topic: [[Link]]("http://ubuntuforums.org/showthread.php?t=944946")

Sorry if this is too much. I thought I already know to deal with new OSes but I guess not.

---

### Post by Favux on 2012-01-05
Hi SonicNo2,

Welcome to Ubuntu forums!

Let's start with Oneiric bug that is affecting Gimp.  See this Lauchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  To fix it install Aapo Rantalainen's PPA that has the Oneiric Gimp with Alexia Death's fix/patch "turn off the history buffer" applied:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)

Oneiric no longer has the WizardPen driver in the repositories so it is great that you mangaged to install it.  How did you manage that by the way?  I'm assuming that is what you used the TabletSetupWizardpen wiki for.  If you have pressure in MyPaint I'm thinking it might be WizardPen but maybe it is the evdev driver instead.  Evdev is actually the driver that is now used instead of WizardPen.  We could get an idea if you are interested by you posting the outputs of the following commands entered in a terminal:
```
lsusb
```
and
```
xinput list
```
With lsusb we just want the tablet line.  With xinput list the whole thing.

Depending on the tablet model the newer WizardPen driver should take care of things by default.  Its 70-wizardpen.conf and udev rules handle most of the known older tablets.  The same should be true of the evdev driver.  So that link to the "out of the box" stuff is hopefully obsolete for you.

---

### Post by SonicNo2 on 2012-01-05
A new problem now. Great. I don't know if this once is an common issue but it might be easy for you guys to understand...

[IMG]http://i50.photobucket.com/albums/f339/SonicNo2/problem.jpg[/IMG]

Got the other 2 source list and there is one floating around.

No wonder I was unable to click on the Ubuntu Software Center. I mean I need to uninstall Gimp in order to reinstall it with the patch. (Right?)

Thanks for the help.

---

### Post by Laobi on 2012-01-05
> **SonicNo2 said:**
> A new problem now. Great. I don't know if this once is an common issue but it might be easy for you guys to understand...

[IMG]http://i50.photobucket.com/albums/f339/SonicNo2/problem.jpg[/IMG]



Can't help you with your original problem, but this one here seems like a typo made when adding new software sources.  Check with a text editor the first line of this file: ```
/etc/apt/sources.list.d/doctormo-xorg-wizardpen-oneiric.list
```

It probably has something like this (missing letter [COLOR="Red"]m[/COLOR]): ```
deb http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu oneiric ain
``` while it should actually have something like this: ```
deb http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu oneiric [COLOR="Red"]m[/COLOR]ain
```
Correct the line using a text editor.

---

### Post by Favux on 2012-01-05
DoctorMO's WizardPen PPA does not include an Oneiric version:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages)  As I mentioned the X driver is now evdev not wizardpen.  Open Update Manager and Close the error message.  In the lower left click on Settings and then the Other Software tab.  Select the DoctorMO PPA and then Remove it.  Close out Update Manager.  You should then be able to use it or the Software Center.  I hope.

The Gimp PPA should just install over the current Gimp without a need to uninstall the current Gimp.

---

### Post by SonicNo2 on 2012-01-05
[IMG]http://i50.photobucket.com/albums/f339/SonicNo2/yayitworks.jpg[/IMG]

Yay it works! Thanks a lot. You guys are awesome. No need for me to use Windows XP.

However the "out of the box" thing is still there but I really don't find it a major issue.

Also if you are interested Favux,

```
~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:5611 Hewlett-Packard PhotoSmart C3180
Bus 001 Device 003: ID 0ace:1215 ZyDAS ZD1211B 802.11g
Bus 002 Device 002: ID 0460:0004 Ace Cad Enterprise Co., Ltd Tablet (5x3.75)
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
```

```
~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ACECAD USB Graphics Tablet              	id=8	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
```

---

### Post by Favux on 2012-01-05
Nice!  :)

Thank you for those outputs.  Now that's interesting because the Ace Cad usb hid driver, hid-acecad.c is empty in the 3.2 kernel.  So some other usb kernel driver must be picking up the tablet.  And it is supporting pressure!
Vendor ID = 0460 = Ace Cad
Product ID = 0004 = Acecad Flair USB

Could you now post the output of?:
```
xinput list-props "ACECAD USB Graphics Tablet"
```

---

### Post by SonicNo2 on 2012-01-05
> **Favux said:**
> Nice!  :)

Thank you for those outputs.  Now that's interesting because the Ace Cad usb hid driver, hid-acecad.c is empty in the 3.2 kernel.  So some other usb kernel driver must be picking up the tablet.  And it is supporting pressure!
Vendor ID = 0460 = Ace Cad
Product ID = 0004 = Acecad Flair USB

Could you now post the output of?:
```
xinput list-props "ACECAD USB Graphics Tablet"
```

```
~$ xinput list-props "ACECAD USB Graphics Tablet"
unable to find device ACECAD USB Graphics Tablet
```

Hmm. :o

---

### Post by Favux on 2012-01-05
Hmmm is right.  The "device name" is correct from *xinput list*.  The command is right.  Was the tablet plugged in?  You can also use the ID # like so:
```
xinput list-props 8
```
But the ID number can change on a reboot or a hotplug.

We could get the same information from your Xorg.0.log in /var/log.

---

