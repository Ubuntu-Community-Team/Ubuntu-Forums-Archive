---
title: "HOWTO: Logitech G7 Mouse"
date: 2006-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by NobodySpecial on 2006-02-04
**UPDATE** 10/24/2007:  This method using the evdev driver is now obsolete.
A newer project called [btnx]("http://www.ollisalonen.com/btnx/") is MUCH easier and more feature rich.

[Ubuntu how-to HERE.]("http://ubuntuforums.org/showthread.php?t=455656")

Before changing to btnx, please remove the evdev device from xorg.conf and revert to the default device "/dev/input/mice".  You may also need to change "protocol" to "auto".

-----------------------------------------------------------------------

Logitech has put out a GREAT product that is fully usable in Ubuntu Linux once properly configured.  I've spent several frustrating hours figuring this out and hope this guide might be helpful to others.

**Big** thanks to to Endy at his thread: [http://www.ubuntuforums.org/showthread.php?t=65471]("http://www.ubuntuforums.org/showthread.php?t=65471")

**_1. Edit the xorg.conf file_**
First we'll tell X how to configure our G7.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

Scroll down until you find the mouse section, something like:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
```

REPLACE the entire mouse section from "Section "InputDevice"" to "EndSection" with the following:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option       	"Dev Name"		"Logitech USB Receiver"
	Option		"Device"		"/dev/input/mice"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5 7 8"
EndSection
```
Save the file.

Note: If the above code doesn't work for you, read the link referenced above which describes how to find a more specific "Device" and a "Dev Phys" entry using output from "cat /proc/bus/input/devices".  Note the mouse has *two* entries and you will have to experiment with both.

**_2. Restart X_**
First, bookmark this page because you will need to come back to finish.  Then _write_ down the following steps:
1. Log out like usual.
2. Simultaneously press "Control + Alt + Backspace"
3. If the mouse cursor moves like it should, log back in and procede to the next section.

If the mouse cursor won't move, simultaneously press 'CONTROL + ALT + F1" and type the following to restore your prior settings:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo restartx

```

**_3. Configure key-bindings_**
First install xvkbd and xvindkeys.
```
sudo apt-get install xvkbd xbindkeys
gedit ~/.xbindkeysrc
```

You then have two choices of code to enter.  The following code will
1. Allow the mouse "back" button to go back in Nautilus.
2. Allow the left/right tilt on the scroll wheel to scroll text left and right in programs such as Firefox when applicable.
Copy and paste the following (but see note below!):
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Right]""
  m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Left]""
  m:0x0 + b:8
```
**Change the "L" in "Left" to a capital "L" !!!**
Save the file.

_OR_ you can use my prefered code below which will
1. Allow the mouse "back" button to go back in Nautilus.
2. Allow the left/right tilt on the scroll wheel to move through open tabs in Firefox!  :D 
Copy and paste the following (but see note below!):
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Down]""
  m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Up]""
  m:0x0 + b:8
```
**Change the "L" in "Left" to a capital "L" !!!**
Save the file.

Finally, go to "System > Preferences > Sessions", click on the "Startup Programs" tab, click "+Add" and enter "xbindkeys" as a Startup Command.

Log out, then log in again and run a final test.

**Bonus:** You do *not* need the "Logitech Applet" as you can change the sensitivity settings directly on the G7 mouse by pressing the "+" and "-" buttons.  :cool:

---

### Post by QettoE on 2006-02-11
As a Kubuntu noob I really appreciate the thread... I was almost very frustrated until I saw this.

Now... my G5 has a very lousy middle button where I always miss my mid clicks and right/left scrolls. Could you tell me how I can bind all those clicks to middle click so I know that however I hit the damn button it will trigger the mid button?

Also, where in Kubuntu I can set that scirpt to run when KDE starts?

Thanks in advance,
Q.

---

### Post by NobodySpecial on 2006-02-11
I understand that you want the left/right tilt on the middle scroll wheel to do the same functions as if the scroll wheel were pressed down (i.e. middle mouse button).  I really don't know the "right" way to do this.  One way that might work is to simply configure a key-binding for whatever specific action you want.

For example, if you want to use this in Firefox to open a link in a new tab, you would look up the keyboard shortcut at  [http://www.mozilla.org/support/firefox/keyboard]("http://www.mozilla.org/support/firefox/keyboard")  and find that it is "Control + Enter".

I have not tested it, but you might _try_:
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Enter]""
  m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Control_L]\[Enter]""
  m:0x0 + b:8
```
**Change the "L" in "Left" to a capital "L" !!!**

