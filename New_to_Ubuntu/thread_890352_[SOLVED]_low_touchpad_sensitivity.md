---
title: "[SOLVED] low touchpad sensitivity"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by macvr on 2008-08-15
hi, i'm dual booting with XP in my Acer 5672WLMi laptop
i have installed gsynaptics also[have set SHMconfig to "on"]

1-i find that the touchpad sensitivity is very low compared to Xp especially when using Tap for mouseclick setting[acceleration is fine]
i have set the the sensitivity to max, but several times i have to tap much harder than in i need to in XP[where the sensitivity setting is only at 70%]
my finger aches after a few hrs of browsing!

is there any way to increase this tap sensitivity?

2-can the area of the vertical scrolling border be reduced?[this option exists with synaptics software in XP]

3-what does the faster tapping option do[system>touchpad>tapping]?

4-click lock doesnt work properly

---

### Post by macvr on 2008-08-16
the tapping is so hard , which i'm not used to... 
i'm worried if i might wear out my touchpad by all this hard tapping

---

### Post by hovzio on 2008-08-16
hi, I am having the same problem. I'm using a toshiba a-200 and the touchpad is working so far, it just feels like I need to get a sludge hammer out to "click" on anything. Any ideas, thanks:)

---

### Post by macvr on 2008-08-16
bump?

---

### Post by macvr on 2008-08-18
second bump...

my fingers are actually paining using the touchpad!!!

---

### Post by SeanHodges on 2008-08-18
Ensure you report this problem, a guide is provided here:

[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

Sorry, I dont have much familiarity with gsynaptics, hopefully the devs on Launchpad will be able to help you get further...

---

### Post by macvr on 2008-08-18
> **SeanHodges said:**
> Ensure you report this problem, a guide is provided here:

[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

Sorry, I dont have much familiarity with gsynaptics, hopefully the devs on Launchpad will be able to help you get further...

finally,someone to the rescue

thank you, i'll report this problem

---

### Post by macvr on 2008-08-19
have filed a bug report at launch pad:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/259289]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/259289")

@hovzio> pls ***add*** your config files, as given in the link _SeanHodges_ has provided above ,to the bug report page in launchpad , so we could hope for a speedy resolution

anyone else having similar problems also add ur files to get his problem fixed

---

### Post by macvr on 2008-09-02
bump?

---

### Post by macvr on 2008-09-02
i'm not sure if my first post was clear...
i have gsynaptics installed, but my main problem is with, 

>click tapping & 

>click locking

---

### Post by macvr on 2008-09-03
ok.... maybe i made a mistake by posting this touchpad problem here in beginners section, 
got bits and  pieces of help in other threads in the Hardware&laptop section
it turns out that the gsynaptics doesnt work as expected in all systems

just put together the procedure in cause other new users need it...

 we have to use 
```
man synaptics
```
^^^this will give a list of all the available variables that can be set...
its a huge list with A LOT of ways to customize...:)

check the   /etc/X11/xorg.conf if SHMConfig is set to "on"
```
 synclient  -m  1
```
^^^this will give the touchpad parameters required to set accordingly in the xorg.conf

backup the xorg.conf 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

to edit the xorg.conf
```
 gksudo gedit /etc/X11/xorg.conf
```
 after editing, save...*** log out and relogin for the changes to take effect***

this is a painful process to get the settings right... u have to logout & relogin everytime u change a setting :(





in case of any problems, to restore ur old xorg.conf>
```
sudo cp /etc/X11/xorg.backup /etc/X11/xorg.conf
```


eg: [COLOR="Red"] changes which corrected my problems[/COLOR]

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	[COLOR="Red"]Option		"RightEdge"	"5400"
	Option		"BottomEdge"	"4500"
	Option		"LockedDrags"	"on"
	Option		"LockedDragTimeout"	"500"
	Option		"FingerHigh"	"21"
	Option		"MaxTapTime"	"500"[/COLOR]
	Option		"SHMConfig"	"on"
EndSection
```

 ... solves my prob.... :)

---

### Post by SeanHodges on 2008-09-04
Glad to hear you got it sorted macvr, sometimes the people on the forums simply don't have the answer you're looking for (or the ones who do never see it).

I suggest you post a link to this page in your Launchpad bug, so others can find it easily.

I myself have bookmarked your solution in case I ever need to use it :)

---

### Post by macvr on 2008-09-05
> **SeanHodges said:**
> 
I suggest you post a link to this page in your Launchpad bug, so others can find it easily.

have linked it in launchpad...

but i still think that gsynaptics is buggy since its not taking full control of the touchpad functions*[MaxTapTime and FingerHigh are options available in gsynaptics GUI but its changes dont really take good effect in my system]*

---

### Post by Elfy on 2008-09-05
I'm glad to see that you have got it sorted for you - perhaps you should post it as a bug on the project page, the bug page is here

[https://sourceforge.jp/tracker/?atid=6433&group_id=1720&func=browse](https://sourceforge.jp/tracker/?atid=6433&group_id=1720&func=browse)

---

### Post by macvr on 2008-09-05
> **forestpixie said:**
> I'm glad to see that you have got it sorted for you - perhaps you should post it as a bug on the project page, the bug page is here

[https://sourceforge.jp/tracker/?atid=6433&group_id=1720&func=browse](https://sourceforge.jp/tracker/?atid=6433&group_id=1720&func=browse)
submitted>

[https://sourceforge.jp/tracker/index.php?func=detail&aid=13462&group_id=1720&atid=6433]("https://sourceforge.jp/tracker/index.php?func=detail&aid=13462&group_id=1720&atid=6433")

but there are so many advanced members in the forums , who even though knowing that gsynaptics doesnt do a good job of controlling the touchpad,have not filed bugs?!?!?![especially hanging in the hardware&laptop section, *i know since they recommended the man synaptics!n its been discussed in other threads*], thats sad!

---

### Post by Elfy on 2008-09-05
manana - I guess, it might be that the project doesn't get much attention from the developer and they know something we don't...

---

### Post by macvr on 2008-09-05
> **forestpixie said:**
> manana - I guess, it might be that the project doesn't get much attention from the developer and they know something we don't...

??? are u referring to manana attitude or to some software called manana???

---

### Post by Elfy on 2008-09-05
attitude :D

---

### Post by macvr on 2008-09-05
well ^^^that could be it

, damn the spanish!!!:):) ;)

---

