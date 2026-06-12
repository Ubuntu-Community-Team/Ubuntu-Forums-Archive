---
title: "standard ps2 mouse doesn't work."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by lone13angel on 2008-05-31
ok. hopefully this is a VERY simple problem, with an equally simple solution. I'm COPLETELY new to this, so I don't even know where to start on solving this. ever since the live cd, my standard ps2 mouse will not work.
ITS NOT USB.
ITS NOT CORDLESS.
its a standard 3 button mouse with scroll wheel that plugs into the back of my computer next to my keyboard.
its a pentium 4 1.6 ghz, nothing fancy about it.

My mouse simply doesn't respond. I don't know where to start looking to see where I can configure this, or change drivers (even if i were to download a driver, most of the driver downloads i've encountered in the past are usually .exe files that are designed for auto installing into a windows format....)

point is... how do i fix this? where do i start? and lets find some answers for everyone else out there who's looking. I kinda figure this to be on the lines of a fatal flaw.... its all base, standard equipment i've got hooked up here. why isn't it recognized or working?

---

### Post by damis648 on 2008-05-31
Did you restart after plugging it in?

---

### Post by shifty_powers on 2008-05-31
well, this will have nothing to do with the livecd ;)

might sound stupid, but have you tried unplugging it and plugging it back in?

---

### Post by sayakb on 2008-05-31
Which version of Ubuntu are you using? This problem was prominent for 7.04 Feisty Fawn.

---

### Post by lone13angel on 2008-05-31
several times.
during the livecd, after initial installation, after upgrades....
this is a problem that's been going on for about a week now.
and, i've used this same mouse in windows 3.x, win 95, win 98, windows xp (base upgrade, service pack 1, 2), as well as in many dos applications.
it works just fine when I install ANY windows o/s, as its a very simple mouse, and very standard.

however, ubuntu does not seem to.... either recognize it, or... something else is going on. simply put (i'm currently resorting to mousekeys, but...lol... yeah. that's a pain in the *** and no good for warcraft or anything....)

when i boot up, the pointers in the middle of the screen, mouse is sitting there, plugged in like it always is, just like whenever I resort back to Microsoft Windows, however.... there's no response. nothing. at all.

....


