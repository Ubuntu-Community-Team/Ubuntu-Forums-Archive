---
title: "Please help me - my touch pad is not working."
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Miss_Muffin on 2008-07-24
I have a Dell Inspirion 6000, and for some reason, (it just started), the touch-pad mouse is doing the opposite from what I'm trying to do. 

Examples:
1) I can't scroll the pages (online).
2) I can't switch between Tabbed Pages (online).
3) Whatever I click on - it acts like I'm right-clicking on it.
4) Won't let me close programs.

I'm still new with technology, and please help.

---

### Post by northern lights on 2008-07-24
Run ```
sudo apt-get install gsynaptics
```reboot and check the touchpad - it should now be functional...

---

### Post by Miss_Muffin on 2008-07-24
I rebooted it many times. I'm still having the same problem.

---

### Post by northern lights on 2008-07-24
Is it doing _exactly_ the opposite?

Or is it just screwing up?

Do you have another OS and can thus verify it's not a physical problem?

---

### Post by Miss_Muffin on 2008-07-24
It keeps acting like I'm right clicking on things, and it's still not letting me click on anything properly.

I recently formatted my laptop and had to re-install the audio, video and network cards/drivers.

---

### Post by northern lights on 2008-07-24
I dunno where my thoughts were half an hour ago. "gsynaptics" might be useful later, it's the touchpad configuration tool, but _not_ the driver...
#-o

They might depend on each other and the actual driver be already installed (which would suck, as it's still broken), but since it doesn't work, let's hope they dont.

Run
```
sudo apt-get install xserver-xorg-input-synaptics
```

Try. If fails, reboot (once does it), try again.

Please post the output of ```
aptitude search synap
``` in case it still doesn't work for verification of proper installation.

If it does, feel free to use gsynaptics to tweak...

---

### Post by gunashekar on 2008-07-24
> **northern lights said:**
> Run ```
sudo apt-get install gsynaptics
```reboot and check the touchpad - it should now be functional...

> **Miss_Muffin said:**
> I rebooted it many times. I'm still having the same problem.

The suggestion by northern lights was to ;
1. Press Alt+F2 (keys marked Alt and F2 together) [Alternatively you can click on the top panel menu in the following order (Applications>Accessories>Terminal]
2. This will pop up a terminal window
3. In the window copy and paste the command ```
sudo apt-get install xserver-xorg-input-synaptics
```
4. If you are prompted for a password, enter your login password and press enter.. the window will display the installation of some new software 
5. Reboot 
6. do post here if it works or not

---

### Post by Miss_Muffin on 2008-07-24
I'm not sure where to type the codes in. I don't see a Terminal. I use a Microsoft XP.

---

### Post by gunashekar on 2008-07-24
> **Miss_Muffin said:**
> I'm not sure where to type the codes in. I don't see a Terminal. I use a Microsoft XP.

LOL:lolflag:. We were assuming that you are asking for help on a linux installation.(Ubuntu / Linux is a different operating system than Microsoft XP and we in this forum believe it is free and trouble free)  

On Microsoft XP, I think you have to find the driver files for your computer, that is usually provided by the manufacturer or on the manufacturers website.


What a Comedy! This was perhaps my first attempt at teaching a beginner on how to use the terminal, and it so happens that the person is asking for support on Windows and not on Ubuntu!

---

### Post by northern lights on 2008-07-24
> **Miss_Muffin said:**
> I'm not sure where to type the codes in. I don't see a Terminal. I use a Microsoft XP.

Are you for real?
:roll:

---

### Post by Miss_Muffin on 2008-07-24
Well, I'm sorry. I'm not familiar with technology.

*blush* 

I'll leave then. -_-

---

### Post by gunashekar on 2008-07-24
> **Miss_Muffin said:**
> Well, I'm sorry. I'm not familiar with technology.

*blush* 

I'll leave then. -_-

you are welcome to stay. Someone might be more familiar to solve your XP / hardware problem.

---

### Post by northern lights on 2008-07-24
> **Miss_Muffin said:**
> I'll leave then. -_-It's not like you're not welcome to use these forums as you please. In fact, please do, as that might convince you to give up Windows at some point.

However, I don't quite get how you ended up at an Ubuntu forum when you're running a Windows machine?

In case you might not have figured: Ubuntu is a distribution of Linux, which itsself is an operating system (as is Windows). You've seen a Mac? It's not that either, but maybe you get an idea of how it's unlike Windows...

Did an accidental google result lead you here?

Anyhoo, a Synaptics Touchpad Driver for Windows can be found [here]("http://drivers.synaptics.com/Synaptics_Driver_v10_1_8_XP32.exe")

---

### Post by thomasjw on 2008-07-25
but wait, my touch pad isn't working either, and i'm actually running ubuntu!  

i tried that suggestion 'aptitude search synap' and all i'm able to get is the plain synaptics driver package, which heron i'm sure already has.  i don't see any gsynaptics, or qsynaptics or anything like that.  and i have no idea why synclient -l gives me the response "can't access shared memory!  SHMconfig disabled?" when I specifically put Option "SHMConfig" "on" in my xorg.conf trying to get the dumb touchpad to work.  This is my first day as a linux user so i obviously don't know much yet, but it seems like something is seriously rotten in denmark.

---

### Post by adult swim on 2008-07-25
this thread is awesome
thomas, try this
open up a terminal and type in 
```
sudo gedit /etc/X11/xorg.conf
```
paste this in 
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

and then at the end in the Section "ServerLayout"
add ```
InputDevice	"Synaptics Touchpad"
```
save the file and close it.  then log out and log back in.   your touchpad should work.

if this doesnt make sense, look at my xorg.conf file to see what i mean.

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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option 		"AccelMethod" 		"EXA"
	Option 		"MigrationHeuristic" 	"greedy"

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
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by thomasjw on 2008-07-25
adult swim - thanks for your reply, but in fact that's exactly what my xorg.conf looked like right out of the box when i first downloaded heron.   Same "InputDevice" section for the touchpad with all the same options, same ServerLayout section including "Synaptics touchpad" at the end.  And though that certainly SHOULD make my touchpad work, it absolutely doesn't at all - no movement, no buttons, nothing.

I've made a couple of edits in xorg.conf following various forum suggestions and howtos, including adding Option "SHMConfig" "on" to the touchpad's InputDevice section as suggested here: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) but it doesn't give me the expected results.  synclient thinks i've got SHMConfig disabled, and this alleged gui-touchpad configuration utility called gsynaptics is nowhere I'm able to find.  (not that it would work even if i could get it, since apparently the driver itself isn't working.)  maybe if i knew more i would have some idea what might be happening, but at the moment i'm like an amish farmer trying to fix the hyperdrive on the millennium falcon.  

