---
title: "HOWTO: Adjust brightness on Sony Vaio"
date: 2005-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Sir Bogoff on 2005-11-10
Upon installing Ubuntu 5.10 on my Sony Vaio I discovered that the brightness was really bad. I hunted around for some info but nothing would keep the brightness settings upon reboot. Sure I could go into a terminal and reset it but what a pain in the arse. 

I tried this first (you can do this if you like but try lower down first). 
Install the package spicctrl (this is in universe so you need to make sure you repository's are up to date),
```
sudo apt-get install spicctrl
```
which gives you command-line control over brightness . Try 
```
spicctrl -b 244
```
to brighten the screen (the higher the number the brighter, the lower..well I am sure you can figure it out).

This worked great until I rebooted and then back to square one.


Now, this works on my Vaio PCG-GRX600P in breezy and I would presume other Vaio models but seeing as how I only have the one I can't swear to it. If it works for you, post your result here. If it doesn't, well sorry about your luck but I found this on my own and I am a learner at this.

Step 1.
```
sudo chown system_username /proc/acpi/sony/brightness 
echo "n" > /proc/acpi/sony/brightness 
```
where n is a number between 1 and 8. 
Note that the quotes around the numeric value are required.

1 is the dimmest setting and 8 is the brightest.
Play around until you find the one you prefer but remember it for step 2.
```
sudo chown root /proc/acpi/sony/brightness
``` 

Step 2.
```
sudo chown system_username /proc/acpi/sony/brightness_default
echo "n" > /proc/acpi/sony/brightness_default
```
where n is the same number that you set it to in step 1.
```
sudo chown root /proc/acpi/sony/brightness_default
```
Now try a reboot (you don't have to obviously) to see if the settings stick.

Hope that worked for you.

These two work in Hoary but I couldn't say about the rest of it.
```
echo "1" > /proc/acpi/sony/brt
``` sets the lowest screen brightness
```
echo "8" > /proc/acpi/sony/brt
``` sets the highest screen brightness

---

### Post by smack on 2005-11-10
That's working great on my vaio pcg-v505 thanks a lot. Maybe this will get me some extra battery life when I need it. :cool:

---

### Post by no1wantdthisname on 2005-11-11
If you have one of the Vaio FS series then you can just use the fn keys for brightness control.  
Not sure about other models.

EDIT: Look down for the how to.

---

### Post by kairu0 on 2005-11-11
[QUOTE=no1wantdthisname]If you have one of the Vaio FS series then you can just use the fn keys for brightness control.  
Not sure about other models.

Go here: [http://forums.gentoo.org/viewtopic-p-2722251.html#2722251](http://forums.gentoo.org/viewtopic-p-2722251.html#2722251) 
The fn keys for volume control work as well.
And when you change volume or brightness a osd shows at the bottom of the screen for the current volume/brightness.

And if you're trying to extend battery life, you can have the powernowd script check whether your laptop is plugged in or not and then turn on powernowd/lower brightness when on battery, and turn off powernowd/raise brightness when plugged in.[/QUOTE]

Thanks for the find! I just followed the instructions in that link and now I have working volume and brightness keys on my SONY VAIO VGN-FS21 (this is a JAPANESE model.) There is also an OSD at the bottom of the screen!

One note: the forum introduces an rc.d script to start and stop the key handling daemon, but I found it simpler to add "fsfn" to the end of my /etc/init.d/bootmisc.sh.

---

### Post by Sir Bogoff on 2005-11-12
Glad it's helping.

Now I just have to figure out the FN keys.

Will try this and let you know how it goes.

> Go here: [http://forums.gentoo.org/viewtopic-p...1.html#2722251](http://forums.gentoo.org/viewtopic-p...1.html#2722251)
The fn keys for volume control work as well.

---

### Post by Sebby on 2005-11-12
I'm trying to get the Fn keys working on my Sony VAIO FS215S, but being a Linux newbie, I'm struggling a bit. I've been following the well-known Gentoo guide.

I do:

```
wget http://download.berlios.de/fsfn/sony_acpi.tar.gz 
tar zxvf sony_acpi.tar.gz 
cd sony_acpi 
make && sudo make install

modprobe sony_acpi 
ls /proc/acpi/sony 
```

This is all fine, but when I do [i[echo sony_acpi >> /etc/modules.autoload.d/kernel-2.6[/i], I get an error. Now I'm sure that this is because this guide is Gentoo-specific, but I don't know how to alter it for Ubuntu.

Also, I started the next stage:

```
wget http://download.berlios.de/fsfn/fsfn-0.2.tar.gz 
tar zxvf fsfn-0.2.tar.gz 
cd fsfn-0.2 
./configure && make && sudo make install 
```

When I do *./configure*, I get an error about Xosd not being a new enough version (I think it said it's < 0.7.0), but I can't seem to update it.

Any help would be grately appreciated.

---

### Post by no1wantdthisname on 2005-11-12
EDIT: Updated for dapper

First of all do this:
```
sudo apt-get install libasound2-dev build-essential linux-headers-$(uname -r) gcc-3.4
```

If you want the onscreen display then also get
```
sudo apt-get install libxosd-dev 
```

Next:
```
wget http://download.berlios.de/fsfn/fsfn-1.0.tar.gz
tar zxvf fsfn-1.0.tar.gz
cd fsfn-1.0
```

If you want osd:
```
./configure && make && sudo make install 
``` 

No osd:
```
./configure --disable-xosd && make && sudo make install 
``` 

After installing that you can test this by doing:
```
sudo fsfn
```

If you enabled osd:
```
fsfn -o
``` 
You should see a bar at the bottom of your screen when using the fn keys.

Next would be the startup script.  The script from the gentoo site doesn't work so I wrote my own.  This just starts up fsfn.
Attached at bottom.

Make it executable and move the fsfn script to /etc/init.d/
```
chown root:root fsfn.txt && sudo chmod +x fsfn.txt && sudo mv fsfn.txt /etc/init.d/fsfn
```

To start it up on boot
```
sudo update-rc.d fsfn defaults
```

If you want the osd to show up when you change volume/brightness
click the start menu and SYSTEM>PREFERENCES>SESSIONS, click the startup tab and add 
"fsfn -o" with order 50.

---

### Post by Sebby on 2005-11-12
Thanks so much, that's exactly what I needed! Everything is working perfectly. Thanks again. :)

---

### Post by swoon on 2005-11-12
when i do:
modprobe sony_acpi
ls /proc/acpi/sony/

all it shows is:

brightness  brightness_defaul

why am is it no showing/installing 'fnkey' ?

---

### Post by no1wantdthisname on 2005-11-13
[QUOTE=swoon]when i do:
modprobe sony_acpi
ls /proc/acpi/sony/

all it shows is:

brightness  brightness_defaul

why am is it no showing/installing 'fnkey' ?[/QUOTE]

Er, not sure, what model do you have?  This applies only to FS series.  For example, I have a Vaio VGN-FS640/W.

You might have to do a 
```
sudo rmmod sony_acpi
```
beforehand as well.

---

### Post by Sebby on 2005-11-13
[QUOTE=swoon]when i do:
modprobe sony_acpi
ls /proc/acpi/sony/

all it shows is:

brightness  brightness_defaul

why am is it no showing/installing 'fnkey' ?[/QUOTE]
I had this exact problem last night when I was trying to set it up. Reboot your computer and try again. It worked for me!

---

### Post by swoon on 2005-11-14
[QUOTE=no1wantdthisname]
```
sudo rmmod sony_acpi
```
beforehand as well.[/QUOTE]

i have a fs-570. this worked, thanks.

---

### Post by madchicken on 2005-11-14
Hi, I tried to install the gentoo daemon for sony fn keys, but when I launch it and I try to change volume or brightness I get this error:

```

amixer: Unable to find simple control 'Front',0

fsfn: simple.c:1472: snd_mixer_selem_get_playback_volume: Assertion `elem' failed.

```

Do I missed something?

--Pierpaolo

---

### Post by Sir Bogoff on 2005-11-14
Well what can I say. I tried to do an upgrade to Firefox over the weekend and completely screwed this thing up. So I did a complete blow out and reinstall and guess what? I didn't have to do any of the setup for this stuff. The function keys all worked straight off the bat and the brightness was set to what I normally would have it as a default. Not to sure what is going on here but I never got the function keys to work before. Oh well, I hope at least I helped a few people with my original post but my problem seems to have gone away all by its self.

Oh as far as the brightness function keys are concerned, I only have one which is for dimming (F5) I discovered by playing around that the F6 key (although not marked) is for brightening.

---

### Post by no1wantdthisname on 2005-11-14
[QUOTE=madchicken]Hi, I tried to install the gentoo daemon for sony fn keys, but when I launch it and I try to change volume or brightness I get this error:

```

amixer: Unable to find simple control 'Front',0

fsfn: simple.c:1472: snd_mixer_selem_get_playback_volume: Assertion `elem' failed.

```

Do I missed something?

--Pierpaolo[/QUOTE]

It seems your sound card doesn't have the Front control.  
If you go to START>SOUND&VIDEO>VOLUME CONTROL you'll probably see volume controls for PCM, master, headphone, etc.  If you don't see Front then yeah, this won't work for you.  
You would have to modify the fsfn script to control something else besides Front or you can try to modify your alsa to create a Front control.  Both of which I have no idea on how to do. :???:

---

### Post by Sebby on 2005-11-14
Further to my post saying that everything was working fine, it seems that the sound control doesn't actually do anything. The slider display at the bottom of the screen comes up and moves up and down, but it doesn't actually adjust the volume. Can anyone help?

---

### Post by Sebby on 2005-11-14
[QUOTE=Sebby]Further to my post saying that everything was working fine, it seems that the sound control doesn't actually do anything. The slider display at the bottom of the screen comes up and moves up and down, but it doesn't actually adjust the volume. Can anyone help?[/QUOTE]
Scratch that, it's sorted. It was due to a problem with the Intel HD audio (again). I switched to the OSS mixer instead of the Alsa mixer, but a reboot was required to get fsfn working. :)

---

### Post by madchicken on 2005-11-15
[QUOTE=no1wantdthisname]It seems your sound card doesn't have the Front control.  
If you go to START>SOUND&VIDEO>VOLUME CONTROL you'll probably see volume controls for PCM, master, headphone, etc.  If you don't see Front then yeah, this won't work for you.  
You would have to modify the fsfn script to control something else besides Front or you can try to modify your alsa to create a Front control.  Both of which I have no idea on how to do. :???:[/QUOTE]

Thanks...you are right, I don't have the Front control for my alsa driver.
I will to modify the fsfn code...

thank you very much.

---

### Post by blackpaw on 2005-11-21
I was doing a Breezy-Installation (full) on my Vaio N505SN and all Fn-Keys worked out-of-the-box. Brightness, Volume, Suspend, Hibernate :)

Now that I did a server-install (only 400Mhz and 128MB ram, so I wanted to try xubuntu) I had to install sonypi and get acpi running manually. ok.

But now the Fn-Keys work and call the scripts as planned (like Fn-F5 calls "sonybright.sh down" or whatever but nothing happens.

when I tail /var/log/acpid I get the call of the keypress but no response from the handler, just a "exited with status 0 (or 2 sometimes)

can someone help me get the Fn-Keys back?


andreas

---

### Post by Global Havok on 2005-11-21
To get the hibernate functionality to work, simply:

sudo cp /etc/acpi/hibernate.sh /bin/hibernate

---

### Post by blackpaw on 2005-11-21
.

---

### Post by Sebby on 2005-11-22
I have just compiled a new kernel (2.6.14.2) and am trying to setup the Fn keys again. I have done the sony_acpi part successfully, as when I do ls /proc/acpi/sony I get brightness  brightness_default  fnkey. However, I run through the fsfn part, which appears to go fine, but when I try sudo fsfn, I get:

```
Opening event interface /dev/input/event0
event interface open failed: No such file or directory

``` 

Can anyone help? Many thanks in advance.

---

### Post by no1wantdthisname on 2005-11-22
[QUOTE=Sebby]I have just compiled a new kernel (2.6.14.2) and am trying to setup the Fn keys again. I have done the sony_acpi part successfully, as when I do ls /proc/acpi/sony I get brightness  brightness_default  fnkey. However, I run through the fsfn part, which appears to go fine, but when I try sudo fsfn, I get:

```
Opening event interface /dev/input/event0
event interface open failed: No such file or directory

``` 

Can anyone help? Many thanks in advance.[/QUOTE]


Ran into same problem when I tried to compile for debian.  You can try to use a different event handler.  
so 
```
fsfn -d /dev/input/event1  
```
If that doesn't work just test the different events in fsfn.  Had to try til event3 til it worked for debian.

If that works, then you need to change the /etc/init.d/fsfn file to have those parameters passed.
Add this to end of the start line so it looks like :
```
start-stop-daemon --start --quiet --oknodo --exec $DAEMON -- -d /dev/input/event(WHATEVER NUMBER)
```

---

### Post by blackpaw on 2005-11-23
yay! success :)
thank you all!

cheers,


andreas

---

### Post by Sebby on 2005-11-23
[QUOTE=no1wantdthisname]Ran into same problem when I tried to compile for debian.  You can try to use a different event handler.  
so 
```
fsfn -d /dev/input/event1  
```
If that doesn't work just test the different events in fsfn.  Had to try til event3 til it worked for debian.

If that works, then you need to change the /etc/init.d/fsfn file to have those parameters passed.
Add this to end of the start line so it looks like :
```
start-stop-daemon --start --quiet --oknodo --exec $DAEMON -- -d /dev/input/event(WHATEVER NUMBER)
```[/QUOTE]
Thanks for your reply. However, I get the same error for events 1 through to 10...

I just don't understand - before I compiled a new kernel, this worked perfectly with no configuration required. Any help would be much appreciated!

---

### Post by kairu0 on 2005-11-23
[QUOTE=Sebby]Thanks for your reply. However, I get the same error for events 1 through to 10...

I just don't understand - before I compiled a new kernel, this worked perfectly with no configuration required. Any help would be much appreciated![/QUOTE]

That must mean that you already had the right event set in the beginning. Now it's a matter of sorting out kernel/module options.

---

### Post by drakeoutlaw on 2005-11-24
no1wantdthisname, You're THE DUDE!. Thank you very much. Your instructions worked perfectly on my Sony Vaio VGN-FS630 running Breezy  with 2.6.12-10-386 kernel.

Thanks again and regards, 

Drake

---

### Post by kairu0 on 2005-11-25
[QUOTE=drakeoutlaw]no1wantdthisname, You're THE DUDE!. Thank you very much. 
Drake[/QUOTE]

Yeah! Keep up the good work!

---

### Post by Sebby on 2005-11-27
Hi guys

Is there a way that I can set the default brightness to highest? I've been thinking that my screen is looking a little dim, and it's because it's only set to just over half upon boot. I have to manually push it up to the highest each time.

Many thanks!

---

### Post by no1wantdthisname on 2005-11-27
[QUOTE=Sebby]Hi guys

Is there a way that I can set the default brightness to highest? I've been thinking that my screen is looking a little dim, and it's because it's only set to just over half upon boot. I have to manually push it up to the highest each time.

Many thanks![/QUOTE]

```
sudo gedit /proc/acpi/sony/brightness_default
```
Put 8 in there.  I'm assuming this is where the default is.  Haven't tried it myself.

---

### Post by Sebby on 2005-11-27
Thanks. I guess what I really am suggesting is to have the maximum brightness when it is running of AC power, and a bit lower when on battery. Is this possible?

---

### Post by no1wantdthisname on 2005-11-27
Yeah I've set my laptop to turn brightness to 8 and turn off powernowd for when it's plugged in.
When it's on battery the brightness goes to 1 and powernowd turns on.
This also leaves powernowd off when you boot up if you're plugged in.  

To do this I modified the powernowd script in /etc/init.d/ and the power.sh script in /etc/acpi/.  I've attached them.

Just search in the powernowd script for 
```
echo 1 > /proc/acpi/sony/brightness
```
if you want to change how low brightness is when you are unplugged.

Probably a better way to do this, but eh, whatever.

---

### Post by Sebby on 2005-11-27
[QUOTE=no1wantdthisname]Yeah I've set my laptop to turn brightness to 8 and turn off powernowd for when it's plugged in.
When it's on battery the brightness goes to 1 and powernowd turns on.
This also leaves powernowd off when you boot up if you're plugged in.  

To do this I modified the powernowd script in /etc/init.d/ and the power.sh script in /etc/acpi/.  I've attached them.

Just search in the powernowd script for 
```
echo 1 > /proc/acpi/sony/brightness
```
if you want to change how low brightness is when you are unplugged.

Probably a better way to do this, but eh, whatever.[/QUOTE]
Great, this is exactly what I want, but I'm a little confused about what I need to do in the files. :rolleyes: 

I don't want powernowd not to load when the adaptor is plugged in, I just want to dim/brighten the screen depending on when the adaptor is plugged in.

:cool:

---

### Post by no1wantdthisname on 2005-11-27
[QUOTE=Sebby]Great, this is exactly what I want, but I'm a little confused about what I need to do in the files. :rolleyes: 

I don't want powernowd not to load when the adaptor is plugged in, I just want to dim/brighten the screen depending on when the adaptor is plugged in.

:cool:[/QUOTE]

Okay, here's the modified powernowd and power.sh

EDIT: See below for fixed powernowd

---

### Post by Sebby on 2005-11-27
[QUOTE=no1wantdthisname]Okay, here's the modified powernowd and power.sh[/QUOTE]
Thanks, that works brilliantly. Just out of interest, what does the echo 1 in powernowd do compared to the echo 1 in power.sh? I'm just interested to know what they are both needed for.

---

### Post by no1wantdthisname on 2005-11-27
The echo 1 in the powernowd script is for when powernowd is stopped.  It's just left over from my version.  Seeing as how you don't stop powernowd, it shouldn't matter.  You can remove it if you want.

EDIT: See below for fixed version.

---

### Post by Sebby on 2005-11-27
[QUOTE=no1wantdthisname]The echo 1 in the powernowd script is for when powernowd is stopped.  It's just left over from my version.  Seeing as how you don't stop powernowd, it shouldn't matter.  You can remove it if you want.[/QUOTE]
When I rebooted my computer, it came back on with the screen on its dimmest setting. So I changed it to 8 and now the computer comes on with the brightest setting. :confused:

---

### Post by no1wantdthisname on 2005-11-27
Ah yeah, I messed up.  Try this version.
The modification to the powernowd script is for when you boot up your laptop.  It'll check whether your laptop is plugged in or not and adjust the brightness accordingly.  
The power.sh script is for when you unplug and plug in your laptop.  It'll just change brightness accordingly.  Change the echo 1 and echo 8 in both files if you want the max brightness or min brightness to be different.

---

### Post by Sebby on 2005-11-28
Excellent, thanks. Now I have it working just like under Windows. :D

---

### Post by drakeoutlaw on 2005-11-28
You guys are the Best! I have nearly attained full functionality of my Sony Vaio FS630. Only a few items remain.

1. Please help to tweak the fsfn utility to be able to use the S1 and S2 programmable buttons. I've tried to download the new fsfs-0.3-r1 but Belios's server seems to be down.

2. My vaio freezes/hangs occasionally for no apparent reason.

Any suggestions? I've already tried noapic nolapic.

---

### Post by no1wantdthisname on 2005-11-28
[QUOTE=drakeoutlaw]You guys are the Best! I have nearly attained full functionality of my Sony Vaio FS630. Only a few items remain.

1. Please help to tweak the fsfn utility to be able to use the S1 and S2 programmable buttons. I've tried to download the new fsfs-0.3-r1 but Belios's server seems to be down.

2. My vaio freezes/hangs occasionally for no apparent reason.

Any suggestions? I've already tried noapic nolapic.[/QUOTE]


fsfn doesn't deal with the S1 and S2 shortcuts (I think).  You have to use setkeycodes.  Try this:
```
sudo dmesg -c
```
to clear dmesg.
Then push S1.
```
dmesg
```
should say something like setkeycodes e075.

Now push S2, and do dmesg again.
Should show another code.  There's another guide on this forum about using setkeycodes that goes into more depth.

Basically you just have to set S1 & S2 to some code.
Then you can just go to keyboard shortcuts and set some event to S1/S2.  Or go to gconf-editor and add a custom command when you push it.

I don't use S1 and S2 though so I don't know.  And, for some reason both S1 and S2 seem to cause the same event for me so you might only have 1 shortcut.  

As for the sudden freeze/hang, that's pretty vague.  Are you using the linux-686 kernel?

---

### Post by drakeoutlaw on 2005-11-28
>>As for the sudden freeze/hang, that's pretty vague. Are you using the linux-686 kernel?

No, using 2.6.12-10-386. But your suggestion is definitely followuppable (nice word huh?)

As for S1 and S2 they both generate the same keycode: e075. 

Lets hope the new 0.3 version of fsfn has a solution.

---

### Post by Sebby on 2005-11-28
[QUOTE=drakeoutlaw]No, using 2.6.12-10-386. But your suggestion is definitely followuppable (nice word huh?)[/QUOTE]
It's worth trying linux-image-2.6.12-10-686, which you can install from Synaptic. I'm not sure that it will change anything, though. Are your crashes occurring when rebooting/shutting down or just generally when using Ubuntu?

---

### Post by drakeoutlaw on 2005-11-29
It happens during general use. Sometimes it will go for 3 or 4 hrs without hanging. Other time it will hang twice in half an hour.

---

### Post by Sebby on 2005-11-29
[QUOTE=drakeoutlaw]It happens during general use. Sometimes it will go for 3 or 4 hrs without hanging. Other time it will hang twice in half an hour.[/QUOTE]
That's very odd. Well give the 686 kernel a try anyway.

---

### Post by drakeoutlaw on 2005-11-29
Full credit  to Mr. Pierre Poissinger for making the S1 and S2 buttons work PLUS! a fsfn.conf file to make all fn keys fully programmable!

Mr. Poissinger writes:

> Hi,

Actually I am working on an new version with some other people. This
will include a easy way to enable specific actions for any keys. I
include the latest SVN stable tarball for your usage.

Please note this version can have bugs, so feel free to post bugs on
[http://developer.berlios.de/bugs/?group_id=4604](http://developer.berlios.de/bugs/?group_id=4604) (simply set version as
'svn rev. 22' for this version)

A few words of explanations about this version:
* syslog output (to see what's going on...)
* hibernate supported (previous version didn't function after a hibernate)
* Auto discover input event to use (not by default)
* User configuration: You can set a few parameters in a config file
(must be /etc/fsfn.conf - I included mine as example)

here comes the possible entries (None are mandatory - default value
should works):
DEVICE=/dev/input/eventX
--> Will use the given event as keyboard entry
or
DEVICE=AUTO
--> fsfn will try to determine automatically the right device for your laptop

ALSA_NAME=Front
--> The name of the alsa 'mixer' to use

F2_CMD=/something/somecommand
F3_CMD=/something/somecommand
F4_CMD=/something/somecommand
F5_CMD=/something/somecommand
F6_CMD=/something/somecommand
F7_CMD=/something/somecommand
F10_CMD=/something/somecommand
F12_CMD=/something/somecommand
--> you can set or even overload Fn+Fxx command - If you overload
built in function, no OSD will appears

S1_CMD=/something/somecommand
S2_CMD=/something/somecommand
--> To set command to execute

OSD_FONT=-*-lucida-*-*-*-*-24-*-*-*-*-*-iso8859-1
--> the font for OSD, use xfontsel to generate the font you want

OSD_VCOLOR=green
--> OSD volume color to use
OSD_BCOLOR=LawnGreen
--> OSD brightness color to use

Hope this will helps,
Pierre

The updated fsfn-1.0-svn.tar.gz  and fsfn.conf is attached.
[ATTACH]3970[/ATTACH]

[ATTACH]3971[/ATTACH]

---

### Post by drakeoutlaw on 2005-12-06
Ok figured out the mysterious hanging problem.

When the machine is far from the access point and the signal breaks down the ipw2200 driver caused the machine to freeze. Whenever I was near the AP, the machine sang along without a hiccup.

Solution: Compile/install new ipw2200 1.0.8 version along with recommended ieee80211 driver and new firmware from sourceforge.

Fixed the hang problem.

cheers all,

Drake

---

### Post by Zhukov on 2005-12-16
Hi there! I have a sony vaio fj1s and everything is fine thanks to your help :D

But there is a small problem:
Using the fn keys only allows me to toggle between to values! Using the echo 1 trough 8 i can change the levels of brightness, but not using the fn keys.
The sound is also making gigantic jumps when using fn...

Any suggestions?

---

### Post by Sebby on 2005-12-16
[QUOTE=Zhukov]The sound is also making gigantic jumps when using fn...[/QUOTE]
Same here, but I just assumed that was how it was...

---

### Post by kairu0 on 2005-12-16
[QUOTE=Zhukov]
The sound is also making gigantic jumps when using fn...

Any suggestions?[/QUOTE]

Maybe your PCM volume is set too high.

---

### Post by swoon on 2005-12-17
has anyone been able to turn off the touchpad? synaptics doesn't seem to see the touchpad at all.

---

### Post by Zhukov on 2005-12-17
Well, the sound isnt really my problem, but the brightness is.
Im only able to toggle between two types of brightness... The jump is too big! Is there any way to set this jump to one, so that it goes from 5 to 6 and so on?

Thanks!

Oh, and by the way, my touchpad is fine...

---

### Post by pijalu on 2005-12-17
Hi guys, 
I am actually one of the dev of fsfn and I notice you have issues with brightness and sound "jump"...

To be sure this is really an issue, the OSD give a % view for sound/brightness. 

Brightness level can only have a value from 1 to 8 --> Only seven jumps
Sound by default jump by 10%

If the jumps don't behave like this, then it's a bug, so posting it on the [fsfn bug p(a)lace]("http://developer.berlios.de/bugs/?group_id=4604"). This will be nice if you want it to be fixed :rolleyes: 

Last but not least, I include the current svn version (1.1 [rev 40]). This version allows you to change the OSD message and the value to use for the volume stepping
eg:
```

OSD_MSG_VOLUME=Volume (%d %%)
OSD_MSG_BRIGHT=Brightness (%d)
SOUND_STEP=5

```

Last note, starting at version 1.0: 
```

man fsfn
man 5 fsfn

```
can be usefull ;)

---

### Post by Sebby on 2005-12-18
Thanks! I've installed the latest version, but where do I change that code?

---

### Post by pijalu on 2005-12-18
just create (or edit) /etc/fsfn.conf (config file for fsfn - should be created as root and read only for other users) and add these lines. For more info of possible content, check 
```
 
man 5 fsfn

```

---

### Post by Zhukov on 2005-12-18
[QUOTE=pijalu]Hi guys, 
I am actually one of the dev of fsfn and I notice you have issues with brightness and sound "jump"...
[/QUOTE]
 - First of all congratulations for the great work! :D And thanks!

[QUOTE=pijalu]
To be sure this is really an issue, the OSD give a % view for sound/brightness. 

Brightness level can only have a value from 1 to 8 --> Only seven jumps
[/QUOTE]
 - I know i can only make 7 jumps, but with the fn keys i can only make 2! With echo i can make the seven, so i believe the problem is with fsfn.
[QUOTE=pijalu]
Sound by default jump by 10%

If the jumps don't behave like this, then it's a bug, so posting it on the [fsfn bug p(a)lace]("http://developer.berlios.de/bugs/?group_id=4604"). This will be nice if you want it to be fixed :rolleyes: 

Last but not least, I include the current svn version (1.1 [rev 40]). This version allows you to change the OSD message and the value to use for the volume stepping
eg:
```

OSD_MSG_VOLUME=Volume (%d %%)
OSD_MSG_BRIGHT=Brightness (%d)
SOUND_STEP=5

```

Last note, starting at version 1.0: 
```

man fsfn
man 5 fsfn

```
can be usefull ;)[/QUOTE]


Once again thank you, now i can customize my sound jumps, but im still having that brightness problem... Any suggestion? Well, maybe i can make a script to decrease and increase brightness now that i can assign whatever i want to the keys. :D

Still i would like to see this fixed... :mrgreen:

---

### Post by Sebby on 2005-12-18
[QUOTE=pijalu]just create (or edit) /etc/fsfn.conf (config file for fsfn - should be created as root and read only for other users) and add these lines. For more info of possible content, check 
```
 
man 5 fsfn

```[/QUOTE]
Thanks. :D

---

### Post by pijalu on 2005-12-18
[QUOTE=Zhukov]
 - I know i can only make 7 jumps, but with the fn keys i can only make 2! With echo i can make the seven, so i believe the problem is with fsfn.
[...snip...]
Still i would like to see this fixed... :mrgreen:
[/QUOTE]

Yap, that definitely strange. The problem may be a differences between FS and FJ series. To avoid polution in this thread, if you can PM your email, so I can ask you to execute few instrumenting commands and possibly make fsfn compatible with your model...

---

### Post by jowood on 2005-12-18
i have exactly the same problem.

---

### Post by jowood on 2005-12-18
i have exactly the same problem.
with echo i can make 7 jumps for brightness but with the fn key i can only make 2 (7 and 8 value)

---

### Post by pijalu on 2005-12-19
[QUOTE=jowood]i have exactly the same problem.
with echo i can make 7 jumps for brightness but with the fn key i can only make 2 (7 and 8 value)[/QUOTE]

Ok, can I ask one of you to open a bug on [http://developer.berlios.de/bugs/?group_id=4604](http://developer.berlios.de/bugs/?group_id=4604) for this problem so we can try to fix this problem ?

The info I will like to get is:
* exact model number
* result of 
```

cat /proc/acpi/sony/brightness
cat /proc/acpi/sony/brightness_default
echo 4 >> /proc/acpi/sony/brightness
cat /proc/acpi/sony/brightness
cat /proc/acpi/sony/brightness_default

```

Without help, I won't be able to do anything

---

### Post by pijalu on 2005-12-20
Hi everyone,

It looks like the "brightness" bug is now fixed thanks to your help. To be sure everyone can have access to the latest "SVN" version, I attach a tarball with this post.

A few instructions:
Update your fsfn with this version and restart the deamon, add the following
line in /etc/fsfn.conf :
BRT_SETDEFAULT=1
and try again. If it does not work, still in /etc/fsfn.conf, add the following line:
BRT_HACK_FJS=1
And restart deamon.

Cheers

---

### Post by madchicken on 2005-12-20
Hi Pijalu. Thank for the new release.
I need a little help configuring the fsfn: I saw that in the config file (man 5 fsfn) it's possible to specify the audio mixer name to use (parameter ALSA_NAME). Since the volume control is not working for me (I don't have Front component) do you have an idea for a config parameter to use for make fsfn work for me?

Thank you very much.

--
Pierpaolo

---

### Post by pijalu on 2005-12-20
[QUOTE=madchicken]Hi Pijalu. Thank for the new release.
I need a little help configuring the fsfn: I saw that in the config file (man 5 fsfn) it's possible to specify the audio mixer name to use (parameter ALSA_NAME). Since the volume control is not working for me (I don't have Front component) do you have an idea for a config parameter to use for make fsfn work for me?

Thank you very much.

--
Pierpaolo[/QUOTE]

You should use the Alsa component name that actually work as main channel on your mixer. I guess you should be able to see it use alsamixer or any(?) gui mixer... I cannot help more since I actually made this "config" entry, but I only knows about vaio with a "Front" entry :-S (and the only place were I read someone having problem with "Front" is here ... I implemented a config for it after reading your post ;-) )

---

### Post by madchicken on 2005-12-20
> You should use the Alsa component name that actually work as main channel on your mixer. I guess you should be able to see it use alsamixer or any(?) gui mixer... I cannot help more since I actually made this "config" entry, but I only knows about vaio with a "Front" entry :-S (and the only place were I read someone having problem with "Front" is here ... I implemented a config for it after reading your post  )

Eheh...yes my laptop is very strange :rolleyes: 
Thank you very much for implementing his feature for me! It worked using **ALSA_NAME=Master** in my config.

Thanks a lot!

--
Pierpaolo

---

### Post by blicero on 2006-01-10
hi.

i just got a new laptop, vaio VGN FJ.

until now I was using sony_acpi and sonyfn to make thing work.
it seems to me fsfn are more apt to do a wider range of things, so I wanted to switch to it.

First of all: i managed to make fsfn-1.1 work ONCE and then it stopped working altogether.
Second: when it worked it was not doing incremental brightness step (like i could have brightness 1 or 8 but not a step by step increase or decrease of brightness). 
Third: i could not make fsfn actually accept other command 

if anybody can help i would be most thankful :))

PS: on [www.inventati.org/blicero/](www.inventati.org/blicero/) you can find an account of my installation process. I still am wondering about the motion eye camera since it seems this vaio laptop do not work with sonypi (at least i did not have any success with it).

---

### Post by pijalu on 2006-01-10
did you try version 1.1-take2 in post 62 (and specified config keys) ? ([http://ubuntuforums.org/showpost.php?p=589970&postcount=62](http://ubuntuforums.org/showpost.php?p=589970&postcount=62))

Btw, if not working, be sure sony_acpi is loaded, you should have 3 "files" in /proc/acpi/sony

And take a look at 
sudo cat /var/log/message | grep fsfn 
to check for possible error message

---

### Post by blicero on 2006-01-12
i used exactly that version of fsfn.

first: osd is not working but it's probably conf problem
second: i cannot vary the brightness degree to 1,2,3,4,5 etc but only to 6 or 8
third: it seems any other command i connect via conf file to the fn+Fkeys combination does not work 

E.G. from conf file :
F10_CMD=/usr/bin/xterm 
doesn't work


hope my report helps :)

---

### Post by pijalu on 2006-01-12
> **blicero]i used exactly that version of fsfn.

first: osd is not working but it's probably conf problem
[/quote]
Possible, but strange... Did you launch the user space program aka "fsfn -o" ?

> 
second: i cannot vary the brightness degree to 1,2,3,4,5 etc but only to 6 or 8

Did you set
```

BRT_SETDEFAULT=1

```
in /etc/fsfn.conf ?
if this is not working, did you try the
```

BRT_HACK_FJS=1

```

> 
third: it seems any other command i connect via conf file to the fn+Fkeys combination does not work 

E.G. from conf file :
F10_CMD=/usr/bin/xterm 
doesn't work

Actually this is "normal", the execution does not yet work in user space... This means you can run anything, as long as it does not need to interfere with current user mode (eg: Launched command cannot play with X). I still have to implement this feature, but didn't have the time yet.... So in short, this is not a bug, just a missing feature  said:**
> 
hope my report helps :)

For sure, since I only have "my" laptop, it's pretty interesting to see what "problems" exists for other vaios.
Now, if 1 or 2 still give you troubles, I guess the best thing to do is to open a bug on fsfn bug page (cf previous posts), and if possible, include a 
```

sudo cat /var/log/messages | grep fsfn

```
to see where the problem is :)