If that doesn't work, try to substitute "Return" for "Enter".

You also ask about starting the script in KDE.  I'm using Gnome and know very little about KDE.  However, you might try to add shortcut to xbindkeys in ~/.kde/Autostart.

---

### Post by QettoE on 2006-02-12
I apprecaite it. It didn't work but with your explanation now I have an idea how this works :).

---

### Post by Pietro Pizzi on 2006-03-16
Hi,

The thing with xbindkeys works good. Now i search for a possibility to put a "double-click" on the "back-button". Is this Possible with this sollution?

---

### Post by ch13f121 on 2006-03-16
There wouldn't be a way to get something like this to work with an mx518 would there?  If so that'd be a great thing :)

---

### Post by NobodySpecial on 2006-03-18
Pietro Pizzi - I like the idea of a double-click, but the only thing I can think of is to use an "enter" or "return" command as I described above.

ch13f121 - I don't see why you couldn't make it work with other Logitech mice.  Read the (*long*) thread I referenced above (by Endy) and start experimenting with settings.

---

### Post by kingzasz on 2006-03-22
My tilt wheel is way too sensitive.  For example, I set it up for Firefox tabs like you said.  But it would move 3 tabs over.

Then I set it up to make a new tab.  It made 3 new tabs.  

Its like its getting 3 signals from one tap.  Is there any way to fix this?

Thanks,
Brian

---

### Post by NobodySpecial on 2006-03-24
king - yes, I know what you mean.  Signals get sent rapidly and I sure wish there was a way to slow it down.  All I can say is that with practice, you can learn how to "just barely" tap the wheel and make it go one tab at a time - most of the time.  :eek:

---

### Post by pianoboy3333 on 2006-05-27
X on my system complains that it can't find the protocol evdev, even with the package xserver-xorg-input-evdev

---

### Post by NobodySpecial on 2006-05-27
pianoboy3333 - I really don't know what to tell you.  I've been using Dapper now for some time, and actually evdev is broken in Dapper, so none of this is working.

I'm hoping the devs will fix this problem in the June 1 release of the final Dapper.  When that happens and I get it working again, I'll post it here or in a new "how to."

This thread will basically be obsolete in 5 days.

---

### Post by ricesteam on 2006-07-30
I have the 6.06 Drapper installed and this is what I used to get my G7 working:

Note your Phys and Device will be different from mine. You can check what your is by "cat /proc/bus/input/devices" as stated by the OP.

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Dev Name"      "Logitech USB Receiver"
        Option          "Dev Phys"      "usb-0000:00:1d.0-1/input0"
        Option          "Device"        "/dev/input/event2"
        Option          "Buttons"       "8"
        Option		"ZAxisMapping"	"4 5 7 8"
