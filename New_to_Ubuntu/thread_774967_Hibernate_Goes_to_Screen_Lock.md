---
title: "Hibernate Goes to Screen Lock"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by dublued on 2008-04-29
First time ubuntu user.  Using Hardy Heron 8.04 with all the latest updates.

Everytime i try to hibernate the system, it goes to the screen lock login.

When i first installed it on my laptop, i didn't specifiy swap.  I did that recenty using the following guide:

[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0)

Now that I have added 1 GB of swap, it still does the same thing.  The only difference is that before it goes to the screen lock login, it displays [1604.5944]drm_sysfs_suspend.  The numbers in the brackets are different everytime.

I've only been exposed to linux ubuntu for a few days so if you do provide any assistance, please try to be as clear as possible :D!

I have had the same problem with my cousin's dell inspiron 1420

System Specs:

Gateway C140-X Tablet Laptop
Intel Core2Duo
1 GB RAM
Dual Boot with win xp pro

Thanks!

---

### Post by RealPSL on 2008-04-29
I used to have a similar problem with my white box machine at home. It turned out that my swap space needed to be a little larger than my memory size for the hibernation to work. Once I changed that it has worked ever since.

---

### Post by CAsurfer on 2008-04-29
If you don't want Ubuntu to prompt you for your password whenever you suspend, run the command "gconf-editor". Go to apps -> gnome-power-manager -> lock and uncheck the suspend and or hibernate boxes. 

BTW, you may want to look around through gconf-editor some, as lots of configuration options are hidden in there.

FYI, whether you get the "Screen Lock" login screen should have nothing to do with swap space allocation.

---

### Post by dublued on 2008-04-30
thanks for the tips...

my swap size is 1 gig... same as my ram... does it have to be more than that??  i guess now i have to figure out how to increase the swap file size... yay!  more searching! :):)

yea i did go into the config editor and got rid of the login screen for screen lock.

but now when i hibernate it just comes back into the OS.

CASurfer:
i see that you are also running the same tablet as i am.  i haven't had the chance to look into getting the pen working.

have you had any luck?  any tips before i dive into that?

---

### Post by natrixgli on 2008-04-30
> **CAsurfer said:**
> FYI, whether you get the "Screen Lock" login screen should have nothing to do with swap space allocation.


To avoid confusion, it's normal to be prompted for a password when resuming from suspend/hibernate. (which is what you can disable in gconf) I think the OP is suggesting that it never in fact hibernates/suspends, but just goes directly to the password prompt. (without passing go OR collecting $200.)

Cheerio,

-n8

---

### Post by dublued on 2008-04-30
yeap, that's exactly what i mean :)

thanks

---

### Post by CAsurfer on 2008-04-30
I did a quick search, and didn't come up with anything authoritative, but it looks like swap space is used to save system state when you hibernate (it seems like such a bad idea, though, I find it hard to believe). So to hibernate successfully, you have to have enough free swap space to save the contents of your RAM. I'm guessing it doesn't overwrite whatever may already be in swap when it hibernates, which would mean that for hibernation to be successful, swap must be bigger than the amount of RAM currently used plus the amount of swap space currently used. Some people recommend making swap 2 or 3 times as big as memory, and this seems reasonable.

Luckily, it's pretty easy to add more swap space. Boot from the LiveCD, start "Partition Editor" (aka gparted), shrink your main partition, and then grow your swap partition. Standard Caution: doing this may destroy the contents of your partitions if there is an error (though in practice this almost never happens, except in the Feisty version of gparted). If the partitioning process stops half way through, you will lose everything, so make sure the computer is plugged in to power and not on battery.