---

### Post by blicero on 2006-01-12
now it works.

i am an ass and got the event device wrong!

---

### Post by pijalu on 2006-01-12
[QUOTE=blicero]now it works.

i am an ass and got the event device wrong![/QUOTE]

Normally the 1.1-take2 shouldn't need you to specified the event device anymore, it should find it "automagically"...

If this is not working on your laptop, then it's a bug :)

---

### Post by firehead on 2006-01-13
Hi all

I just installed Ubuntu Breezy on my Vaio VGN-S4XP and was quite surprised, that the fn-keys for volume-control and mute worked automagically (even with OSD). But i get no response at all when trying to adjust brightness. so i started trying your suggestions in this post:

1.) Spicctrl
easy to install, but spicctrl -b 180 (e.g.) doesn't do anything, except that spicctrl -B returns 180, but no change in brightness :( 

2.)manual
i did the whole "chown ...  /proc/acpi/sony/brightness" and "echo "n" > /proc/acpi/sony/brightness " with n between 1 and 8 but - as you could guess - without any succes (i.e. no change in brightness at all)

3.)sony_acpi fix
i followed the tutorial to the end (sudo modprobe sony_acpi) and ls /proc/acpi/sony yielded just 
brightness  brightness_default
and no fnkeys at all. following the further posts i tried reboot (no change,as expected) and sudo rmmod sony_acpi before installing it again & sudo modprobe sony_acpi...with no change at all :mad: 

