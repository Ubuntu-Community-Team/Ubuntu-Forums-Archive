---
title: "HOWTO: Turn Touchpad On and Off On your Laptop"
date: 2006-03-11
forum: Outdated Tutorials &amp; Tips
---

### Post by noob_Lance on 2006-03-11
****NEW VERSION AT BOTTOM****

Ok For All you that have the problem of a touchpad where you have no options to turn them on and off, heres what i did to solve my problem and it works. but youll need to take a few steps to get it to work so i hope you dont mind lol.

**Step 1:**
Ok first off you need to edit your Xorg File and add the following line of code to it to allow you to turn your touchpad on and off.
```

#Before
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```

```

#After
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	**Option      	"SHMConfig" 		"on"**
EndSection

```
you need to create 2 bash scripts.. one to turn the touchpad on, and one to turn it on.. 

so this would be the start of it
**Step 2**
Name This File tpoff
```

#!/bin/bash
#

synclient touchpadoff=1 

```

And this file tpon
```

#!/bin/bash
#

synclient touchpadoff=0

```

These will be your on and off switches :)

**Step 3**
when you are done both, chmod both to 777 and move both to /usr/local/bin/
```

sudo chmod 777 tpon tpoff
sudo mv tpon /usr/local/bin/
sudo mv tpoff /usr/local/bin/

```

onces thats done.. you will need to edit your sudoers files to allow you to exe both scripts without a password. 

**Step 4**
so use the following command
```

sudo visudo

```

and add these 2 lines
```

{user}   ALL = NOPASSWD: /usr/local/bin/tpoff 
{user}   ALL = NOPASSWD: /usr/local/bin/tpon 

```
where {user} is your user name

then save. 

**Step 5**
Next install the following 2 programs

xbindkeys
```

sudo apt-get install xbindkeys

```

and xbindkeys-config, the GUI for xbindkeys
```

sudo apt-get install xbindkeys-config

```

once installed start both application
```

xbindkeys

```
and
```

xbindkeys-config

``` 

**Step 6**
then go ahead and edit your file to the shortcuts you want to exe the script with. then for the action, set it to /usr/local/bin/ (the name of the script)


The way i set mine up is as follows, under Edit:
Name: Touchpad Off
Key: Control + F5 | m:0x4 + c:71 
Action: /usr/local/bin/tpoff

Thats it for turning it off.

then at the bottom, hit New and enter the following
Name: Touchpad On
Key: Control + F6 | m:0x4 + c:72
Action: /usr/local/bin/tpon

then click apply & save & exit

Now that that is done we have to restart the xbindkeys.

```

xbindkeys

```

Now go try it out :D and have some fun.. your touchpad problems are now solved :D

If there are any suggestions or anything please feel free to post it. My next revision is to make it with jsut one key and one script. but since this is my first howto... go easy on me :D

For all those who are sick of the touchpad always messed up for work.. your welcome :D


~Lance

Ok Above Was The Previous Version. I want to point out that i did change the previous howto to include step numbers. those will be seen below :). 

Follow These Steps.. any wth a * refer to the ones above has they have not changed:

***Step 1**