EndSection
```

Can't seem to get xbindkeys working though ... =(

---

### Post by NobodySpecial on 2006-07-30
ricesteam - glad to see you got yours going.  I have been struggling a lot with this.  I'll get it going, then another day on reboot it won't work.  Then I'll use an older version of evdev and it will work for awhile, then break.  I'm not sure why the evdev driver is so flaky.

Now I do use xbindkeys, so maybe you can post your .xbindkeysrc file and let us know what you it is you want to do.

---

### Post by ricesteam on 2006-07-31
I'm still pretty new to linux, so I'm not sure why yours is unstable.  A lot of people are reporting the evdev is a little buggy.

Actually I had to revert mine back to the default config since I couldn't get xbindkeys working; with the "logitech" config, I couldn't make my windows transparent via XGL/Compiz which is vital to showing off linux to your friends :)

Hopefully someone more experience and helpful enough can solve this problem and report back.

My .xbindkeysrc  was copied/pasted from the settings recommended by the OP. I'm not sure why it didn't work. It was loaded and xev reported that all my buttons on my G7 worked.

---

### Post by NobodySpecial on 2006-07-31
Realize that the "buttons" might be identified differently with the evdev driver.  On mine, whereas buttons 7 & 8 were previously the tilt wheel and 6 was the "back" button, now under evdev, it has buttons 6 & 7 as the tilt wheel and button 8 as the "back" button.  Thus, you would need to edit your .xbindkeysrc file accordingly.

---

### Post by ricesteam on 2006-08-02
Hmm..I'm gonna try that later tonight.

---

### Post by PigCorpse on 2006-10-01
It works, but now my tilt wheel is backwards.

Can someone explain the options to me ("Buttons", "Emulate3Button", etc.)?

---

### Post by QettoE on 2006-10-01
> **PigCorpse said:**
> It works, but now my tilt wheel is backwards.

Can someone explain the options to me ("Buttons", "Emulate3Button", etc.)?

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option       	"Dev Name"		"Logitech USB Receiver"
	Option		"Device"		"/dev/input/mice"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5 7 8"
EndSection

```

Reverse the order 4 and 5 or 8 and 7 until you get it right.

---

### Post by PigCorpse on 2006-10-08
Nope. No worky.

---

### Post by emarkay on 2006-10-09
Any updated info?

What about the middle button below the wheel on some MX mice - is there a way to emulate the Mouseware selection of "Keyboard Command" so I can set up a button to "open new page" (control "N") in Mozilla?

---

### Post by splintax on 2006-11-21
I was able to get the mouse 'working' with altered config under Edgy by setting the **driver** to "evdev". Here's my current config:
```

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
    Option        "Dev Name"		"Logitech USB Receiver"
    Option        "Dev Phys"    	"usb-0000:00:02.0-4/input0"
    Option        "Device"      	"/dev/input/event3"
    Option        "Buttons"     	"8"
    Option        "ZAxisMapping"	"4 5 7 8"
EndSection

```
Adding 'core pointer' as suggested above stops X from starting.

I still can't detect the side-scroll, even in 'xev'. Suggestions?

---

### Post by PigCorpse on 2006-11-22
Will probably need IMWheel for the tilt wheel...

---

### Post by Dave Burbank on 2007-01-08
Thanks, with a little tweaking I get every button on my G7 working properly in Edgy (side-scroll and all).

Here are the changes I made to xorg.conf:
I had to insert -- Option "CorePointer"
```
#Logitech G7
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Dev Name"      "Logitech USB Receiver"
        Option          "Dev Phys"      "usb-0000:00:1d.0-1/input0"
        Option          "Device"        "/dev/input/event2"
        Option          "Buttons"       "8"
        Option		"ZAxisMapping"	"4 5 7 8"
EndSection
```

And the setting I used for .xbindkeysrc
Notice I had change to the mouse button numbers (8,6,7) from the original. I guess the key-bindings have changed.  Check your's with 'xev'
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Right]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Left]""
  m:0x0 + b:7
```

I tried setting the tilt wheel to change tabs in firefox, but it was far too sensitive.

---

### Post by cgrado on 2007-01-29
NM. It works on my case, but not on my Icemat. i have to force it to work in windows by alt+f4ing the software for it. Is there a similar way to do that here?

And to make the buttons work, i just put that in the xorg.conf file, then follow the rest of your instructions?

---

### Post by xcafeus on 2007-10-21
tried the advice on the 1st post on Gutsy and X would not restart... Gnome would not come back and I had to restore the backup copy of xorg.conf from within RECOVERY...

any updated info on this for 7.10?

---

### Post by XavierGr on 2007-10-21
In order to make most of the buttons on my G7 work (except resolution buttons) on Kubuntu 7.10 I had to edit the mouse entry on /etc/X11/xorg.conf with this:

```