if you do a forum search on winbook a710 touchpad, you'll find there's another poor soul with my exact same hardware having my exact same problem.  also, the first linux distro i tried to install was Debian etch, and I couldn't get my touchpad to work there either, which was part of the reason i decided i needed more user-friendliness and switched to Ubuntu.  

back in the archives i found some posts about non-working synaptics touchpads on HP500 laptops, a problem that was only solved by someone rebuilding the kernel (please god no) which of course broke the wifi until someone else solved that problem too... yeah, i've been at this many hours already, wondering why i don't just go buy a usb mouse and forget about my touchpad working....

do i get forgiven for hijacking a thread if i actually made it *more* on topic?

---

### Post by northern lights on 2008-07-25
> **thomasjw said:**
> do i get forgiven for hijacking a thread if i actually made it *more* on topic?

Most certainly. Yet I ain't so sure whether you can/will be helped. Threads with a multitude of replies are less likely to be read by someone other than those involved already. And even if, it's still not certain he or she is gonna read your post somewhere in the middle and reply.
That being said, I suggest you still open a new thread on your problem and give detailed info in the very first post.

If the package *xserver-xorg-input-synaptics* is installed and your *xorg.conf* looks as it should, I personally at least am at the end of my wits...

---

### Post by thomasjw on 2008-07-25
> **northern lights said:**
> Most certainly. Yet I ain't so sure whether you can/will be helped. Threads with a multitude of replies are less likely to be read by someone other than those involved already.

Even if people find out there is/was a WOMAN in this thread?  ;)

Yeah, I would have made my own thread, but the other guy who's having my same problem with my same hardware started his thread on the subject only last week.  I didn't want to be redundant so I just posted in his thread and a couple other places where people were discussing how to make a touchpad work.    

I did some more googling and found this [http://www.linuxquestions.org/questions/showthread.php?p=3164577#post3164577](http://www.linuxquestions.org/questions/showthread.php?p=3164577#post3164577) additional batch of things to try changing in my xorg.conf.  If the problem is like the HP500 bug these won't work, but I figure I'll try them just in case.

---