please try to understand, I just think there's something going on here that's kind of.... well... ridiculous. I see no reason why it shouldn't work. 
(and, I'm mostly testing this system out so I can get my friends away from windows and provide them with a stable o/s on their systems that...well... works. so far, I'm seriously having my doubts, because I've helped build thier systems to rougly the same standard.)

in short, what else could the problem be, barring completely retarded answers like "is it plugged in?" "did you reset your computer?" "is your computer plugged in", "are you sitting in front of your computer"...

seriously. this should be easy troubleshooting.
if this was a windows system, i'd have it solved in minutes.
however.... I don't even know how ubuntu is built, or where the mouse drivers are located, how to configure hardware, etc, etc, etc...anything with ubuntu.
I've never seen this set up before, so bear with me. its a whole new vocabulary and structure i've been trying to learn since the beginning of the week... and after spending 10 years studying windows, this is very discouraging.

so, where else can i look for help, or try solving this? what step would be next into troubleshooting a solution to this problem?

---

### Post by sayakb on 2008-05-31
Which version of Ubuntu is it? We understand the frustration but you need to provide us information..

---

### Post by lone13angel on 2008-05-31
8.04, the latest release, including the recent auto updates.

---

### Post by sayakb on 2008-05-31
Keeping the mouse plugged in, can you provide the output of these commands?
```
ls /dev/input
cat /etc/X11/xorg.conf
```

Note: X11 has a capital X.

---

### Post by lone13angel on 2008-05-31
btw. its also a completely clean install. wiped and formatted the harddrive, boot up, everything else seems to work just fine. except for this annoying mouse problem.

...and I haven't even tried to install other programs yet ...don't think I'll need too, I am VERY impressed with the base of this installation. however, the lack of a mouse is the biggest drawback, and its debilitating to see what the full extent of what this o/s can do.... so far... its potentially impressive. potentially.

however, if this is a problem with something in the .iso download for installation, it'd be good to find a way to fix it for future installations so...well... guys like me don't end up banging their head against a wall trying to figure out what's going on.

now, as I had asked before, where or how do i start looking to see how / if my mouse is set up in ubuntu? its plugged in, ready to go, ----should have been autodetected and working---- but isn't. (not like a usb, which would need further work, right?)

somewhere, somehow, there's got to be a way to take a look to see how/if/where my mouse is configured.... something like in windows with the .ini or .sys files for configuring my mouse and where the drivers are located.... it'd be a start.

where/how do i find these or look for these?

---

### Post by lone13angel on 2008-05-31
by-path event 0 event 1 event 2 event 3 event 4 mice mouse 0

---

### Post by sayakb on 2008-05-31
Copy the output of the command
```
cat /etc/X11/xorg.conf
```
And post it here..

---

### Post by lone13angel on 2008-05-31
Section "Input Device"
        Identifier        "configured mouse"
        driver            "mouse"
        option            "CorePointer"
        option            "device"            "/dev/input/mice"
        option            "protocol"          "ImPS/2"
        option            "ZAxisMapping"      "4 5"
        option            "Emulate3buttons"   "true"
EndSection



I beleive that would be the pertinant section we want to look at, after accessing "Terminal" and entering in the commands you specified in Terminal.
(i'm wording it this way so others reading this will be able to follow.)

---

### Post by pbpersson on 2008-05-31
Background information that might be interesting:

Whereas the Microsoft Windows system is very monolithic, Linux is very modular.  When you start up Windows.....it is graphical by default - that is Windows.

Linux on the other hand is very modular - the kernel is the core....then you have a graphical environment that runs on top of that.....then you have a desktop window manager such as KDE or Gnome.....and the programs run on top of that.

In the Linux world, the module that paints the GUI environment is XServer - it knows what sort of mouse you have, what sort of graphics card, monitor, etc.  Your /etc/X11/xorg.conf file contains all the configuration information that XServer uses to communicate with your various system devices.

I didn't know if anyone cared.....I just felt like typing :)

---

### Post by pbpersson on 2008-05-31
For the sake of comparison, I have the same type of mouse and here is how the same section appears on my Hardy Heron machine:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"explorerps/2"
	Option		"ZAxisMapping"	"4 5"
EndSection
```

This is not your main problem, but you do NOT want to emulate a three-button mouse!  That will cause strange things to happen.

---

### Post by lone13angel on 2008-05-31
so, here's the big question.
should I remove that line about 3 button emulation from the configuration, better question. how would I remove that line or edit it?
...if that would work.

also, apparently it seems that its picked up on what my mouse is... but for some reason its not responding (because it seems to be included in the configuration.....)

...

yeeeah. lol!!! uhm... so, what would the next step to this be?

---

### Post by pbpersson on 2008-05-31
This is what I would do if I were you.  There is a way to reconfigure XServer by telling it to re-detect what you have and then it can ask you questions.....but if you want to try the following method, go to the terminal prompt and type the following:

```
sudo gedit /etc/X11/xorg.conf
```

Then make your section look EXACTLY like mine and remember that everything is case sensitive in Linux.  Then save the file and reboot.  See if that does the trick.  If not, you will need to totally reconfigure XServer which is not a big deal but should not be required.

---

### Post by lone13angel on 2008-05-31
okay. I've tried removing the Option "Emulate3button" "true"....
didn't appear to work after restarting.
I tried even changing "Imps/2" to what you had.
nothing.
so, i've changed everything back.

something else is going on here... is there any listing for all available context on "option" with triggers? see if i can read through something comprehensive to see what all available changes can be made to those lines to see if it works?

---

### Post by AndrewTheArt on 2008-05-31
Try this - 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
```

This is a very strange hardware incompatibility. If reconfiguring the X11 server doesen't work, you're mouse might indeed have special drivers that do not have a Linux equivalent. This is possible, but just very unlikely with what appears to be a generic PS2 mouse.

---

### Post by lone13angel on 2008-05-31
okay. I tried your commands, went through the configuration, and have tried and tested both the true and false for the emulation of a 3 button mouse.
... still no response from the mouse in any of this. so, I'm going to guess that the problem could lie elsewhere.

now, what would there be that dictates input to or from the configuration in this.... 
this is getting kind of interesting trying to figure out why this is doing this...and not working.

---

### Post by SunnyRabbiera on 2008-05-31
what is the make and model of this mouse?
Any branding or is it just some generic mouse?
Its very odd that this is not working, as mice are usually detected right away with ubuntu... very strange.

---

### Post by pbpersson on 2008-05-31
I really thought the problem was because you had Imps/2 instead of what I have.

The "emulate three button mouse" means that you are telling Linux to click the middle button "your mouse wheel" when you click buttons one and two on the mouse.  Having that set to "true" means that when you attempt to use the mouse wheel, weird things happen but the mouse still functions.

I am also at a loss to understand what is happening with your machine. :(

---

### Post by pbpersson on 2008-05-31
Oh and by the way, if you want to learn about the wonderful world of xorg.conf and all the options that can go in that file, you can type the following at a terminal prompt:

```
man xorg.conf > xorginfo.txt
gedit xorginfo.txt
```

To read other posts from other people with your same problem, you might Google something like:

Ubuntu "dead mouse" xorg.conf

---

### Post by pbpersson on 2008-05-31
Here is yet another thought......

Thinking that it might be a problem in how the kernel is talking to your motherboard, you might get daring and using the mobo model Google one of the following:

Ubuntu "PCChips A13G" "dead mouse"

or

Linux "PCChips A13G" "dead mouse"

and see what you get.  I used my own motherboard as an example.  I am CERTAIN you are not the first to travel this path.

---

### Post by pbpersson on 2008-05-31
Last but not least.....if ALL ELSE fails....there is [another option]("http://www.amazon.com/USB-To-PS-2-Adapter/dp/B000086TKU").....

I like to think there is always a way out of every mess but I only mention this as a last resort.

---

### Post by tigertom on 2008-06-17
I have a very similar problem.  Are you guys still there?  Did anyone solve this problem, or find a solution somewhere else?

My machine worked well with Ubuntu version 6.  The update to version 8 (Hardy Heron) was very problematic, and in the end I did my best to wipe the disk and do a clean install.  Once the install was done, everything works fine except the PS2 mouse.  I'm working around the problem by using a USB mouse, which works fine. If anyone has the interest, here are some of the answers asked for above:

 - System is a clean install of Ubuntu 8.04, Hardy Heron

 - Computer is a "Mega" PC with an Intel Pentium 4 at 2.4 GHz and reports 979 MiB of RAM

 - I've tried two mice: One is a Dell mouse with two buttons and a scrool wheel / third button, and has a Logitech chip inside The other is a genuine old Microsoft mouse with just two buttons.

Lone13Angel, I'm afraid I'm not as clever as you at running the system without a mouse.  Can you give me some tips?

The best reply I can get to "ls /dev/input" is:
by-path event 0 event 1 event 2 event 3 event 4 mice mouse 0
 
The best reply I get to "cat /etc/X11/xorg.conf" was:
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
	Option		"XkbLayout"	"ie"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
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
EndSection

Any suggestions?  Thanks in advance

---

### Post by mperezra on 2008-06-22
I have the same issue here, any solutions?:(

---

### Post by silkstone on 2008-06-22
On Feisty I used a wired USB mouse and USB keyboard but ran them through USB>PS2 adapters to free up the USB ports. Everything worked fine.

I then did a fresh install of Hardy, and all seemed well to start with, but then the keyboard suddenly froze for no apparent reason. This happened several times. So I removed the adapters and plugged both mouse and keyboard into the USB ports, and everything was fine after that.

I know this isn't quite the same issue - keyboard instead of mouse - but I wonder if there is a bug with Hardy and PS2 connections.

Anyway, since mice are cheap, the solution may be to buy a USB mouse. I've now switched to a wireless mouse and keyboard which also works well.

---