Section "InputDevice"
        Driver          "evdev"
        Identifier      "Configured Mouse"
        Option          "Phys"  "usb-*/input0"
        Option          "Device" "/dev/input/event4"
        Option          "CorePointer"
        Option          "Name"  "Logitech USB Receiver"
EndSection

```

Also add the Identifier name that you choose,  on the Section "ServerLayout" (around the bottom of the file) like this:

```
Section "ServerLayout"
        ...
	Inputdevice	"Configured Mouse"
        ...
EndSection

```

Keep in mind that you have to change the Phys and Device entries to the ones that you see when you type the command: 
```
cat /proc/bus/input/devices
```

**Now to reconfigure the resolution buttons (+, -):**
I encountered [**_this guide_**]("http://wiki.archlinux.org/index.php/Get_All_Mouse_Buttons_Working") which at the bottom suggest that by using the tool g5hack you can reconfigure those buttons.
Although I compiled and run the tool I didn't manage to stop those button from changing the resolution.

Can someone test that utility for G3/G5 or G7 and share his experience?

---

### Post by kev82 on 2007-10-25
This guide got my mouse working, but the sidescroll isn't detected by xev or xbindkeys -k, and the xbindkeys is somehow off... It's like that right now:
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + c:100
```
Problem is that now my left key doesn't work, and when I thumb click it works as if I hit the left key...

So howto fix that? :)

---

### Post by xcafeus on 2007-10-26
can someone please provide a complete step by step guide for G7 under Gutsy? Id be gratefull.

---

### Post by blakecraw on 2007-10-26
> **kev82 said:**
> This guide got my mouse working, but the sidescroll isn't detected by xev or xbindkeys -k

