---
title: "Need to re-create file..."
date: 2008-01-09
forum: Packaging and Compiling Programs
---

### Post by buccaneere on 2008-01-09
I edited [mangled] my /etc/X11/xorg.conf file. I only changed some touchpad values, but that wasn't a good thing:(

After the grub loader begins to load Ubuntu, the load stops, and I managed to get to a command line (not the regular terminal). I've even gotten logged as root-user.

How do I re-create the original file?

Thanks.....

---

### Post by stroyan on 2008-01-09
You can repeat the generation of xorg.conf by running```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by buccaneere on 2008-01-09
I got booted up with a live CD.

Now what do I do?

Thanks...

---

### Post by buccaneere on 2008-01-09
> **stroyan said:**
> You can repeat the generation of xorg.conf by running```
sudo dpkg-reconfigure xserver-xorg
```

Hi stroyan...

I see your post after I'm booted from a live cd, and I'm on on another machine too.

Do I key in your code from the 'failed-boot' command line? Or key it in from the Livecd boot terminal (as root)?

---

### Post by zero-9376 on 2008-01-09
what application did you use to edit the file. if you used gedit (ubuntu default text editor) there should be a file xorg.conf~ which i believe is the original unedited version if its there you can rename it back to xorg.conf and reboot.

if your running from the livecd you will need to access the real partition, it should be in places>computer probably called disk then browse to etc/X11/ and you many need to view hidden files (press ctrl-H)

---

### Post by buccaneere on 2008-01-09
> **zero-9376 said:**
> what application did you use to edit the file. if you used gedit (ubuntu default text editor) there should be a file xorg.conf~ which i believe is the original unedited version if its there you can rename it back to xorg.conf and reboot.

if your running from the livecd you will need to access the real partition, it should be in places>computer probably called disk then browse to etc/X11/ and you many need to view hidden files (press ctrl-H)

Hi zero...

I edited it with gedit.

While on Live cd, I entered
[HTML]exec sudo gedit /media/disk/etc/X11/xorg.conf
[/HTML]
I saved pulled the disk, and X-server failed to start.

I have no clue, but all I did before was edit that file. Once edited back, it should have been all hunky-dory. Right?

---

### Post by buccaneere on 2008-01-09
> **stroyan said:**
> You can repeat the generation of xorg.conf by running```
sudo dpkg-reconfigure xserver-xorg
```

I went through x-server re-config once, but must not have gotten values correct. Re-boot failed to start server.

Where do I get correct values?

Is it easier to re-configure from live boot?

Thanks

---

### Post by zxscooby on 2008-01-09
type startx at the command prompt and 
if x fails to start it should return some type of error message
indicating what line of the file is not kosher
type sudo nano /etc/X11/xorg.conf
to edit the file.
 typing man xorg.conf  will tell you more about it

---

### Post by buccaneere on 2008-01-09
Thanks scoob...

Got the file up to edit (the error was 'no screen found').

I have no clue what to change in this file...

---

### Post by zero-9376 on 2008-01-09
from the livecd when you look in /media/disk/etc/X11/ is there a file called xorg.conf~ (with the tilda). If there is that should be your original although now that you have edited by hand again it is probably not the original.
If everthing is working in the livecd just copy the xorg.conf from that into the directory above and reboot

---

### Post by buccaneere on 2008-01-09
> **zero-9376 said:**
> from the livecd when you look in /media/disk/etc/X11/ is there a file called xorg.conf~ (with the tilda). If there is that should be your original although now that you have edited by hand again it is probably not the original.
If everthing is working in the livecd just copy the xorg.conf from that into the directory above and reboot

Just tried that exact procedure zero.

No joy.

open xorg.conf,/ select all,/ copy,/ exec sudo gedit /media/disk/etc/X11/xorg.conf , select all, delete, paste, save exit re-boot.

NO X-SERVER.

I have NO clue...:confused::confused::confused:


EDIT: I did not unmount volume. This is the problem???

re-EDIT: Nope - not the problem. Still clueless after another attempt.

I will install from a different Live CD, transfer settings from new to old, and have two bootable installs. I hope. Just wish I knew what was wrong/how to fix............

---

### Post by zxscooby on 2008-01-09
post your xorg.conf

---

### Post by ayenack on 2008-01-09
Make sure to remove any LiveCD.
As mentioned earlier. Reboot your computer and let it fail to the command line. After this type this at command promt.

**sudo dpkg-reconfigure -phigh xserver-xorg**

Select **vesa** and a safe resolution for your monitor and graphics card. Normally 1024x768. That should be it can't quite remember been a long time since I've done this. When your done reboot you should have a GUI again.

After that make a backup of your xorg.conf so you can always recover it in times of need. Like this.

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup**

To restore your xorg.conf in times of need do this.

**sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf**

Be sure to use capitol X in all instances of "X11".

Good luck.

---

### Post by buccaneere on 2008-01-10
Thanks for the help.

I tried everything. Even a new install on the same disk, new partition, copied entire folders to the original partition, and attempted to re-boot from the original partition. It did not take. I still have no clue.

All I did was edit the original xorg.conf, from this:

[HTML]Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"
EndSection[/HTML]

to this:

[HTML]Section "InputDevice"
	Identifier	"Synaptics"
	Driver	"synaptics"
	Option	"Protocol" "event"
	Option	"Device" "/dev/input/event1"
	Option	"LeftEdge" "1900"
	Option	"RightEdge" "5400"
	Option	"TopEdge" "1900"
	Option	"BottomEdge" "4000"
	Option	"FingerLow" "25"
	Option	"FingerHigh" "30"
	Option	"MaxTapTime" "180"
	Option	"MaxTapMove" "220"
	Option	"VertScrollDelta" "100"
	Option	"MinSpeed" "0.02"
	Option	"MaxSpeed" "0.10"
	Option	"AccelFactor" "0.0010"
	Option	"SHMConfig" "on"
EndSection[/HTML]

Mind you, I did do it blindly, but I figured at worst, I'd have buttons with no touchpad.

Any ideas? I put in a spare HDD, and took the other one out, and still have it with the old jammed-up install, and the new install beside it...

---

### Post by ayenack on 2008-01-10
You know there are a few touchpad editors in the repo's. One that jumps to mind is gsynaptics that edits X server it also has a gui front end.

BTW. Shouldn't that be **"Protocol" "event1"** and not **"event"** or vice-versa. Maybe **"Protocol" "auto-event"**?

Or you should just be able to edit the file so it's the same as the old one.

---

### Post by buccaneere on 2008-01-10
> **ayenack said:**
> You know there are a few touchpad editors in the repo's. One that jumps to mind is gsynaptics that edits X server it also has a gui front end.

BTW. Shouldn't that be **"Protocol" "event1"** and not **"event"** or vice-versa. Maybe **"Protocol" "auto-event"**?

Or you should just be able to edit the file so it's the same as the old one.

Hiaye!

I think the .conf that I blindly copied/pasted into mine was from a file configured with gsynaptics...

Don't know the answer to the 'protocol' question. That's how I copied it:confused:

---

### Post by ayenack on 2008-01-12
Hello buc.

> **buccaneere said:**
> Hiaye!

I think the .conf that I blindly copied/pasted into mine was from a file configured with gsynaptics...

LOL. Well that puts that one to rest.

> **buccaneere said:**
> Don't know the answer to the 'protocol' question. That's how I copied it:confused:

Not sure myself just thinking allowed. Well you've got a working desktop again with the new install so a lesson learned for the future I suppose.

---