i gave up on trying fsfn, since i assumed it only controles the fnkeys (maybe i'm wrong) but this would be the least of my problems...i just want to dim my screen

desperately waiting for answers...;)

---

### Post by pijalu on 2006-01-13
The Vaio S4 series don't implement ACPI actions, but use the sonypi thing (actually, it behaves like "all other previous vaio"), so using sony_acpi/fsfn is useless for your laptop.
For your brightness, take a look at the gentoo-wiki, this gave lots of usefull informations including a way to change brightness: [Gentoo Wiki about S4 series](http://gentoo-wiki.com/HARDWARE_Sony_VGN-S4)

---

### Post by firehead on 2006-01-13
Aah ok thx, i'll check this out...hope it works ;)

---

### Post by ggulik on 2006-02-02
I recently got a Vaio FJ series notebook and found this thread VERY helpful.  I am successfully using the latest sony_acpi driver just fine but I'm still having some trouble with fsfn-1.1-take2

Fn-F3&F4 work fine for audio but Fn-F5&F6 don't work for screen brightness.  The OSD keeps showing the lowest setting every time I hit those buttons but the screen doesn't brighten or dim.

I think the problem is that with the FJ series the brightness setting doesn't keep track of the current brightness level.  Here is an example:
```

[root@vaio sony]# cat brightness
0
[root@vaio sony]# echo 5 > brightness
[root@vaio sony]# cat brightness
0

```

Per the recommendations my /etc/fsfn.conf contains exactly the following:
```

BRT_HACK_FJS=1
BRT_SETDEFAULT=1

```

Before I discovered this thread and fsfn I was using a program called sonyfn which I had hacked to keep track of the brightness level itself.

Any suggestions?

---

### Post by pijalu on 2006-02-02
Can you try only with 
```

BRT_SETDEFAULT=1

```
?

Even if I don't think they should lead to problems if set together, this is strange...
Be sure you work on a "restarted" deamon (maybe a older session in memory ? - killall fsfn is your friend)

If still not working, can you post the result of
```

sudo grep /var/log/message | grep fsfn

```
(you can post only the latest reload) - it should contains lines like "Writing to default brigthness" (if BRT_SETDEFAULT) and "FSJ HACK:current brightness XX "
 (if BRT_HACK_FJS)

If you are curious and want to hack around, take a look in src/acpihandler.c , the function should be quite near of sonyfn  ;-)

