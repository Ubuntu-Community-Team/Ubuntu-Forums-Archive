---
title: "screen resolution problem"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by x88a on 2008-06-26
The old thread seems dead with no more replies, so i think i will create a new one.
here is the old one
[http://ubuntuforums.org/showthread.php?t=839678](http://ubuntuforums.org/showthread.php?t=839678)

i am usnig a laptop and i cannot make my screen resolution bigger.
my max screen resolution is 1024 x 768

Here are some information:-
i have ATI accelerated graphics driver and it is enabled.
i also have xorg-driver-fglrx, but not xorg-driver-fglrx-dev.

this is my "sudo gedit /etc/X11/xorg.conf" output

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

pls help
tq very much

---

### Post by Canis familiaris on 2008-06-26
Can you change resolution using the Catalyst Control Center
(in terminal: type amdcccle)

---

### Post by cazmatazzz on 2008-06-26
hi i have the same problem, started a thread about it a while ago, even though i still havent figured it out and none of the offered solutions have worked for me, maybe some of the solutions will work for you... good luck! ([http://ubuntuforums.org/showthread.php?t=834528](http://ubuntuforums.org/showthread.php?t=834528))

---

### Post by x88a on 2008-06-27
> **Anurag_panda said:**
> Can you change resolution using the Catalyst Control Center
(in terminal: type amdcccle)

i got a new screen.
looks cool
but my max is still 1024 x 768
any more ideas??

tqtqtq

---

### Post by x88a on 2008-06-28
hello
anyone else can help me?
tq

---

### Post by iaculallad on 2008-06-28
Lines of texts below is the edited version of your /etc/X11/xorg.conf file you posted above. Try to copy and paste.

Create a backup of your original file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

Open your original xorg.conf file for editing:

```
gksu gedit /etc/X11/xorg.conf
```

Select all (Ctrl+A) the contents of your original xorg.conf file and delete it, copy the lines of texts below and paste it to your now empty xorg.conf file. Save and Close.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync 30-110
        VertRefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth 24
        SubSection "Display"
        Depth 24
        Modes "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Logout of your current account then log back in.

---

### Post by Methuselah on 2008-06-28
I recommended a solution to someone in the thread below since I really don't like adding certain information to xorg.conf by hand.

It works for me and apparently worked for him.
[Not quite sure from the response whether he followed the steps or fixed it some other way]
You can try it if you wish.

[http://ubuntuforums.org/showthread.php?p=5264032&posted=1#post5264032](http://ubuntuforums.org/showthread.php?p=5264032&posted=1#post5264032)

---

### Post by x88a on 2008-06-28
> Create a backup of your original file:

what do u mean by this?

do you mean i make a copy and save my original xorg.conf somewhere before i make changes to it?

tq

---

### Post by iaculallad on 2008-06-28
> **x88a said:**
> what do u mean by this?

do you mean i save my original xorg.conf somewhere before i make changes to it?

tq

What that means is:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Just to be sure that when you mess up your xorg.conf file, there will always be an available backup copy.

EDIT: That allows you to create xorg.conf.backup file in your /etc/X11 directory.

---

### Post by Methuselah on 2008-06-28
He means do something like:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig

```

That way you have a copy of your current config in case X really hates the edited one.

---

### Post by x88a on 2008-06-28
> **iaculallad said:**
> What that means is:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Just to be sure that when you mess up your xorg.conf file, there will always be an available backup copy.

EDIT: That allows you to create xorg.conf.backup file in your /etc/X11 directory.

ok, i have done this, but it still doesnt work. still a small resolution.
what is wrong?

---