**Step 2**
Download the file i have attached below and upack it to **/usr/local/bin/**
ones unzipped, you will have to chmod it to 777.
```

chmod 777 /usr/local/bin/touchpad.py

```

**Step 3**
Edit the sudoers file (like above).. but change the 2 lines you need to insert to jsut this line:
```

{user}     ALL = NOPASSWD: /usr/local/bin/touchpad.py

```

**Step 4**
refer to *Step 5 

**Step 5**
Now Here Is Where The Real Update Is. Instead of having to remember 2 key combos to turn it on and off... this script i made will use only one key combo and do both functions :D life jsut got easier.

The way i set mine up is as follows, under Edit:
Name: Touchpad Control
Key: Control + F5 | m:0x4 + c:71
Action: /usr/local/bin/touchpad.py

**Step 6**
Restart xbindkeys and your set to go :D ENJOY EVERYONE!

---

### Post by ranf on 2006-03-12
Into which section of the xorg.conf do I have to put:

SHMconfig "on"

---

### Post by noob_Lance on 2006-03-12
oh crap... i forgot all about that. you should put it as the last thing in your input device section for your touchpad. Ill have to go and edit that into the howto. thanks for the reminder..

---

### Post by cbudden on 2006-03-12
On my laptop, I just need to do Fn + F7.

---

### Post by noob_Lance on 2006-03-12
then your lucky and have the function built into your laptop.. this is for those who are as lucky >,<

---

### Post by Super King on 2006-03-13
noob_Lance, you rock, this works perfectly on my Thinkpad! I've seen probably a half-dozen threads on this forum where others were wanting this same thing, so I'm sure others will find this solution helpful as well. No more annoying touchyness while typing!

---

### Post by noob_Lance on 2006-03-13
Im glad to hear it Super King. Ill be sure to send you off a PM when i get the program to work that im working on. it makes it so only the ctrl+F5 (or whatever key combo you use) will turn it on and off :) get that working and it will all be good. Hell i was even thinkin to myself at work.. maybe create an all out program that will do all this.. in a simple deb (if i can learn how to make those too haha)

Anyways. Everyone... until i complete the program.. ENJOY!

---

### Post by noob_Lance on 2006-03-14
Everyone The Howto Has Been Updated!

---

### Post by dbunder on 2006-03-14
Sorry to resurrect an old topic, but this is related to synaptics and figured it'd be a good place to ask.  Is there a way to automatically run a script, or scripts, upon, or after X startup?  I'd like to run "syndaemon -d -i 2" after the xorg.conf is read and the SHMConfig is seen to be set to "on."  This will disable the touchpad whilst you are typing and won't enable it again until 2 seconds after your last keystroke, but will not work until it sees that SHMConfig is set to "on."

This'd be a question I could easily answer myself if it were years ago, but it's been at least 5 years since I've run linux, freebsd, or anything of the sort and the XOrg setup/config seems to be a lot different from good ole' XFree86.

Thanks much for any help.  Very new to Ubuntu, and linux in general has changed a lot since I last used it, so please excuse my ignorance. :mrgreen:

---

### Post by patrick.ubuntu on 2006-03-14
Hi,
So I have a Dell Lattitude D610 that has both a touchpad and an eraser point mouse.  Is there any way I can turn off the touchpad (which is driving me nuts) and keep the eraser point (trackpoint) on?
Any ideas would be greatly appreciated!
Cheers,
patrick

---

### Post by noob_Lance on 2006-03-14
dbunder- um... im not that advanced with any sort of programming to determine wether that can be done or not... well i know it can be done... i jsut dont have the skills to do it :p

patrick.ubuntu, um... i have never worked with a dell (im on a gateway) are there any differences in your xorg.conf file. post your entire conf file and lets see. thats all i can do for now.

---

### Post by m.musashi on 2006-03-14
Hey Lance,

Thanks for this. It's a cool little fix for an annoying problem.

However, I'm having a bit of problem getting it to work. I've gone through all the steps and from the xbindkeys-config window if I click the run action button it works fine - TP goes off and on. However, if I try and use the F5 key it's a no go. I even tried to reboot the computer but still no effect. Am I missing something?

---

### Post by patrick.ubuntu on 2006-03-14
Hi,
I think you might have hit on the answer!
Here's my file, including where I just tried to comment out the touchpad (which I hope will work.)  I'll restart and see if that's fixed it.
Cheers,
patrick

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

##This is me turning off the touchpad
##Section "InputDevice"
##	Identifier	"Synaptics Touchpad"
##	Driver		"synaptics"
##	Option		"SendCoreEvents"	"true"
##	Option		"Device"		"/dev/psaux"
##	Option		"Protocol"		"auto-dev"
##	Option		"HorizScrollDelta"	"0"
##EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M300 (M22)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by m.musashi on 2006-03-14
I think I might have solved my own problem. First, I have been using kde lately (trying to become more knowledgeable all around) and it seems that xbindkeys doesn't work in kde. At least I can't get this work. If I switch to gnome and run the xbindkeys command again it does start to work. However, after a reboot you have to run the command again. I solved that by adding it to startup programs in the system -> preferences -> sessions option.

dbunder - if you add the "syndaemon -d -i 2" command to the session options as well it does seem to activate it and then whenever you start to type the touchpad turns off. However, it seems to interfere with the xbindkeys as the F5 switch stopped working after I added the new command.

It seems you can have one or the other but not both - unless I'm doing something wrong which is very likely :).

---

### Post by m.musashi on 2006-03-14
Okay, I don't really know what I'm doing but I started to think that I want the F5 switch so that I can kill the touchpad anytime I like. But I also thought it would be nice to have the ability to just have it die while typing and then come back. However, I don't want that on all the time as it could be annoying when you are actually using the touchpad and the way I had it set up I lost the F5 switch.

So....

Taking a page from Lance's how to, I did a bash script (my first:)) that was basically a copy of Lance's with the "syndaemon -d -i 2" command. Saved it in the /usr/local/bin as touchpadtype.sh and then used xbindkeys to add F6 to run it.

Now when I boot up I can either use F5 to kill the touchpad if I'm using a usb mouse or use F6 to turn on the typing = temp kill touchpad feature. Of course, once on it is always on until you reboot. Perhaps I'll disect Lance's python script so that you can turn this off and on as well. However, what would be the command to turn the syndaemon back off or set it to normal?

Or maybe Lance is up to it :).

EDIT: cool, I just earned a new title with messed up and toppled beans. Now I'm really somebody...

---

### Post by noob_Lance on 2006-03-14
patrick... uncomment out all your touchpad stuff in xorg. 
now in that section add the:

Option      	"SHMConfig" 		"on"


into that section. from the looks of it... it should jsut turn your touchpad on and off... as the pointer is in the other "input device" for the mice.. if it dosnt work.. well keep trying different options until you get it.. then post the solution for everyone else ^_^. im no help.. me and my gateway here.

As for you m.musashi, i will try to modify my program to do this... but im not sure how haha.. ill figure it out tho and make another script.. have 2 solutions in one howto :). but for now (and probally the next day or two...) i will be installing a new laptop hard drive... so backup and unzippin.. here i come :). btw... i have another howto up my sleve :) that will be for another time :p

---

### Post by patrick.ubuntu on 2006-03-15
noob_Lance, thanks for your help.  After finding out the hard way that commenting out lines requires ONE, and not two, of these guys #, I finally got the file reworked in safe mode.  I've uncommented all the lines and added the line you suggested into the file towards the end of the trackpad section.  It now reads like this-

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection

Hopefully that's right.  Now for the really dumb question- now what do I do to turn it off?  Is the SHMConfig pointing to one of the function keys or something?
I really appreciate any light you can shed on this to help rid me of some of my "noob-ishness"!  (I'm obviously an actual noob, whereas I think you're probably keeping that name with a sense of irony...)
Cheers,
pt

---

### Post by m.musashi on 2006-03-15
[QUOTE=patrick.ubuntu]Now for the really dumb question- now what do I do to turn it off?  Is the SHMConfig pointing to one of the function keys or something?
I really appreciate any light you can shed on this to help rid me of some of my "noob-ishness"!  (I'm obviously an actual noob, whereas I think you're probably keeping that name with a sense of irony...)
Cheers,
pt[/QUOTE]
Lance is the expert here but I think the SHMConfig doesn't need to be "turned off". I believe it just allows configurations of the touchpad such as the on/off switch that Lance created. Any scripts you run should be able to be turned on or off but the SHMConfig would stay "on" to allow that. Does that make sense?

Does the F5 key combo that Lance explained allow you to turn the touchpad on and off? If it does and does not have any effect on the eraser thing then you are probably set. If it turns both off then that will require some more work.

Hope that helps to clear things up a bit. If not, well it's probably because it's getting late :).

---

### Post by m.musashi on 2006-03-15
[QUOTE=noob_Lance]As for you m.musashi, i will try to modify my program to do this... but im not sure how haha.. ill figure it out tho and make another script.. have 2 solutions in one howto :). but for now (and probally the next day or two...) i will be installing a new laptop hard drive... so backup and unzippin.. here i come :). btw... i have another howto up my sleve :) that will be for another time :p[/QUOTE]
No worries. If you feel enlightened then go for it. If not, I will play around with it. I didn't even know about the "syndaemon -d -i 2" option until dbunder posted it. Until I play with both that and the F5 switch I won't know which suits me better. However, at the moment, once you turn on the syndaemon option it's on until you reboot. Turning it off will require more knowledge of it's options. I haven't used it much yet but I can see how not being able to turn it off could be a problem.

---

### Post by noob_Lance on 2006-03-15
m.musashi is right patrick... jsut leave it as Option "SHMConfig" "on"
the script once set up correctly.. will do the rest for you. and m.musashi i have ubuntu installed on my laptop once again. new hard drive is working :) lol but now to get wireless again. once i get wireless ill have the new script up asap :p 

hm.. this one will be tricky lol... but i think i can get it to work. after jsut playing around with it for a few seconds i might have a solution haha :D

---

### Post by m.musashi on 2006-03-15
Okay, I played around with the syndaemon a bit and managed to modify Lance's first how to and use it to control the syndaemon option if you like it.

I did two bash scripts as follows
```
#!/bin/bash
#Turn on syndaemon with 2 second delay

syndaemon -d -i 2
```
and
```
#!/bin/bash
#Turn off syndaemon

killall syndaemon
```
Follow Lance's instructions and save these as something like touchpadsynon.sh and touchpadsynoff.sh, chmod 777 them, and edit the sudoers file.

I then used the xbindkeys to assign each to an F key as per Lance's instructions. It's a bit of a hack job but it works. It's also my first attempt at something like this so don't flame me if it's poor scripting or something. I now have ultimate power over my touchpad :twisted: . Hope this isn't completely useless info.

Lance, I looked at the python script but don't have a clue how to modify it to make a single on/off switch. It's probably not overly necessary anyway.

---

### Post by noob_Lance on 2006-03-15
well man.... let me jsut say that after you posted that ... about 5 seconds went by before i opened up my script and started to modify it ... and im telling you im close to the solution haha... it jsut dosnt seem to want to work right :p but ill post it when i get it working. for now tho... im trying to install VMware player and such lol. But if you want to add me to msn ill talk ya thru editing it if you want

~Lance

btw, my msn is [email]silver_suicide_rider@hotmail.com[/email]

for you.. and anyone who wants help lol

---

### Post by sethrd on 2006-03-26
I'd just like to add, you have to restart X for this to work. At least, I did.

Thanks for this. Been trying to figure it out for a while.

---

### Post by rante on 2006-03-27
How do i get xbindkeys to auto start? I need to type in the terminal "xbindkeys" to get the shortcut to work.

Thanks

---

### Post by noob_Lance on 2006-03-27
yup thats all you have to do to start it. you can set it up to start when gnome starts. System > Preferences > Prefered Applications

its in there somewhere :)

~Lance

---

### Post by brallan on 2006-03-27
edit: the only difficulty I had with this with the > sudo visudo command, only because nano asked me if i wanted to save it to /etc/sudoers.tmp, which of course is NOT what you want, but to save it to /etc/sudoers. after that it worked great. I am starting a [wiki]("https://wiki.ubuntu.com/SynapticsTouchpadHowTo") which will put the steps in order a bit clearer for total noobs like me.

the touchpad itself is a bit of a problem, but i often use it, because of the silly wireless mouse which often eats my last pair of batteries. is there any way to simply disable tapping or make it less sensitive? they don't call it a touchpad for nothing.

---

### Post by noob_Lance on 2006-03-27
[QUOTE=m.musashi]Okay, I played around with the syndaemon a bit and managed to modify Lance's first how to and use it to control the syndaemon option if you like it.

I did two bash scripts as follows
```
#!/bin/bash
#Turn on syndaemon with 2 second delay

syndaemon -d -i 2
```
and
```
#!/bin/bash
#Turn off syndaemon

killall syndaemon
```
Follow Lance's instructions and save these as something like touchpadsynon.sh and touchpadsynoff.sh, chmod 777 them, and edit the sudoers file.

I then used the xbindkeys to assign each to an F key as per Lance's instructions. It's a bit of a hack job but it works. It's also my first attempt at something like this so don't flame me if it's poor scripting or something. I now have ultimate power over my touchpad :twisted: . Hope this isn't completely useless info.

Lance, I looked at the python script but don't have a clue how to modify it to make a single on/off switch. It's probably not overly necessary anyway.[/QUOTE]


brallan- follow what m.musashi posted there and my howto. with those you will get the results you want.

~Lance

---

### Post by OldFart on 2006-03-28
I am worse than a newbie, I am an old newbie](*,) Could turning the touch pad off help me get my mouse to work?:confused:

---

### Post by m.musashi on 2006-03-28
[QUOTE=OldFart]I am worse than a newbie, I am an old newbie](*,) Could turning the touch pad off help me get my mouse to work?:confused:[/QUOTE]
Probably not. What is the problem with the mouse? Are you doing bluetooth or usb? I'm not a bluetooth expert but I did get it working using a howto in here somewhere. I'll try and find it. If you can't get a usb mouse to work it is probably something to do with drivers or settings in the xorg.conf file. Could you post the contents of /etc/X11/xorg.conf? Might be good to start a new thread as you might not get much help in here (not as many will find it). You might link it here though so *we* can find it.

---

### Post by m.musashi on 2006-03-28
Anyone know if the xbindkeys should work in KDE 'cause they don't for me. Or at least something isn't working in KDE because I can't kill the touchpad. If I switch to gnome it works fine. Switch to KDE and no go. One thought, is there a way to get xbindkeys to run at startup in KDE? I know you can in gnome and that is probably why it works there. What about the KDE side?

Thanks.

---

### Post by kavenien on 2006-04-04
An option in Gnome (perhaps there's something similar in KDE?):

If (like me) xbindkeys isn't working properly (probably my fault) or you'd rather not install it, you can add a toggle button on a panel.

Follow steps *1, 2, 3, then

Right-click panel
> Add to Panel...
> Custom Application Launcher
> enter whatever name (Touchpad Toggle?)
> in Command:enter /usr/local/bin/touchpad.py
> pick an icon if you want (a handy one is located [here]("http://greengenes.lbl.gov/Download/Crystal%20Clear/22x22/apps/Synaptics%20touchpad.png"))

This will default as the touchpad being on during session start, click the new panel button when you want to toggle it off.

UPDATE

Just found [this page]("http://gnome-hacks.jodrell.net/hacks.html?id=14"), which describes how to add your own shortcuts in Gnome. So...

Follow steps *1, 2, 3, then (edited for the purpose of this thread):

> Run gconf-editor (SystemTools->Configuration Editor).

Go to "Apps->Metacity->Keybinding Commands"

Here we have a list of twelve slots for commands. We want one of them
(command_3, say) to run touchpad.py:

Double click (or right-click and choose "Edit key" in the popup-menu), and you
will get to edit the key. In "Key Value", enter "/usr/local/bin/touchpad.py". Press OK.

Note that there is a bit of explanatory text at the bottom of the gconf-editor
screen.

We have our command, but now we must also tell Metacity what key to press to
run it. Go to "Global keybindings" (in the list to the left). As you see, there
are a lot of stuff to bind keys to. Scroll down until you find the line
"run_command_3" - it's about in the middle of the list.

* Select the line and double-click or select "Edit key". Change the key value
to "<Control>F6". Press "Ok".

You're done! Try it by pressing ctrl-F6 and you should disable/enable the touchpad.

Hope this all helps other people who may have had trouble with xbindkeys.

---

### Post by starfire1983 on 2006-04-08
I've tried each solution in this thread and none of them have worked. None. I've followed them to the "T". I'm using a synatpics touchpad on a Gateway 7322GZ

---

### Post by noob_Lance on 2006-04-08
Did you restart xbindkeys then try it?

~Lance

---

### Post by srwilson on 2006-05-26
I tried this solution on my Thinkpad through step 4.  But it seems when I type either tpon or tpoff into the console (which I assume would do the same thing as binding it to keys) it gives me the error 

"Can't access shared memory area. SHMConfig disabled?"

I'm relatively new to linux so this message really mystified me.

---

### Post by omair.majid on 2006-05-27
I am getting the same error

$ sudo /usr/local/bin/touchpad.py
Can't access shared memory area. SHMConfig disabled?

What does this mean? I have added the option to enable SHMConfig in my xorg.conf :
Option "SHMConfig" on

Oh yeah, i am running dapper beta if it makes any difference

---

### Post by lohmueller on 2006-05-30
This simple script also changes the touchpad-state. It also outputs a nice message (passive popup) if a kde session is running.

```

#!/bin/bash

if [ "$(synclient -l | awk '$1=/TouchpadOff/ { print $3 }')" == "1" ] ; then
    # Touchpad disabled
    NEWSTATE="0"
    MSG="Touchpad enabled"
else
    # Touchpad enabled
    NEWSTATE="1"
    MSG="Touchpad disabled"
fi

synclient touchpadoff=${NEWSTATE}
[ "$(pidof dcopserver)" ] && dcop knotify default notify '' 'Touchpad' "${MSG}" '' '' 16 0

```

I added a K-menu-entry and associated a keyboard shourtcut to it. Works great ;-)

---

### Post by Marcy on 2010-04-13
Hi,
I am definitely what you would consider GREEN. I desperately need to be able to turn off my touchpad when I am writing but the instructions on how to do it were very confusing to one such as myself. Are there some initial instructions you could give me to get me started? I'm not even sure quite where to begin. If you could maybe tell me how to get into a place where I could alter code that might help. Unless you think I might just make a mess of it?
 
Thanks :-)

---

### Post by bookcrazy on 2010-07-05
> **cbudden said:**
> On my laptop, I just need to do Fn + F7.
You just saved me hours of searching! Thank you

---

### Post by zawmai on 2010-09-10
> Name This File tpoff
 	Code:
 	#!/bin/bash #  synclient touchpadoff=1 
And this file tpon
 	Code:
 	#!/bin/bash #  synclient touchpadoff=0 
These will be your on and off switches :smile:

Hey, I'm confused with STEP 2. What do you mean by naming the file?

---