Hope this helps

---

### Post by ggulik on 2006-02-02
I tried BRT_SETDEFAULT=1 by itself and that didn't fix it.

I even rebooted just to make sure the old version wasn't "lingering" somewhere.

So, I put the BRT_HACK_FJS back in and here is the output from /var/log/messages:

```
Feb  2 13:48:42 vaio fsfn[6168]: Loading config file /etc/fsfn.conf
Feb  2 13:48:42 vaio fsfn[6168]: Setting default configuration
Feb  2 13:48:42 vaio fsfn[6168]: Configuration: DEVICE=AUTO
Feb  2 13:48:42 vaio fsfn[6168]: Configuration: ALSA_NAME=Front
Feb  2 13:48:42 vaio fsfn[6168]: Configuration: F12_CMD=/bin/hibernate
Feb  2 13:48:42 vaio fsfn[6168]: Configuration: OSD_VCOLOR=red
Feb  2 13:48:42 vaio fsfn[6168]: Configuration: OSD_BCOLOR=blue
Feb  2 13:48:42 vaio fsfn[6168]: Configuration: OSD_FONT=-*-*-*-*-*-*-20-*-*-*-*-*-*-*
Feb  2 13:48:42 vaio fsfn[6168]: default configuration done
Feb  2 13:48:42 vaio fsfn[6168]: Configuration: BRT_HACK_FJS=1
Feb  2 13:48:42 vaio fsfn[6168]: Configuration: BRT_SETDEFAULT=1

```