You should be able to get this working; suspend and hibernate work for me, using the fglrx driver, though sound sometimes needs to be restarted after suspend ([https://bugs.launchpad.net/ubuntu/+bug/198218](https://bugs.launchpad.net/ubuntu/+bug/198218), and see my attached bash script).

Enabling pen input is as easy as uncommenting three lines in xorg.conf. You will also need to add a line to the wacom InputDevice section to properly remap buttons for the C-140X. See the attached xorg.conf.

---

### Post by dublued on 2008-04-30
you're my hero!

i will try this stuff out tonight and post here what happens

---

### Post by dublued on 2008-05-01
i decided to do a clean install of ubuntu.  this time i made a swap partition instead of a swap file.  set it at 2GB (i have 1 gb ram) and now hibernate works!

now looking at your xorg.conf file.  mine looks nothing like it.  is it because i haven't installed fglrx.  is that for ati only?

---

### Post by CAsurfer on 2008-05-01
What video card do you have, or do you have integrated graphics? Do desktop effects work for you?

fglrx is ati only.

It's surprising that your xorg.conf would deviate significantly from mine, since I have a pretty vanilla install. Can you post your xorg.conf?

---

### Post by dublued on 2008-05-01
yes I have the integrated graphics and compiz works brilliantly.  running on 1280x768 resolution

here's my xorg.conf
```
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

### Post by CAsurfer on 2008-05-01
It looks like this isn't going to be as easy as I had hoped, and I'm not sure exactly what you should do, but here's an idea in 2 parts:

1) Your xorg.conf seems to be pretty similar to mine, but missing 3 InputDevice sections (the ones corresponding to the wacom pen input). It's also missing the 3 lines in ServerLayout corresponding to those sections. I'd trying adding those to see what happens.

2) It may be the case that even if your xorg.conf is configured properly, you will still need to install a wacom driver. The two wacom packages I have installed are "wacom-tools" and "xserver-xorg-input-wacom". I'd make sure you have both installed.

On another note: my Synaptics touchpad was poorly configured by default on my install (the scrollbar was far too wide). If that's the case for you, I can offer some tips.

---

### Post by dublued on 2008-05-01
Now that you mention it.  The scroll is indeed too far wide.

I'll go ahead and try adding the wacom packages and see if thoe 3 (or 6) lines show up in xorg.conf

and we'll go from there

---

### Post by dublued on 2008-05-02
So it's working now... the pen works including the right click button

i first installed the "wacom-tools" package.
then i tried to install the "xserver-xorg-input-wacom" package but it said it was already installed.  i went into synaptic package manager and it showed as installed

i then added the 3 input devices and then added the 3 lines in the serverlayout section

restarted with ctr+alt+bkspc and the pen was working great.

i do notice that you have a device called "Configured Mouse"  is that for fixing the wide scroll on the touch pad or is that some external mouse?

---

### Post by CAsurfer on 2008-05-02
"Configured Mouse" is presumably for an external mouse. 

To change scroll bar width, read this guide: [http://ubuntuforums.org/showthread.php?t=493758&highlight=scroll%20touchpad](http://ubuntuforums.org/showthread.php?t=493758&highlight=scroll%20touchpad)

I found that a good "RightEdge" width for my/our computer is "5900".

---

### Post by dublued on 2008-05-02
5900 works perfectly

all i had to do was:

> sudo apt-get install xserver-xorg-input-synaptics gsynaptics

and then 

> sudo gedit /etc/X11/xorg.conf

xorg already detected the synaptic touchpad so i didn't have to go thru all the mumbo jumbo
I just added the following option under the input device and it was good to go.

> Option          "RightEdge"     	"5900"

thanks for all the help.  now i just need to figure out if i can extend my display onto an external monitor and i'll be set

i am changing the tags and thread title so hopefully others will benefit

---

### Post by CAsurfer on 2008-05-04
Great!

BTW, you don't need to install "gsynaptics" - it's just a gnome-based graphical utility (thus the "g" in "gsynaptics"), which you didn't end up using.

Unfortunately, I've never hooked up an Ubuntu computer to an external monitor, so I probably won't be of much help to you there. However, I'm pretty sure that such display magic is usually handled by Resize and Rotate (RandR), so that may give you a place to start looking.

---

### Post by indiecast on 2008-05-18
first i'd just like to say that i've found this thread extremely informing!
thank you!

1.  my hibernate works fine but still shows that drm_sysfs_suspend message and right now im just assuming that that's telling me my system has actived its hibernation stuff and that it's going to hibernate.  stil...anyway i can make a silent hibernate like vista?

2.  to get my hibernate to work all i had to do was put resume=[swap partition] in a certain spot in the grub menu

...see...
[http://www.linuxquestions.org/questions/ubuntu-63/hibernate-ubuntu-355177/](http://www.linuxquestions.org/questions/ubuntu-63/hibernate-ubuntu-355177/)

3.  dublued said his graphics are integrated and he has effects?  from what i know that's impossible.  he must have some kind of gfx card in there.

4.  my synaptics touch pad works great but im gonna install those things so i get more config options (i love playing with configuration so thanks!)

5.  i'm really confused by my xorg.conf file.  i've done editing in here before on 6.10-7.10, but in 8.04 things are ALOT different.  The graphix card section isn't in the xorg.conf file and it appears as if the wacom drivers no longer come installed by default.  why is this?

---

### Post by dublued on 2008-05-19
by silent hibernate do you mean that the computer powers down and stores everything in your ram onto your hard drive?  if so, the steps i did hibernated my laptop that way.

also i don't know too much about what graphics cards work with effects and stuff.  but i did lspci and this is what it showed me for my graphics stuff...

```
 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

---

### Post by tamias on 2008-06-10
> **indiecast said:**
> 
1.  my hibernate works fine but still shows that drm_sysfs_suspend message and right now im just assuming that that's telling me my system has actived its hibernation stuff and that it's going to hibernate.  stil...anyway i can make a silent hibernate like vista?

This is actually just a bug in Ubuntu's kernel, on its way to being fixed. Have a look here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234239](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234239)

> 5.  i'm really confused by my xorg.conf file.  i've done editing in here before on 6.10-7.10, but in 8.04 things are ALOT different.  The graphix card section isn't in the xorg.conf file and it appears as if the wacom drivers no longer come installed by default.  why is this?

As far as I understand it, 8.04 is the beginning of "Failsafe X", whereby xorg.conf is being phased out. So I wouldn't worry about these changes -- yes, they confused me as well!

---