I'm in the same boat as you. Sidescroll won't show up, except via ```
evtest /dev/input/event4
```
Where it is listed as HWheel (so something's going right?)

I had to use this xorg.conf section to get x to start:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "Protocol"      "auto"
        Option          "Dev Name"      "Logitech USB Receiver"
        Option          "Dev Phys"      "usb-0000:00:1d.1-1/input0"
        Option          "Device"        "/dev/input/mice"
        Option          "Buttons"       "8"     
        Option          "ZAxisMapping"  "4 5 6 7"
EndSection

```

EDIT: the back button works perfectly now, so I'm really happy so far.

---

### Post by kev82 on 2007-10-26
How did you fix the back button?

---

### Post by blakecraw on 2007-10-26
To get my back button working, I first disabled the xbindkeys that I had running:
```
ps aux |grep xbindkeys 
         xxxx  0.0  0.0   4484  1480 ?        S    18:35   0:00 xbindkeys
kill -9 xxxx
```

Then ran xbindkeys -k and pressed the back button in the little window it pops open, and copied that output (m:0x0 + b:8 in my case) to the .xbindkeysrc file, and made sure that its bind was alt+left. I believe the file provided in the original guide had it set to button 6, which was throwing me off since I set mine up differently and got different button numbers.

---

### Post by B00R4dL3y on 2007-10-27
I can use the below to get my G7 working, but sometimes when I reboot, the display isn't recognized properly and I get a really low resolution screen (xorg.conf.failsafe replaces my xorg.conf file).  I'm using Ubuntu 7.10 and this happened when I was using 7.04 (but there wasn't an xorg.conf.failsafe which meant X just didn't boot and I got an error message).

```
Section "InputDevice"
        Driver          "evdev"
        Identifier      "Configured Mouse"
        Option          "Dev Phys"  "usb-0000:00:1a.0-1/input0"
        Option          "Device" "/dev/input/event1"
        Option          "CorePointer"
        Option          "Name"  "Logitech USB Receiver"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5 6 7"
EndSection
```

---

### Post by NobodySpecial on 2007-10-27
Update:  I wrote this how-to, but since then I moved on to a Logitech MX Revolution mouse.  The latest method does not require evdev, and is MUCH easier and more feature rich: use [btnx]("http://www.ollisalonen.com/btnx/").

[Ubuntu how-to HERE]("http://ubuntuforums.org/showthread.php?t=455656")

It works great for my MX mouse.  I would encourage you to switch to that method.  The first person to get it to work with the G7, please post here so I can change the how-to above to refer people straight-away.

Before doing the btnx way, please remove the evdev protocol from xorg.conf and revert to the default protocol.

---

### Post by B00R4dL3y on 2007-10-28
I reverted my xorg.conf's "Configured Mouse" back to the original.  Installed btnx, but I can't get the side button on my mouse to work in Firefox for some reason.  I've assigned it to be KEY_LEFT and Modifier key 1 as KEY_LEFTALT.  This should be the equivalent of the 'Back' button, but it doesn't seem to work while in Firefox.

Seems to work while in any other program.  When I press the side-button, it behaves like pressing the middle-button where it lets you quick scrolling with moving mouse.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"Buttons"	"8"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

I added in the 'Option		"Buttons"	"8"' line to see if it made any difference.


edit: I changed "Protocol" to "auto" and it fixed my problem.  Things are working great now!

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"auto"
	Option		"Buttons"	"8"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"no"
EndSection 
```

---

### Post by mirwin77 on 2007-10-30
Does anyone else have problems with their G7 mouse battery running out really quickly?  The mouse seems to work OK (brand new mouse, just installed btnx), but I'm having to switch fully charged batteries every day.  It's strange, the monitor will go to screensaver after the designated time but will not go on standby like it used to before I started using the G7.  I left my box on over night last night and this morning still no standby and the mouse battery is drained.  This has been happening for the last few days.  Hmmm, maybe I need to switch protocol to "auto" in my xorg configuration?  Any ideas?

---

### Post by NobodySpecial on 2007-10-30
mirwin77 - I didn't have problems with the battery running dead, but some other problems with one that recurred again when Logitech sent me a replacement.

I've switched over to the MX Revolution and love it.

---

### Post by mirwin77 on 2007-10-31
I did some testing last night and, as I suspected, the monitor standby mode is what was causing the mouse battery to run out.  Every time the monitor attempts to go into standby mode, the mouse turns on.  This triggers the monitor to wake up (out of standby mode) until the designated time of inactivity, and then this cycle repeats.  I turned off monitor standby in the power management options last night and this morning my mouse had plenty of battery left.  If I don't want my mouse battery to drain, no monitor standby mode for me!  Hahaa.  If anyone knows how to fix this issue, please let me know.

Thanks NobodySpecial, I may switch to a nice corded mouse to avoid the standby issue I'm having or just not use standby at all and manually turn off my monitor by pressing the power button when not in use.

---

### Post by madestro on 2007-11-30
I'm sorry there might be something that I'm not doing right here because when I follow the tutorial here [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656) I don't get any errors or anything but nothing happens. I have followed the whole troubleshooting and the instructions but nothing. So, I decided to give this script a try and when I restart the X environment my graphics get all messed up and the system tells me that it can't find my correct display drivers and defaults me to low graphics mode. Now the only way I can get back to normal graphics is to disable and enable my restricted graphics driver. But when I do that the xorg.conf file returns to it's defaults INCLUDING the mouse section.
Will anyone be so kind as to help me out here because I've followed everything as it says here and I have looked everywhere and I now have a G7 that works like a cheap-*** 10 dollar mouse.
These are the things that make Ubuntu not accesible to the programing impaired such as myself.

---