I don't see that message about the FSJ hack.

---

### Post by ggulik on 2006-02-02
Ok, I have no idea what it didn't work before but it seems to be working now.

Something is weird about this laptop.  When I was messing with it earlier none of the Fn keys would work at all so that's the reason I decided to just reboot.  After reboot the keys started working again.  There might be something flaky about this laptop.

---

### Post by pijalu on 2006-02-02
hmm....
That's weird...
The only explanation I got was fsfn daemon not started as root or a possible "seg fault" somewhere...

If it happend again (no need to brake the "working" state... only if suddenly it stops working) what I will like to "see":
```

$ ls -l /proc/acpi/sony

```
To see what are the rights 

And open 2 consoles, one with
```

# killall fsfn
# fsfn -n

```
and the other with
```

# tail -f /var/log/messages | grep fsfn

```

the -n should keep the daemon attached to the console to see if a segfault happend and check the var log messages and provide feedback with these infos...

Anyway, hope this won't be needed anymore ;)

---

### Post by ggulik on 2006-02-02
Thanks for all the tips.  I would also especially like to thank pijalu for the work on fsfn.

I added many of the ideas in this forum to my guide on getting the Sony VAIO FJ series to run Fedora Core 4:

[http://www.gagme.com/greg/linux/vaiofj-fc4.php](http://www.gagme.com/greg/linux/vaiofj-fc4.php)

---

### Post by Zhukov on 2006-02-03
Oh, by the way...
(FJ1s/w here)
I cant use the S buttons...

---

### Post by sniffass on 2006-02-13
absolutely incredibly. I spent nearly four hours to get this working, the instructions are difficloult because there are so many conflicting ones, eventually i downloaded modules different to the ones listed and these built correctly. Just one thing left: I;m running kubuntu - how do i enter fsfn -o order 50 in to the startup, i mean where is this to be found under kde?? Until now I've been dual booting with windows but since all my keys are working now tomorrow I'm nuking windows for good. Really no reason to keep it now!! Thanks a bunch:rolleyes:


PS= thought I'd mention that i got this working on a Sony VGN-FS115E

---

### Post by Zhukov on 2006-02-13
In fact we should post new instructions.
About nuking windows... Easy there boy (just my advice). If you were holding Windows just because of the keys then you were holding Windows for some other reason. Once again, just my advice based on similar situations,
 leave Windows alone for a month or two. If you dont use it in that period than nuke it! Only then...

Glad you finally make it out! :D

Good luck!

---

### Post by sniffass on 2006-02-14
yeah i was keeping windows not just because i can use my fn keys but because acpi works. So if I go to battery I use windows to save power. Running linux on maximum brightness is pointless i'll get just an hour out of the battery.

I'd really appreciate someone telling me how to edit the kde startup script so I can make it run "fsfn -0"...?

---

### Post by drakeoutlaw on 2006-02-14
just add the line to an executable file called fsfnstart save the file in /home/yourusername/.kde/Autostart

KDE will execute the files in this directory in sequence.

Remember to chmod u+x fsfnstart to make it executable

---

### Post by Zhukov on 2006-02-14
Yeah, ACPI is a problem, at least with my vaio, the battery doesnt last as long as in Windows... :( Oh and the S keys arent working.

---

### Post by fantagol on 2006-03-03
Hi all,
i have some problems with my VAIO VGN_A215Z, and my young Breezy Badger's installation

dmesg show
```

[4300413.539000] Asus ACPI: Error reading brightness
[4300413.539000] Asus ACPI: Error reading LCD status
[4300413.539000] Asus ACPI: Error reading LCD status
[4300413.639000] Asus ACPI: Error reading brightness
[4300413.639000] Asus ACPI: Error reading brightness
[4300413.639000] Asus ACPI: Error reading brightness
[4300413.639000] Asus ACPI: Error reading brightness
[4300413.639000] Asus ACPI: Error reading LCD status
[4300413.639000] Asus ACPI: Error reading LCD status
[4300413.739000] Asus ACPI: Error reading brightness
[4300413.739000] Asus ACPI: Error reading brightness
[4300413.739000] Asus ACPI: Error reading brightness
[4300413.739000] Asus ACPI: Error reading brightness
[4300413.739000] Asus ACPI: Error reading LCD status

```

an kde show me sometimes messages such as
"Display Changed : LCD off", ecc

Please help me, tks

---

### Post by Ferri on 2006-04-02
Thanks for this. Now I'm able to adjust brightness and volume in my Sony Vaio VGN-FS415B.
However, I've struggled trying to make work FN-F7 key (external screen) without success.
Anyone has been successfull?

---

### Post by Ferri on 2006-04-06
Nobody?

---

### Post by drakeoutlaw on 2006-04-07
This may help:


[http://packages.ubuntulinux.org/breezy/utils/i810switch](http://packages.ubuntulinux.org/breezy/utils/i810switch)

I have NOT tried it myself. (never needed extrnal CRT)

---

### Post by Ferri on 2006-04-07
Thanks.
I've had already tryed, but it only enables/disables the external CRT, it's not able to turn off the Vaio screen. I'm not able to set different resolutions in the two screens, although I've not finished with all the suggestions I've found around this forum.
I need an external CRT because I have to give presentations quite often, and I'd prefer to avoid going on translating them to PowerPoint.

---

### Post by drakeoutlaw on 2006-04-08
[QUOTE=Ferri]Thanks.
I've had already tryed, but it only enables/disables the external CRT, it's not able to turn off the Vaio screen. I'm not able to set different resolutions in the two screens, although I've not finished with all the suggestions I've found around this forum.
I need an external CRT because I have to give presentations quite often, and I'd prefer to avoid going on translating them to PowerPoint.[/QUOTE]


I got the following from the i810switch README file:

>>>>Options are self-explaining:

  Usage: i810switch [crt on/off] [lcd on/off]
         or
         i810switch probe

`crt' enables/disables the output to CRT display. 
`lcd' enables/disables the output to LCD.

`probe' displays a register dump of the graphics controller.

With no options, it displays the current output status.
<<<<<<<<

I suppose you've already tried the options. 

Contact the program's author, he has already asked for feedback to help improve its performance. go to : [http://www16.plala.or.jp/mano-a-mano/i810switch.html](http://www16.plala.or.jp/mano-a-mano/i810switch.html)

Good luck

---

### Post by PowerWCRulez on 2006-04-08
HI all, I had the Live CD works FN keys and OSD, so the install CD didn't put the FN key and OSD except the brightness FN Key works good, no OSD :(

My lappy is Sony Vaio PCG-GRZ610.

I need to fix the OSD and FN Keys for Speaker volume, LCD/VGA, LCD/TV and HD Sleep.

Volume control:
FN+F3 Mute
FN+F4 Volume meter and pressing arrow up or down.

Brightness:
FN+F5 and pressing arrow up or down.

LCD/VGA switch:
FN+F7 Toggle/Switcher

LCD/TV Switch:
FN+F8 Toggle/Switcher

HD Sleep:
FN+F12 Toggle

OSD bar color:
White foreground on black

OSD Icon:
Same as Live CD does show icon.

Timer for meter or OSD to disappear: 3 Secs

thanks :)

---

### Post by wildseven on 2006-07-11
> **no1wantdthisname said:**
> Forgot to mention that you need some things.  This is adapted from the gentoo site.  First of all do this:
```
sudo apt-get install libxosd-dev libasound2-dev build-essential linux-headers-$(uname -r)
```

Now get the sony_acpi fix.
```
wget [http://download.berlios.de/fsfn/sony_acpi.tar.gz](http://download.berlios.de/fsfn/sony_acpi.tar.gz)
tar zxvf sony_acpi.tar.gz
cd sony_acpi
```

Now to install it, there are 2 ways.
You could do
```
make && sudo make install
```
Alternatively, you could download checkinstall with 
```
sudo apt-get install checkinstall
```
and then do the same thing as above except for
```
make && sudo checkinstall
```
This will make a .deb file so it's much easier to keep track of things you install.
Small note: .deb files can't have underscores in the package name so you have to rename sony_acpi to sony-acpi and the version number needs to be changed to an actual number.  This also overrides files from the one of the kernel module packages.  So, you can either force install the .deb with
```
sudo dpkg -i --force-overwrite (whateverNameYouGave.deb)
```
or use dpkg-divert to move all the files from the kernel module package out of the way.  There are a lot of packages to move, and if you really needed the old sony_acpi back you can just reinstall the module package.  So whatever.

Either way
```
modprobe sony_acpi
ls /proc/acpi/sony 
```
should show 
```
brightness  brightness_default  fnkey
```

Next:
```
wget http://download.berlios.de/fsfn/fsfn-0.2.tar.gz
tar zxvf fsfn-0.2.tar.gz
cd fsfn-0.2
./configure && make && sudo make install 
```
Again, you can do either sudo make install or sudo checkinstall.

After installing that you can test this by doing:
```
sudo fsfn
fsfn -o
```
You should see a bar at the bottom of your screen when using the fn keys.

Next would be the startup script.  The script from the gentoo site doesn't work so I wrote my own.  This just starts up fsfn.
Attached at bottom.

Make it executable and move the fsfn script to /etc/init.d/
```
chown root:root fsfn.txt && sudo chmod +x fsfn.txt && sudo mv fsfn.txt /etc/init.d/fsfn
```

To start it up on boot
```
sudo update-rc.d fsfn defaults
```

If you want the osd to show up when you change volume/brightness
click the start menu and SYSTEM>PREFERENCES>SESSIONS, click the startup tab and add 
"fsfn -o" with order 50.

heyyy, I am following your instructions and i seem to have ran into an error. at the make && sudo make install i get this error:

make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/wildseven/sony_acpi modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/wildseven/sony_acpi/sony_acpi.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/wildseven/sony_acpi/sony_acpi.o] Error 127
make[1]: *** [_module_/home/wildseven/sony_acpi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2


I am pretty new to linux and i'm not quite sure whats happening here. Please help if you can. Thank you.

---

### Post by sniffass on 2006-07-11
Hi, it maybe that you don't have gcc-3.4 installed which is needed to use the  commands. My advice to you is to ensure it is installed by running the following command:
sudo aptitude install gcc-3.4

after installation you should try running your commands again, let me know if it works.

---

### Post by larytet on 2006-07-21
for  Sony VAIO VGN-S460
sudo apt-get install nvclock 
you get version 0.8b
next step in the /etc/X11/xorg.conf
add line 
```

	Option "HWCursor" "0"

```
i used section screen
after that try
sudo nvclock -S 60%

you do not have to edit xorg.conf, instead  you can run vclock outside of X

to make Fn-F5/Fn-F6 working
file /etc/acpi/sonybright.sh
```

#!/bin/bash

BRIGHTNESS=$(cat /proc/acpi/sony/brightness)

if [ "$BRIGHTNESS" -gt 8 ]; then
        BRIGHTNESS=1
fi

if [ "x$1" = "xdown" ]; then
   if [ "x$BRIGHTNESS" != "x1" ]; then
      BRIGHTNESS=$(( $BRIGHTNESS - 1 ))
      echo $BRIGHTNESS > /proc/acpi/sony/brightness
   else
      [ -x /usr/bin/spicctrl ] && /usr/bin/spicctrl -b 0
   fi
   # Recent nvidia Sonys have ACPI methods that do nothing. Thanks, Sony.
elif [ "x$1" = "xup" ]; then
   if [ "x$BRIGHTNESS" != "x8" ]; then
      BRIGHTNESS=$(( $BRIGHTNESS + 1 ))
      echo $BRIGHTNESS > /proc/acpi/sony/brightness
   fi
else
   echo >&2 Unknown argument $1
fi
   [ -x /usr/bin/nvclock ] && nvclock -S $(( $BRIGHTNESS * 12 )) >/dev/null

```

Update:
nvclock causes segmentation fault in 6.10 when called in the context of acpi - see log file
```

 cat /var/log/acpid

```

```

sudo /etc/acpi/sonybright.sh

```

does the trick
I will try to fix the problem stay tuned ...

---

### Post by no1wantdthisname on 2006-07-21
No need to recompile the sony_acpi module, 2.6.15+ kernels already have it enabled.  At least for dapper anyway.

I guess I'll change the original instructions.
[http://www.ubuntuforums.org/showpost.php?p=487144&postcount=7](http://www.ubuntuforums.org/showpost.php?p=487144&postcount=7)

---

### Post by larytet on 2006-07-21
indeed - sonypi and ACPI are all in
any ideas/links regarding dual monitor for VGN-S460 ?
i tried lot of configuration and nothing. Display settings do not do the trick. 
Another problem is audio - volume control by Fn-F3/F4 keys. i see that in file /etc/acpi/volupbtn.sh there is a call to acpi_fakekey
what acpi_fakekey does ?

---

### Post by sniffass on 2006-07-21
Thanks for the new instructions, great news I don't need to compile and install that sony module, cuts out half the work. I have implemented your new instructions, only problem is the sound volume doesn't seem to adjust normally, sometime I press the fn key to reduce volume but instead the volume jumps up, and vice-versa. It kinda changes randomly. This isn't normal behaviour and it was working perfectly with your old instructions. On breezy and dapper.

---

### Post by no1wantdthisname on 2006-07-21
I haven't experienced that, but you can try making a /etc/fsfn.conf file and experiment with the different variables.

You could also just change the command for f3 to
```
amixer -q sset Front 2+
```
to increase volume, and for f4 to 
```
amixer -q sset Front 2-
```
to decrease volume.

Replace Front with whatever is controlling your volume.

This is also useful for those who experience large jumps in volume.

Do
```
man 5 fsfn
``` for the format of the fsfn.conf file.

---

### Post by sniffass on 2006-07-25
Cheers, then later I noticed I had more than ten fsfn processes running, these must have accumulated when I was trying to follow you instructions and invariably made a mistake. Killing these processes and starting a single one returned the normal behaviour.

---

### Post by G2k on 2006-09-21
I have a Sony Vaio VGN-FS660. I installed the fsfn thingy and it's working well, except for when the screensaver goes on, the brightness goes to the max even though my brightness_default is 4. Does anyone know how I can fix this?
thanks

---

### Post by LaintalAy on 2006-09-23
> **Sebby said:**
> Thanks for your reply. However, I get the same error for events 1 through to 10...

I just don't understand - before I compiled a new kernel, this worked perfectly with no configuration required. Any help would be much appreciated!

You can try creating the node if it doesn't exists, that works for me in Gentoo.

```
mknod /dev/input/event0 c 13 64
```

---

### Post by Zhukov on 2006-09-25
Don't forget to install the headers for your new kernel and then reboot.

---

### Post by blackangel666 on 2006-10-12
Hello!

A few months ago i bought a sony fe21s notebook. yersterday i installed ubuntu dapper drake and i'm really happy about the fact that nearly everthing 
is working. everthing but the possibility to adjust the brightness of the lcd panel. 

is there anyone who can report about how to install the fn keys or is there another way to increase or decrease the brightness.
i've already tried it with smartdimmer and with the scroll bar for brightness adjustment that is integrated in the power management, but no success.

hope you can help me. i would be thankful for every tip.

---

### Post by guitarist549 on 2006-11-10
This worked beautiful with VGN-SZ240... THank you so much.

---

### Post by Zhukov on 2006-11-23
> **blackangel666 said:**
> Hello!

A few months ago i bought a sony fe21s notebook. yersterday i installed ubuntu dapper drake and i'm really happy about the fact that nearly everthing 
is working. everthing but the possibility to adjust the brightness of the lcd panel. 

is there anyone who can report about how to install the fn keys or is there another way to increase or decrease the brightness.
i've already tried it with smartdimmer and with the scroll bar for brightness adjustment that is integrated in the power management, but no success.

hope you can help me. i would be thankful for every tip.

Where exactly do the instructions stop working?
Ill try to "clean up" this how-to tomorrow, if nobody minds :D
No doubt credit will be given to the authors.

---

### Post by timelord726 on 2006-11-26
Hi everyone,

I've attempted to use the solutions in this thread (and the one on the Gentoo Forums) to get my brightness and sound Fn controls working on my Sony Vaio PCG-K15.  I had one tantalizing glimpse of success, and it worked immediately after setting it up for the first time.  However, after restarting, my "fnkeys" file has disappeared from my /proc/acpi/sony and absolutely refuses to come back, and none of the keys work any longer.  I've redone the tutorial and tried many variations many different times but I just can't get it to work anymore.  I know it will if you push it just right though because I saw the results for myself!  Does anyone have any idea what I should do to perhaps clear everything out and try once more completely from scratch?  Or at least what the current problem might be?

Thanks so much!

---

### Post by Zhukov on 2006-11-27
Well, I'll try to do what I proposed. I'll post the instructions that work for ME! Maybe you can try then.

---

### Post by timelord726 on 2006-11-27
> **Zhukov said:**
> Well, I'll try to do what I proposed. I'll post the instructions that work for ME! Maybe you can try then.
Much appreciated, Zhukov, thank you!

---

### Post by nickxs on 2006-11-28
.

---

### Post by Zhukov on 2006-11-29
Done. I made a new thread, I will add the link here as soon as it is approved by the moderator. Credits were given. If anyone disagrees with what I posted just let me know and I will add/delete as requested.

Sorry for the late reply.

---

### Post by Pjotr123 on 2007-03-02
> **Sir Bogoff said:**
> Upon installing Ubuntu 5.10 on my Sony Vaio I discovered that the brightness was really bad. I hunted around for some info but nothing would keep the brightness settings upon reboot. Sure I could go into a terminal and reset it but what a pain in the ****. 

Now, this works on my Vaio PCG-GRX600P in breezy and I would presume other Vaio models but seeing as how I only have the one I can't swear to it. If it works for you, post your result here. If it doesn't, well sorry about your luck but I found this on my own and I am a learner at this.

Step 1.
```
sudo chown system_username /proc/acpi/sony/brightness 
echo "n" > /proc/acpi/sony/brightness 
```
where n is a number between 1 and 8. 
Note that the quotes around the numeric value are required.

1 is the dimmest setting and 8 is the brightest.
Play around until you find the one you prefer but remember it for step 2.
```
sudo chown root /proc/acpi/sony/brightness
``` 

Step 2.
```
sudo chown system_username /proc/acpi/sony/brightness_default
echo "n" > /proc/acpi/sony/brightness_default
```
where n is the same number that you set it to in step 1.
```
sudo chown root /proc/acpi/sony/brightness_default
```
Now try a reboot (you don't have to obviously) to see if the settings stick.

Hope that worked for you.



This worked fine on my Sony Vaio VGN-BX296VP , both in Dapper 6.06 and in Edgy 6.10. Thank you very much for posting this excellent solution to an annoying problem!

Pjotr.

---

### Post by ARGONIQ on 2007-04-24
> **no1wantdthisname said:**
> EDIT: Updated for dapper

First of all do this:
```
sudo apt-get install libasound2-dev build-essential linux-headers-$(uname -r) gcc-3.4
```

If you want the onscreen display then also get
```
sudo apt-get install libxosd-dev 
```

Next:
```
wget http://download.berlios.de/fsfn/fsfn-1.0.tar.gz
tar zxvf fsfn-1.0.tar.gz
cd fsfn-1.0
```

If you want osd:
```
./configure && make && sudo make install 
``` 

No osd:
```
./configure --disable-xosd && make && sudo make install 
``` 

After installing that you can test this by doing:
```
sudo fsfn
```

If you enabled osd:
```
fsfn -o
``` 
You should see a bar at the bottom of your screen when using the fn keys.

Next would be the startup script.  The script from the gentoo site doesn't work so I wrote my own.  This just starts up fsfn.
Attached at bottom.

Make it executable and move the fsfn script to /etc/init.d/
```
chown root:root fsfn.txt && sudo chmod +x fsfn.txt && sudo mv fsfn.txt /etc/init.d/fsfn
```

To start it up on boot
```
sudo update-rc.d fsfn defaults
```

If you want the osd to show up when you change volume/brightness
click the start menu and SYSTEM>PREFERENCES>SESSIONS, click the startup tab and add 
"fsfn -o" with order 50.

This worked very well for me  in 6.10 release... but NOT in 7.04. What can I do in Feisty?

Thx!

---

### Post by zazen666 on 2007-04-24
Dont know if this has been said or not, but with Xubuntu 7.04 I can adjust my VGN-S170P sony viao with applications=> settings manager=> desktop.

---

### Post by Zhukov on 2007-05-02
You can still use the old command. I did an ugly script for it:

#!/bin/bash
# Ugly brightness control toll for Vaios
#
echo "$1" | sudo tee /proc/acpi/sony/brightness
echo "Brightness changed to $1."

---

### Post by schwieb on 2007-05-03
I was having this trouble too, and I figured it out: 

> **swoon said:**
> when i do:
modprobe sony_acpi
ls /proc/acpi/sony/

all it shows is:

brightness  brightness_defaul

why am is it no showing/installing 'fnkey' ?

The problem is that the "make install" process puts the module in:
```
/lib/modules/2.6.20-15-generic/kernel/drivers/acpi/
```

For some (me included) there is already a sony_acpi module in:
```
/lib/modules/2.6.20-15-generic/kernel/ubuntu/acpi/
```

To fix the issue, make sure the module is not loaded:
```
sudo rmmod sony_acpi
```

Then copy your newly compiled module from where ever you ran the make process
```
sudo cp sony_acpi.ko /lib/modules/2.6.20-15-generic/kernel/ubuntu/acpi/
```

Now load the module with:
```
sudo modprobe sony_acpi
```

Test that it is working with:
```
ls /proc/acpi/sony
```

You should now see all three files:
```
brightness brightness_default & fnkey
```

Hope that helps somebody!  It drove me nuts for several days.

---

### Post by jnicholson on 2007-05-16
Hi,

I tried this on my VGN-FS730F (running Kubuntu 7.04) and now I can't boot into my desktop. I can boot in safe mode but that is it. 

Can somebody help, please?:(

---

### Post by jnicholson on 2007-05-16
Hi,

I tried this on my VGN-FS730F (running Kubuntu 7.04) and now I can't boot into my desktop. I can boot in safe mode but that is it. 

Can somebody help, please? :(


>  
Now, this works on my Vaio PCG-GRX600P in breezy and I would presume other Vaio models but seeing as how I only have the one I can't swear to it. If it works for you, post your result here. If it doesn't, well sorry about your luck but I found this on my own and I am a learner at this.

Step 1.
Code:

sudo chown system_username /proc/acpi/sony/brightness 
echo "n" > /proc/acpi/sony/brightness

where n is a number between 1 and 8.
Note that the quotes around the numeric value are required.

1 is the dimmest setting and 8 is the brightest.
Play around until you find the one you prefer but remember it for step 2.
Code:

sudo chown root /proc/acpi/sony/brightness

Step 2.
Code:

sudo chown system_username /proc/acpi/sony/brightness_default
echo "n" > /proc/acpi/sony/brightness_default

where n is the same number that you set it to in step 1.
Code:

sudo chown root /proc/acpi/sony/brightness_default

Now try a reboot (you don't have to obviously) to see if the settings stick.

Hope that worked for you.


---

### Post by Zhukov on 2007-05-16
Well, thats at least odd, since I don't believe this is doing anything to your X configuration, nevertheless, can you provide us some output?

Best regards!

---

### Post by jnicholson on 2007-05-17
It was giving me the "no screens" error (only when I tried startx in recovery mode, else it would just pretty much freeze).

I decided to just start from scratch so I installed Kubuntu again,and the first thing I did was try to make the screen less bright and funnily enough it worked. Oh well... any ideas?

---

### Post by fantastic_id on 2007-05-28
I am using SONY FJ. With about half hour's reading of this thread, the fsfn works great on my machine.

I mainly took ideas from 3 posts of No1wantdthisname and Sir Bogoff on page 1 and  Pijalu's #62.

/etc/fsfn.conf should be manually created and I only added two lines:
ALSA_NAME=PCM
BRT_HACK_FJS=6

Thank you for your everyones' endeavour and help! That's the most happy thing I met today ,hah!

---

### Post by cricketer on 2007-09-06
I have a Sony Vaio laptop model PCG-V505 and Ubuntu Feisty Fawn installed. I had the same problem adjusting the brightness using the Fn key. However, by trial and error I solved the problem!

For users who have thisSony model, try this:

Press the Fn key and at the same time press F5 key to decrease or F6 to increase the brightness.

This may work for other Vaio models as well. Try it and post your experiences here!

---

### Post by zamurai on 2007-10-24
Hi,


I'm using FS25GP and just installed 7.10, and I've already tried all the steps provided. Not getting anything. Please help.

and when I do:
ls /proc/acpi/sony/


There is no such file or directory. 



The default brightness is so damn bright. :(

---

### Post by howlsmoving on 2007-10-26
> **zamurai said:**
> Hi,
I'm using FS25GP and just installed 7.10, and I've already tried all the steps provided. Not getting anything. Please help.
and when I do:
ls /proc/acpi/sony/
There is no such file or directory. 
The default brightness is so damn bright. :(

This fix has changed for Gutsy, but I was able to make it work.
First, make sure that the sony-laptop module is loaded.  The easiest way to do this is to type: 

sudo modprobe sony-laptop
(this loads the module if it wasn't loaded, or it should return an error if it is)

Now, Issue the next command, its the same command as before, it just uses a different directory.  "your_user" is whatever account you need to use to control brightness.

sudo chown your_user /sys/class/backlight/sony/brightness

Finally use the next command to set it the lowest level brightness level.  To change it to other levels, simply change the number to anything between 1 and 8:

echo 1 > /sys/class/backlight/sony/brightness

Hope this helps.

---

### Post by pijalu on 2007-12-01
Hi,

For anyone interested, I made a few days ago a package for 7.10 of fsfn 2.0 [the current svn trunk that supports sony_laptop]

You can find it here:
[http://users.skynet.be/muaddib/ubuntu/fsfn_2.0-0ubuntu1_i386.deb](http://users.skynet.be/muaddib/ubuntu/fsfn_2.0-0ubuntu1_i386.deb)
Btw, first time I play with Debian packaging so I may have screwed the dependencies.... but it seems to work on my old Sony ;-)
(And since I have no clue how to install a service/config files on it via deb, it's not part of it either...)

---

### Post by 4nT0 on 2007-12-07
> **howlsmoving said:**
> sudo chown your_user /sys/class/backlight/sony/brightness


I have a FZ21S. I loaded sony-laptop module, but my directory /sys/class/backlight/ is empty.

How can I solve?

Thanks.

---

### Post by vins32 on 2007-12-11
Same problem on a FZ11S. Any ideas?

thanks!

---

### Post by jonnyalpha on 2007-12-12
> **pijalu said:**
> Hi,

For anyone interested, I made a few days ago a package for 7.10 of fsfn 2.0 [the current svn trunk that supports sony_laptop]

You can find it here:
[http://users.skynet.be/muaddib/ubuntu/fsfn_2.0-0ubuntu1_i386.deb](http://users.skynet.be/muaddib/ubuntu/fsfn_2.0-0ubuntu1_i386.deb)
Btw, first time I play with Debian packaging so I may have screwed the dependencies.... but it seems to work on my old Sony ;-)
(And since I have no clue how to install a service/config files on it via deb, it's not part of it either...)

Any feedback on the above deb?

---

### Post by rosegarden78 on 2008-01-19
Try typing the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

### Post by 4nT0 on 2008-01-19
It's a pity that doesn't influence battery usage... :\

---

### Post by lp1912 on 2008-01-21
> **jonnyalpha said:**
> Any feedback on the above deb?

Did not work for me :(
Vaio VGN-C190G

---

### Post by Daniel83BG on 2008-02-11
> **pijalu said:**
> Hi,

For anyone interested, I made a few days ago a package for 7.10 of fsfn 2.0 [the current svn trunk that supports sony_laptop]

You can find it here:
[http://users.skynet.be/muaddib/ubuntu/fsfn_2.0-0ubuntu1_i386.deb](http://users.skynet.be/muaddib/ubuntu/fsfn_2.0-0ubuntu1_i386.deb)
Btw, first time I play with Debian packaging so I may have screwed the dependencies.... but it seems to work on my old Sony ;-)
(And since I have no clue how to install a service/config files on it via deb, it's not part of it either...)


Thanks mate... it is working perfect on my Sony Vaio FS630.

---

### Post by damneddark on 2008-02-20
> **howlsmoving said:**
> This fix has changed for Gutsy, but I was able to make it work.
First, make sure that the sony-laptop module is loaded.  The easiest way to do this is to type: 

sudo modprobe sony-laptop
(this loads the module if it wasn't loaded, or it should return an error if it is)

Now, Issue the next command, its the same command as before, it just uses a different directory.  "your_user" is whatever account you need to use to control brightness.

sudo chown your_user /sys/class/backlight/sony/brightness

Finally use the next command to set it the lowest level brightness level.  To change it to other levels, simply change the number to anything between 1 and 8:

echo 1 > /sys/class/backlight/sony/brightness

Hope this helps.

Thanks this worked for me :-) Sony Vaio VGN CR14GN

i <3 ubuntu again

damn my eyes hurt now :(

---

### Post by wieman01 on 2008-04-04
> **howlsmoving said:**
> This fix has changed for Gutsy, but I was able to make it work.
First, make sure that the sony-laptop module is loaded.  The easiest way to do this is to type: 

sudo modprobe sony-laptop
(this loads the module if it wasn't loaded, or it should return an error if it is)

Now, Issue the next command, its the same command as before, it just uses a different directory.  "your_user" is whatever account you need to use to control brightness.

sudo chown your_user /sys/class/backlight/sony/brightness

Finally use the next command to set it the lowest level brightness level.  To change it to other levels, simply change the number to anything between 1 and 8:

echo 1 > /sys/class/backlight/sony/brightness

Hope this helps.
What if module "sony-laptop" cannot be found? That's strange.

On Kubuntu Gutsy that is. :confused:

---

### Post by bhi24 on 2008-08-07
hi all,
i tried this fix on my VGN NR260E, but no success.
there is no /sys/class/backlight/sony/brightness  in my machine, but i have /sys/class/backlight/acpi_video0/brightness.
i did 

echo 1 > /sys/class/backlight/acpi_video0/brightness 

but from what i can tell, nothing has changed.
here's hoping that future versions of ubuntu fixes this important problem!
(i have used gutsy 7.10, and now upgraded to hardy heron, but no luck so far).

thanks for any suggestions though!:confused:

---

### Post by chrisreichel on 2008-09-07
I am almost giving up from  8.04 (hardy heron).

I tried everything to make the brightness control works on my Vaio VGN-FZ430E. Nothing works.


Theres no sony_acpi modeul, no /proc/whatever/sony ... the LCD brightness control in gnome panel, doesn't work.

Does any have a last clue, before I get to vista (unfortunately I need the battery) or get blind.. lol.

Thanks mates!

---

### Post by matts12290 on 2008-09-16
I have an FZ series Vaio also.  I really want to increase the battery life so I am able to use it as a laptop!!

---

### Post by simo415 on 2008-09-21
I've an vgn-sz and i try anything to fix the brightness, but don't works.
Someone can help me?

---

### Post by crl on 2008-10-02
> Quote:
Originally Posted by howlsmoving View Post
This fix has changed for Gutsy, but I was able to make it work.
First, make sure that the sony-laptop module is loaded. The easiest way to do this is to type:

sudo modprobe sony-laptop
(this loads the module if it wasn't loaded, or it should return an error if it is)

Now, Issue the next command, its the same command as before, it just uses a different directory. "your_user" is whatever account you need to use to control brightness.

sudo chown your_user /sys/class/backlight/sony/brightness

Finally use the next command to set it the lowest level brightness level. To change it to other levels, simply change the number to anything between 1 and 8:

echo 1 > /sys/class/backlight/sony/brightness

Hope this helps.

This did`nt work for me.
I have a Sony VAIO CR31 with ubuntu 8.04. 
I adjusted the backlight /brightness by writing

sudo nano /sys/class/backlight/sony/brightness

change the number between 1-7 and save the file.

This worked great for me:D

---

### Post by Kuroyume on 2008-10-02
i have a vgn-c240fe and the brightness panel applet works for me on an up to date 8.04.1.

However, it all goes crazy when working on battery.

---

### Post by kiloxxx on 2008-10-17
> i have a vgn-c240fe and the brightness panel applet works for me on an up to date 8.04.1.

However, it all goes crazy when working on battery. 

Try this: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/213128]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/213128")

It may help with the battery problem. In my case, vgn-fz11z, it has worked.

---

### Post by Beetzart on 2008-10-19
> **pijalu said:**
> 
```

cat /proc/acpi/sony/brightness
cat /proc/acpi/sony/brightness_default
echo 4 >> /proc/acpi/sony/brightness
cat /proc/acpi/sony/brightness
cat /proc/acpi/sony/brightness_default

```

Without help, I won't be able to do anything

I had the same problem when I just installed Linux Ubuntu on my VAIO PCG-7M1M and tried the figure it out step by step through this forum. The problem is (I guess), I can get to /proc/acpi, but there is no sony map to find.

---

### Post by frank17next on 2008-11-16
RESOLVED:

Hi,
I've posted the solution on my website: [http://www.frank17.it/linux/fz18m.htm]("http://www.frank17.it/linux/fz18m.htm") from [http://www.linux-on-laptops.com]("http://www.linux-on-laptops.com/")
(In Italian language, i'm Italian)
See ya!

---

### Post by munit5000 on 2008-12-05
How do I install sony_laptop? It isn't even on any repositories anymore! Someone, I need help setting up my Vaio VGN-290 backlight to work!

---

### Post by the_fury on 2008-12-05
> **no1wantdthisname said:**
> Er, not sure, what model do you have?  This applies only to FS series.  For example, I have a Vaio VGN-FS640/W.

You might have to do a 
```
sudo rmmod sony_acpi
```
beforehand as well.

That doesn't work for me either. I get:

```
thefury@Upstairs-Laptop:~$ sudo modprobe sony_acpi
FATAL: Module sony_acpi not found. 
```

I'm running a Sony VAIO VGN-FZ240e

---

### Post by munit5000 on 2008-12-05
When i do modprobe sony_acpi, it tells me that it cannot find sony_acpi module

---

### Post by hihihi on 2008-12-08
> **frank17next said:**
> RESOLVED:

Hi,
I've posted the solution on my website: [http://www.frank17.it/linux/fz18m.htm]("http://www.frank17.it/linux/fz18m.htm") from [http://www.linux-on-laptops.com]("http://www.linux-on-laptops.com/")
(In Italian language, i'm Italian)
See ya!



thank you very much, i can report gladly, that brightnes is reallly working on my VAIO FZ31M,
i translated your how to into english here:
[http://ubuntuforums.org/showthread.p...+FZ+brightness](http://ubuntuforums.org/showthread.p...+FZ+brightness)

---

### Post by rohitgupta on 2009-01-29
I am using Sony Vaio FJ series laptop.
My problem is I am still not able to configure how to use volume control and Brightness control through Function keys

---

### Post by magic-neophyte on 2009-01-31
This thread helped me. Thanks to all contributors and the author.

m-n

---

### Post by blakecraw on 2009-02-11
I have a sony vgn-fe790, with everything working except the screen actually dimming.

The fn keys work, in so far as the little brightness indicator pops up on the screen, and the /sys/class/backlight/sony/brightness file does get modified when I press the fn keys, but the brightness does not change.

Ideas?

---

### Post by matts12290 on 2009-03-02
Get the latest version of Ubuntu (8.10).  I am able to get everything working!  Multimedia buttons, function keys, brightness, volume control... I have a Vaio VGN-FZ4000.  If you are having trouble with the brightness (when I would do FN+F5 it would show the brightness should be going down but didn't) follow this page: [http://ubuntuforums.org/showthread.php?t=1004568&highlight=vaio+brightness](http://ubuntuforums.org/showthread.php?t=1004568&highlight=vaio+brightness)

Let me know if you are still having trouble and I can try to help.

---

### Post by steve101101 on 2009-04-06
this works out of the box when you install 9.04

---

### Post by bobman on 2009-04-09
Thank you for listing the fn button + the button to change lighting

I never thought about using function buttons on my IBM Thinkpad T30

I manually changed my brightness by editing my
 

/proc/acpi/ibm/brightness by typing:
sudo pico /proc/acpi/ibm/brightness 
then i changed the level from 5 to 7, which is the highest for a t30.

Anyways, I tried to sudo gedit the file, but it kept displaying blank
By using:  cat brightness, I could tell there was something in the file, but I had to use pico to edit it

---

### Post by hadocon on 2009-04-25
> **steve101101 said:**
> this works out of the box when you install 9.04

Unfortunately brightness controls do not automatically work in 9.04 on the new Vaio P netbooks.  With the small battery on these units getting brightness control will really help.

Anyone have ideas?

---

### Post by wilfredtee on 2009-05-04
I'm having the same problem on 9.04 Jaunty

Fn+brightness keys trigger the on screen tooltip, but the screen brightness does not change, the bar keeps resetting to 0 everytime i try to increase brightness.

this feature is confirmed to work on 8.04 LTS.

:confused: I wonder what broke this, what other information would be helpful here in this thread?

---

### Post by Hunnamus on 2009-10-19
I just installed Kubuntu 9.04 on my Vaio VGN-CS212. I found a little program from synaptic package manager named smartdimmer. My laptop had installed it automatically. Try running smartdimmer on terminal. This is what I got:

NVClock SmartDimmer adjustment tool version 0.8b4.

Usage: smartdimmer [OPTION]...

Options:
        -g  --get               Query brightness level.
        -s  --set <level>       Set brightness level (15-100)
        -i  --increase          Increase brightness with one level.
        -d  --decrease          Decrease brightness with one level.
        -h  --help              Prints this help text.

It was quite shocking to find this easy way to dim my laptop screen after four hours of exploring. Hope this helps you. At least it should be helpful for new releases of ubuntu and kubuntu.

---

### Post by mnial on 2009-10-20
so does this work in Ubuntu?

ps I'm sorry, I just can't check it myself right now...

---

