---
title: "HOWTO: Running a Tascam US-122 in Dapper"
date: 2006-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by SFN on 2006-06-11
This is simply a rewrite of a HOWTO I did for getting a US-122 to work on Hoary. Very little has changed except for versions of packages being installed.

I should add that I did the [Ubuntu Studio]("http://ubuntustudio.com/wiki/index.php") setup before doing any of this. If you actually have use for a US-122, you probably have use for many of the other pieces of Ubuntu Studio.

First, do
```
sudo apt-get install fxload alsa-base alsa-firmware-loaders alsa-tools alsa-tools-gui alsa-utils alsamixergui alien

```
Next, get an RPM of alsa-firmware and install it via alien. The one listed here was done for OpenSuSE.

Do 
```
wget ftp://chuck.ucs.indiana.edu/pub/array2/linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch/alsa-firmware-1.0.9-4.noarch.rpm

```
then, get to the location where you downloaded the RPM and do
```
sudo alien --to-deb alsa-firmware-1.0.9-4.noarch.rpm
```
and
```
sudo dpkg -i alsa-firmware_1.0.9-5_all.deb
```
*(the above is not a typo. The RPM is 1.0.9-4 but the DEB created by alien is 1.0.9-5*)

Once your deb is installed, do
```
wget http://langerland.de/linux/usx2y/usx2y-fw-0.1b.tar.bz2
```
and extract it. Then do
```
lsusb
```
and make note of the bus and device. In my case, I got:
> Bus 002 Device 003: ID 1604:8006 Tascam US-122 Audio/Midi Interface
Now do
```
sudo fxload -s /path/to/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/002/003
```
/path/to/ represents the location of your ld2-ezusb.hex file. It was in the archive you downloaded from langerland.de. The /002/003 comes from the lsusb results. 002 = Bus. 003 = Device

Finally, do
```
sudo usx2yloader
```
The lights on the US-122 should come on. If you do
```
cat /proc/asound/cards
```
you will see something like
> 
0 [Live ]: EMU10K1 - Sound Blaster Live!
Sound Blaster Live! (rev.10) at 0xd000, irq 18
1 [USX2Y ]: USB US-X2Y - TASCAM US-X2Y
TASCAM US-X2Y (1604:8007 if 0 at 001/006)
If you already had a sound card(s) installed, as I did, your USB card will be the last in the list.

Should you reboot or disconnect the device, you'll need to do
```
sudo usx2yloader
```
again to initialize the card.

You could even have usx2yloader run on startup, if the card was attached all the time.

Hope this helps.

---

### Post by passonno on 2006-06-12
I am going to try this very soon, but I do have a question:

Do I need to uninstall the old Alsa version before I do this?

---

### Post by SFN on 2006-06-12
You shouldn't have to. I didn't.

---

### Post by passonno on 2006-06-13
Ok, I have it working now, but

each time I disconnect it, i have to load the firmware with fxload, per the example, to get it back working again.

What have I done wrong?  How can I make it autostart, or at least just allow me to run usx2yloader to start it manually?

---

### Post by SFN on 2006-06-13
[QUOTE=passonno]Ok, I have it working now, but

each time I disconnect it, i have to load the firmware with fxload, per the example, to get it back working again.

What have I done wrong?  How can I make it autostart, or at least just allow me to run usx2yloader to start it manually?[/QUOTE]

This part

[QUOTE=SFN]Should you reboot or disconnect the device, you'll need to do
Code:

```
sudo usx2yloader
```

again to initialize the card.

You could even have usx2yloader run on startup, if the card was attached all the time.[/QUOTE]

covers that.

I'm not at my Ubuntu machine right now but essentially, in Gnome click System -> Preferences -> Sessions -> Startup Programs. Click Add and "sudo usx2yloader" in for the program you wish to run, then click OK.

You could also create a startup script usx2yloader. If someone has more info on this or some better way to make this happen, feel free to post it and I will add it to the HOWTO.

Personally, I don't want my US-122 to load up automatically as it's not always connected to the computer.

---

### Post by passonno on 2006-06-13
That's the problem, though.  

When I unplug the us122 from the machine, and then plug it in again, I have to run the fxload command EACH TIME, and then run usx2yloader.

It's not terribly annoying, but it's not terribly convenient either.

---

### Post by SFN on 2006-06-13
[QUOTE=passonno]When I unplug the us122 from the machine, and then plug it in again, I have to run the fxload command EACH TIME, and then run usx2yloader.[/QUOTE]

Ahh, OK. I see what you're saying.

To make matters worse, the Device ID changes every time you plug the US-122 in. Only when you unplug and plug back in though. Rebooting doesn't seem to affect it.

Hmm. I'll play with this and see what I can come up with.

---

### Post by Ivhassel on 2006-06-14
First of all, thanks for the howto.
I got my card working in dapper, but I installed it a bit different. You might want to compare it, so I'm adding my 2 cents.


[QUOTE=passonno]That's the problem, though.  

When I unplug the us122 from the machine, and then plug it in again, I have to run the fxload command EACH TIME, and then run usx2yloader.

It's not terribly annoying, but it's not terribly convenient either.[/QUOTE]

I installed my Tascam US-122 in a different way, and I don't have this problem.

- Install the alsa packges from the dapper repositories.
```

sudo apt-get alsa-base alsa-firmware-loaders alsa-oss alsa-tools alsa-utils alsamixergui fxload


```
- Grab the firmware of [http://www.alsa-project.org/](http://www.alsa-project.org/) : [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.10.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.10.tar.bz2)
Extract, and copy the firmware to /usr/share/alsa/firmware/usx2yloader:
*note: the first dir in the next command is the directory that contains the firmware drivers from the package you extracted, ie us122fw.ihx, ...*
```

sudo cp ~/alsa_temp/firmware/usx2yloader /usr/share/alsa/firmware/usx2yloader

```

My /usr/share/alsa/firmware/usx2yloader shows:
```

ingmar@ingmar-laptop:~$ ls /usr/share/alsa/firmware/usx2yloader
an2131.asm  tascam_loader.asm  us122.conf   us122.prepad
README      tascam_loader.ihx  us122fw.ihx  us122.rbt

```
So these are, afaik, the only files you need to add, if you install alsa from the repositories.

---

### Post by SFN on 2006-06-14
I was just about to link to [this]("http://ubuntuforums.org/showthread.php?t=168221") which would solve his problem but your solution seems cleaner. However, I want to verify that it solves his problem.

I don't have the problem when I reboot. It starts up correctly. But when unplugging the US-122 then plugging it back in, the device ID changes. As a matter of fact, unplugging any USB device then plugging it back in causes the device ID to change.

Do you not have that problem?

I'll update the HOWTo with whichever way works best, once we've got it nailed down.

---

### Post by passonno on 2006-06-15
Thanks for the help,

I have not had the chance to try it out yet, but I definitely will and I will report back soon with my results.

---

### Post by martintfd on 2006-06-22
I'm having trouble getting my TASCAM US-122 working correctly under dapper.  I've followed all the steps and the packages install fine, when I try to run usx2yloader, get the error message below. Interestingly, every time I update the firmware with fxload the Tascam accupies the next device number.  So if it's at Bus 006 and Device 007 and I run:
```
sudo fxload -s /home/martin/us122/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/006/007
```
```
lsusb
```
I get:
```
Bus 006 Device 008: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 006 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 006 Device 003: ID 1058:0403 Western Digital Technologies, Inc.
Bus 006 Device 002: ID 050d:0237 Belkin Components
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
```

Does anyone else see this?

ps Being unable to use this card in linux is the last thing stopping me from deleting my evil Windows partition!  Below is the error I get from usx2yloader.

```
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:1
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:2
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:3
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:4
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:5
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:6
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:7
usx2yloader: no US-X2Y-compatible cards found
```

---

### Post by passonno on 2006-06-22
Hey Martin, 

I am having the same problem.  

I cannot check it now, as I am away from home, but you should pm me with any updates/solutions.

---

### Post by kurisutofaa on 2006-06-22
Thank you! :D

---

### Post by kurisutofaa on 2006-06-23
errr... It first worked for me, as you can see in my previous post. The light came up and everything seemed to work fine. I didnt really test anything if it really worked, But after reboot I get the same error from usx2yloader as others seem to get. I think this is due to installing alsadrivers and using them. When usx2yloader worked for me, i wasnt using alsa to playback sound on my system. At least this is my theory. Not a clue if its right :). Well I'll also try to find a way to get this thing working.

---

### Post by martintfd on 2006-06-24
[QUOTE=kurisutofaa]errr... It first worked for me, as you can see in my previous post. The light came up and everything seemed to work fine. I didnt really test anything if it really worked, But after reboot I get the same error from usx2yloader as others seem to get. I think this is due to installing alsadrivers and using them. When usx2yloader worked for me, i wasnt using alsa to playback sound on my system. At least this is my theory. Not a clue if its right :). Well I'll also try to find a way to get this thing working.[/QUOTE]

I should also mention I get exactly the same thing as you, ie the first time I ran through the steps the lights came on with no error messages. I couldn't get any sound out of the thing (which could be a seperate issue with gnome or somthing) and so rebooted (I was out of ideas!). After that the lights never came on again with usx2yloader and I got the error message...

I think we need to establish why it works on SFN's setup but not everyones. SFN you mentioned that you did the Ubuntu studio setup first (I did not do this) could you go into more detail, did you just install extra packages or did you you patch the kernal also?

---

### Post by SFN on 2006-06-26
> **martintfd]I think we need to establish why it works on SFN's setup but not everyones. SFN you mentioned that you did the Ubuntu studio setup first (I did not do this) could you go into more detail, did you just install extra packages or did you you patch the kernal also?[/QUOTE]

I did the Vanilla Kernel Patch mentioned [here]("http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption"), the added in Real Tme Support.

I just want to verify something. I mentioned it before but I think I could have been clearer.

I experience the same problems that everyone is having if I just unplug the card then plug it back in. This is due to the original device ID not being reassigned when I plug in. If I have the same things plugged in every time I boot up, I don said:**
> Bus 003 Device 004: ID 05dc:b022 Lexar Media, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 050d:0805 Belkin Components Nostromo N50 GamePad
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 002 Device 001: ID 0000:0000


If I plugin the US-122 and do "lsusb" again, I get

> Bus 003 Device 004: ID 05dc:b022 Lexar Media, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 050d:0805 Belkin Components Nostromo N50 GamePad
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 002 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 002 Device 001: ID 0000:0000


The US-122 always gets Device 003. Now if I unplug the US-122 and plug it back in, I get

> Bus 003 Device 004: ID 05dc:b022 Lexar Media, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 050d:0805 Belkin Components Nostromo N50 GamePad
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 004: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 002 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 002 Device 001: ID 0000:0000


From what limited knowledge I have, this is just the way udev works by default. But I could create udev rules to make sure that the US-122 always gets Device 003. I haven't done this yet because I always shut down my computer and unplug the US-122 when I'm done.

I would think that would be the only reason that I don't seem to have the same problem as most others do. Writing the udev rules should fix that. [Here]("http://ubuntuforums.org/showthread.php?t=168221") is the info for doing that.

---

### Post by martintfd on 2006-06-28
Ok so just to report back I think I my have a solution to our problems with usx2yloader.  I'll start at the begining...I reinstalled dapper just to make sure I hadn't broken alsa with all my messing about.  I then followed SFN's steps and tried booting with the card unplugged and then plugged it in only after it had booted to ensure that the Bus and Device numbers were identical from when it works (ie the first time you run through the steps) to when it doesn't work (after the first time you reboot after running through the steps).  Dispite all the Bus and Device numbers being the same everytime I rebooted I got exaclty the same problem as before.

So then I went fishing and found the following:
[https://launchpad.net/distros/ubuntu/+source/alsa-tools/+bug/45880](https://launchpad.net/distros/ubuntu/+source/alsa-tools/+bug/45880)

I don't understand much of it but I basically interpreted this page as the following: Make a file called /etc/udev/rules/56-tascam.rules and fill it with the text:

```
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /home/martin/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"
```

And don't forget the /home/martin/usx2y-fw-0.1b/ bit needs to be changed to point to wherever your d2-ezusb.hex file is.  Since doing this the lights have come on every time I connect and disconnect! However I still can't get any sound out of the device from Rhythembox in Gnome or Audacity, does anyone know what I need to do now to make the hardware talk to applications?

---

### Post by passonno on 2006-07-03
So the udev rules works likes a charm.  

I don't remember right off hand about making it work with certain apps, but rhythmbox seemed to be a problem.

the only other problem is a small inconvenience:

Sometimes I need to unplug the us122 from usb for one reason or another: the udev rule works fine if I boot with it plugged in, but if I unplug it, it still moves it up one in the usb bus.


What would be cool is if someone with killer bash scripting ability were to figure out a script to do the following:

prompt the user for the location of the us122 on the usb bus, then run the fxload command with the users input.

Does that make sense?  

Could this be done?

anthony

---

### Post by martintfd on 2006-07-10
I managed to solve the problem of the card not talking to applications, for some reason it didn't like being plugged into via an external usb hub and as soon as I plugged it in directly it starting working correctly!

passonno - I don't quite understand your question, if you change the udev rules then (from my limited experience) it doesn't matter how many times or when you plug it in it should just work.

Right I'm off to delete my Windows partition finally!

---

### Post by passonno on 2006-07-15
Hey Martin,

Essentially, what happens is this:

For the sake of argument, let's say that my computer is up and the us122 is running with the udev rule set, when it is plugged in, it will always get put on /proc/bus/usb/003/002, then is iterated to 003/003 with the fxload command.  However, if I then unplug it, then plug it back in, it for some reason gets put at 003/004, thus making my alias for fxload useless, unless I reboot, then the udev rule goes back into effect.

Does that make sense?

---

### Post by SFN on 2006-07-19
> **passonno said:**
> For the sake of argument, let's say that my computer is up and the us122 is running with the udev rule set, when it is plugged in, it will always get put on /proc/bus/usb/003/002, then is iterated to 003/003 with the fxload command.  However, if I then unplug it, then plug it back in, it for some reason gets put at 003/004, thus making my alias for fxload useless, unless I reboot, then the udev rule goes back into effect.

Does that make sense?

This is the only thing that's keeping me from updating the thread with the udev instructions. If that's the case, it's the same situation I had without messing with udev rules.

I'm not seeing this at all. Can anybody else verify that this is happening? Not that I don't believe you. Just need to figure out why it's happening to some and not others.

---

### Post by martintfd on 2006-07-21
I think I know what you are saying passonno but if you look at the code below it does not use the bus or device number it just looks for a device with idProduct 8006 and a idVendor of 1604.  Could you check that this is the case by looking at the last two numbers that come after ID for the TASCAM when you type lsusb (before you load any firmware etc)?

```
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /home/martin/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"
```

---

### Post by passonno on 2006-07-22
Here you go:

Bus 003 Device 002: ID 1604:8006 Tascam US-122 Audio/Midi Interface (without fw)

---

### Post by martintfd on 2006-07-23
Ok this is good, so when you add the udev rules file what should happen is the device will get spotted when it's plugged in and the firmware should be loaded.  When this is done the idProduct will change from 8006  to 8007 and the second rule will kick in and run usx2yloader.  There shouldn't be any need to specify the bus or device number and it should all happen automatically.  

You could try just adding just the first rule to check if that works ok.  Then if the idProduct changes correctly when it's plugged in add the second rule and let me know if you get any errors...

---

### Post by BIGtrouble77 on 2006-07-28
Has any one gotten jack to work with the us-122?  If yes, can you post your Jack Audio Connection Kit settings?  I can get sound in Ardour, but it's super slow motion sound.  I can't get it to playabck properly.

BTW, I appreciate this howto. 

Thanks,
-BT

---

### Post by BIGtrouble77 on 2006-08-09
I'm really hoping someone can help me out here.  I had my us-122 working perfectly last weeek after following the info posted in this thread.  Fastforward a week and I've had to reformat my machine...  

Unfortunately now I cannot get the us-122 to work.  Doing the lsusb does show the device exists.  The fxload command goes through, but the us-122 doesn't light up like it used to.  Doing sudo usx2yloader always resulted in an error, even when the card worked.  The tascam card does show up in the system->preferences->sound and it sticks when I select it, but I get no sound and amarok says there's problems with the alsa xine engine.  The tascam does not show up in the gnome volume applet.  When I had the card working it did show up there.

I have a feeling there's a package I need to install that I previously had, I just have no idea what it is.  Any suggestions?

TIA,
-BT

---

### Post by hulst on 2006-08-12
Hi,

I did not follow the entire thread, but I got mine working flawless with:
```

BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

```

---

### Post by BIGtrouble77 on 2006-08-13
Hulst, can you explain your code a little further?  I don't know how to execute that code.  The first thread basically outlines what I've done to this point.

---

### Post by hulst on 2006-08-13
Put the lines in /etc/udev/rules.d/55-tascam.rules and your set to go.

---

### Post by BIGtrouble77 on 2006-08-13
Hulst,
Thank you so much!!!  My us-122 works amazing now.  It works perfectly on boot so I don't have to type any commands to get it working and the leds work correctly now.  Before, when I did have it working, I had sound but the leds were problematic and typing the command everytime was a pain.

I had nearly lost all hope, thanks again.  You made my week.

-BT

---

### Post by hulst on 2006-08-14
:mrgreen: 

You're welcome

---

### Post by yeehawjared on 2006-08-25
best howto I've read on these forums so far.  Now I need to get Guitar Rig 2 working :)

---

### Post by minreelbayron on 2006-09-01
can someone help me out here.
this is where i KEEP getting stuck:

michaelbeijer@xubuntu:~$ sudo fxload -s /home/michaelbeijer/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/001/002
[B]/proc/bus/usb/001/002: No such file or directory
[/B]
what the **** does this mean?
lsusb gives me:

michaelbeijer@xubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 1241:1603 Belkin
Bus 001 Device 001: ID 0000:0000
Bus 001 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 004: ID 056a:00b1 Wacom Co., Ltd
**Bus 001 Device 002: ID 1604:8006 Tascam US-122 Audio/Midi Interface (without fw)**

so why am i told that '/proc/bus/usb/001/002' doesn't exist? i can't get past this step! and i need my Tascam to play my studio monitors! any hints...?

---

### Post by cremisi on 2006-09-07
> **martintfd said:**
> 

```
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:1
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:2
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:3
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:4
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:5
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:6
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:7
usx2yloader: no US-X2Y-compatible cards found
```

I'm still blocked at this step. Just don't know what to try. Please, any suggest?? :confused:

---

### Post by martintfd on 2006-09-11
First of all try what I did on post 17, if it doesn't make sense let me know and I'll write out a proper walkthrough...

---

### Post by San10 on 2006-09-11
Hi, the installation went fine til
the 'sudo usx2yloader' command.
When I type that, I get the output:

> ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:1
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:2
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:3
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:4
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:5
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:6
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:7
usx2yloader: no US-X2Y-compatible cards found

And the last line of this output I don't get,
because when I type the 'lsusb' command I can see my US 122 listed.

Any help appreciated.
Thanks, ;) Sanne

---

### Post by cremisi on 2006-09-14
> **martintfd said:**
> First of all try what I did on post 17, if it doesn't make sense let me know and I'll write out a proper walkthrough...

GREAT!! I just made an error in editing that file. Following your instructions all seems to work properly. 
I'm going recording :D

---

### Post by gergtreble on 2007-02-09
Is this guide good for installing in Edgy too? If I can get my US -122 working I can finaly ditch windows.

Thanks

---

### Post by jonobo on 2007-02-12
For Edgy try this one (no major changes if i see it right):
[https://help.ubuntu.com/community/TASCAM_US-122#head-b1eaf5e95be3998a41e9de3f88cfc809648ba15c](https://help.ubuntu.com/community/TASCAM_US-122#head-b1eaf5e95be3998a41e9de3f88cfc809648ba15c)

Oops - that is the same but in a different place - it is written by SFM too.

Worked well on my Edgy (still have to do some fine-tuning).

---

### Post by forcesofhabit on 2007-02-16
The link to the RPM no longer works...

---

### Post by drf_av on 2007-03-09
Hi, I've tried today to install my us-122, I've done everything as described, but when I issue sudo usx2yloader I get the message "usx2yloader: no US-X2Y-compatible cards found"
The strange thing is, before doing fxload my lsusb looked like this:
Bus 004 Device 002: ID 1604:8006 Tascam US-122 Audio/Midi Interface (without fw)
After fxload, it looks like this:
Bus 004 Device 003: ID 1604:8007 Tascam US-122 Audio/Midi Interface

Each time I retry, Device increases. It has the same behaviour on 64Studio, do you think it is motherboard-related?

[EDIT]Sorry, didn't read through the thread. But, after adding udev rules, things doesn't change, I'm still stuck and leds doesn't lit up. Any hints?[/EDIT]

---

### Post by purplecar on 2007-03-21
First off thanks for this HOW TO.  I've got my US-122 running on Feisty but the sound is sort off crackly.  I've only been using Linux for a week and a half and I have been using Windows to run my sound apps.  Sound Design is my job so any help with this would be great.  I need to purge Windows....
thanks....

---

### Post by pliktrologos on 2007-04-07
> **drf_av said:**
> Hi, I've tried today to install my us-122, I've done everything as described, but when I issue sudo usx2yloader I get the message "usx2yloader: no US-X2Y-compatible cards found"
The strange thing is, before doing fxload my lsusb looked like this:
Bus 004 Device 002: ID 1604:8006 Tascam US-122 Audio/Midi Interface (without fw)
After fxload, it looks like this:
Bus 004 Device 003: ID 1604:8007 Tascam US-122 Audio/Midi Interface

Each time I retry, Device increases. It has the same behaviour on 64Studio, do you think it is motherboard-related?

[EDIT]Sorry, didn't read through the thread. But, after adding udev rules, things doesn't change, I'm still stuck and leds doesn't lit up. Any hints?[/EDIT]

I have exactly the same problem my friend either on Dapper or Edgy. I tried installing the Ubuntu Studio first and it work once but I had to do a format on my system partition and unfortunately I don't remember the configuration to setup it again now. :-(
Can anyone help us out?

---

### Post by [censored] on 2007-04-24
Hi. Did the howto, fully. For some reason I'm gettting a strange crackling noise whenever I try to play anything back with Audacity. Haven't tried recording with it. 

Not sure if this is a problem with the Tascam set up, or whether it's a problem with Audacity. Can anyone help diagnose?

---

### Post by shanek on 2007-04-25
I'm having the crackling problem in Feisty too. Looks like this is a common theme for those of us who upgraded. My wife's Dapper setup uses this how-to without a problem at all.

---

### Post by [censored] on 2007-04-26
Shanek interestingly, don't get the problem with ardour  + jack. A pity, because I hate ardour, way too complicated and buggy.

Can't get audacity to run via jack though. Just won't work.

---

### Post by shanek on 2007-05-03
Yeah, I feel your pain. Ardour is a decent app, but it's way more complicated than necessary for simple recordings.

On the other hand, its better than nothing. I'll give it a try.

---

### Post by lcadwell on 2008-01-13
Hi.

I had the cracking problem in 64 studio. It seems that the usb needs to be prioritized. I tried this but it didn't work. What did was to increase latency to plus 20ms. Not really acceptable but at least it works without crackling. 

I read all this on another forum somewhere. I'll post the link if I can find it.

---

### Post by nrolland on 2008-01-13
Hi,

If I understand well, the firmware is updated with the ubuntu one.
How will I restore the original firmware to get it working back with a Windows box ? 

Nicolas

---

### Post by ejoftheweb on 2008-01-24
Nicolas, I think the windows driver will probably reload the windows firmware when you plug it in because the linux driver has to be reloaded each time (it's not saved on the tascam when you unplug it). 

Unfortunately I'm still having no luck with this thing myself. I've tried using both the unfree firmware in the alsa-firmware package and Martin Langer's free firmware; whether I run it from the command line or using udev the problem is the same, usx2yloader says "no US-X2Y-Compatible Cards Found"; but lsusb shows that the first stage seems to have gone OK because the device number has gone up from 8006 to 8007 and it no longer says "without fw"...

It works OK in XP though, so box not broken.

(using Debian lenny/sid, not ubuntu, but the problem on this thread is the same as mine)...

---

### Post by pliktrologos on 2008-02-19
> **pliktrologos said:**
> I have exactly the same problem my friend either on Dapper or Edgy. I tried installing the Ubuntu Studio first and it work once but I had to do a format on my system partition and unfortunately I don't remember the configuration to setup it again now. :-(
Can anyone help us out?

Almost everything plays well now on Gutsy. I managed to install the latest alsa-firmware-loaders (copy the downloaded alsa-firmware-1.0.15 files in the `/usr/share/alsa/firmware` folder) and add the `55-tascam.rules` file to the `/etc/udev/rules.d/` folder containing these 2 lines
```
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx'"
BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"
```
Unplugging the TASCAM's usb cable and re-plugging it works but not always instantly (sometimes I have to wait maybe a few minutes for the "USB green light" to power on the soundcard again after re-plugging). Also when I sometimes start Amarok I get an error message "*xine was unable to initialize any audio drivers*" and I have no audio output (in random starts) and I have to quit the Amarok and start it again until no message failure or reboot the OS if I have no audio output signal at-all and finally I have occasionally random "pops" only when playing an audio cd and a high db "shshsh" noise for about 1sec between track change and audio pause from audio or video (with embedded audio) files.
Now I'm on continuing and setting up JACK and more multimedia applications and maybe I'll go on by installing Ubuntu-Studio in the future...

---

### Post by pliktrologos on 2008-02-22
I did notice that I can't have more than one application running that use TASCAM's audio output, so if I have e.g. Amarok playing and I try to open a website on firefox which has audio embedded I have an "audio crash" in which I have to quit all applications using the audio drivers for a while since I can use the audio output again :-(

---

### Post by eel on 2008-03-08
i am at my wits end. really
i tried every how-to on the subject but nothing gives. No green light for me (sob & cry). I caught myself thinking of reinstalling windows for the first time since i changed to ubuntu.

I got so far that my us 122 shows when i do lsusb and also when i do cat /proc/asound/cards. Every time i connect/reconnect the card gets a different device number though. And no flashing lights.

I have the feeling something went wrong at the very beginning, for instance i have no 'firmware' folder in my usr/share/alsa but an 'alsa-firmware-1.0.15'. If i remember correctly this was because some download link was broken and i had to get the stuff somewhere else. Also i have been trying so many howtos that are all slightly different that i get the feeling that they all work half but some of the files i am supposed to create already exist with the same name but not necessarily the same content. Maybe.

i just want to make music but i have been spending the last 2 days doing nothing but learning a lot about linux which is nice too but not nearly as satisfying as my primary goal.

So anyone who has a thought on this or is willing to help me in general do not hesitate to make yourself heard

if you help me get my soundcard working you will be liked & memorized for as long as i live.

---

### Post by pliktrologos on 2008-03-08
I re-installed my US-122 today cause I had a problem and I did a format on my Kubuntu Gutsy. So let's see if I can help you out. Can you download this file? [ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.15.tar.bz2]("ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.15.tar.bz2")

---

### Post by eel on 2008-03-09
if i paste the code i get a no such file or directory. So no i guess i cant.

---

### Post by pliktrologos on 2008-03-10
I'm sorry. I edited my previous post so please click now on the link to download the file. I entered it as a "code" by mistake. Is it ok now?

---

### Post by eel on 2008-03-10
it is being sucked into my desktop as we speak :)

---

### Post by pliktrologos on 2008-03-10
Allright! Can you make a new folder in the "/usr/share/alsa/" called "firmware" and extract all the files from the alsa-firmware-1.0.15.tar.bz2 archive into it? I think you will need root access for this so try with "sudo" command or via the graphical interface. Is it clear or do you need the exact commands?

---

### Post by eel on 2008-03-10
i know i can eventually figure it out but if you would be able to give me the direct code i would be very happy

---

### Post by pliktrologos on 2008-03-31
go to this folder
```
cd /usr/share/alsa/
```
and make a new folder called "firmware"
```
mkdir firmware
```
run ark for your "tar.bz2" file containing the firmware and **located in your Desktop** to extract all the files from the alsa-firmware-1.0.15.tar.bz2 archive
```
ark ~/Desktop/alsa-firmware-1.0.15.tar.bz2
```
**select the folder "usx2yloader" under the Root Folder and go to menu "Action" -> "Extract" and at the "Destination folder" paste this**:
/usr/share/alsa/firmware/
so if you now run this
```
ls /usr/share/alsa/firmware/usx2yloader/
```
you will get the above files listing:

an2131.asm Makefile.in tascam_loader.asm us122.conf us122.prepad us224.conf us224.prepad us428.conf us428.prepad Makefile.am README tascam_loader.ihx us122fw.ihx us122.rbt us224fw.ihx us224.rbt us428fw.ihx us428.rbt

is that clear?

---

### Post by brunets on 2008-04-04
> **minreelbayron said:**
> can someone help me out here.
this is where i KEEP getting stuck:

michaelbeijer@xubuntu:~$ sudo fxload -s /home/michaelbeijer/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/001/002
[B]/proc/bus/usb/001/002: No such file or directory
[/B]
what the **** does this mean?


I had the same problem. Replace "/proc/bus/usb/001/002" with "/dev/bus/usb/001/002"

Stéphane

---

### Post by bryerhop on 2008-05-27
I'm having a hard time with this. I'm stuck on step 8 from here [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122). 

I am using the command:
sudo fxload -s /home/robert/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/001/002

the /home/robert/ is the right location for the file, I double checked??

and my bus looks like this:
Bus 001 Device 002: ID 1604:8004 Tascam US-224 Audio/Midi Controller (without fw)

Here is the message I receive:

/usr/share/alsa/firmware/usx2yloader/us122fw.ihx: unable to open for input.

Can someone please help me?

---

### Post by pneaveill on 2008-05-27
> **brunets said:**
> I had the same problem. Replace "/proc/bus/usb/001/002" with "/dev/bus/usb/001/002"

Stéphane

Loaded alsa-firmware from alsa project (it has usx2y.... in it) and loaded that into /usr/share/alsa/firmware/alsa-firmware-1.0.16 directory 

 now alsa says it needs as31

> Building the firmware from source is possible, if you use the 
configure option --enable-buildfw. Also, it requires the 8031/8051
cross-assembler as31. As31 version 2.3.0 is fine for this job, but 
every version since 2.2 should do it.

As31 is available from:
[http://wiki.erazor-zone.de/doku.php?id=wiki:projects:linux:as31](http://wiki.erazor-zone.de/doku.php?id=wiki:projects:linux:as31)

What am I not doing right here please?
Never loaded an assembly compiler system and have no clue what to do with it from here.

------- edit --------------

---

### Post by pneaveill on 2008-05-28
I think this worked (so far), but submitting it for review here:

> niceguy@niceguy:~/Desktop/usx2y# make
as31 ld2-ezusb.asm
including file: an2131.asm
Begin Pass #1
Begin Pass #2
niceguy@niceguy:~/Desktop/usx2y#

> lsusb
Bus 002 Device 002: ID 8086:1120 Intel Corp. 
Bus 002 Device 003: ID 0644:800e TEAC Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 001 Device 001: ID 0000:0000 
>  niceguy@niceguy:~/Desktop/usx2y# sudo fxload -s /home/niceguy/Desktop/usx2y/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/002/003
can't modify CPUCS: Broken pipe I know that the broken pipe thing there is the ~/002/003 that is somehow not being written to and I cannot figure out why.  Hoping for some assistance on this.  
anyone with ideas?

---

### Post by khaosgott on 2008-12-06
hey guys, im having a problem to finish the installation.

after loading the usx firmware, im trying to run the usx2yloader but apparently its not found:

no US-X2Y-compatible cards found

help please?

---

### Post by amias on 2009-03-04
anyone tried this card in intrepid 64bit ?

---

### Post by pneaveill on 2009-03-04
> **khaosgott said:**
> hey guys, im having a problem to finish the installation.

after loading the usx firmware, im trying to run the usx2yloader but apparently its not found:

no US-X2Y-compatible cards found

help please?

Just curious and did not know this until just recently: my problem all of this time was that not all USB are created equal.  Most of the older ones are 1.0 and most of the external uSB devices use 2.x.

Otherwise what else is going on with it please?

---

### Post by pneaveill on 2009-03-04
> **amias said:**
> anyone tried this card in intrepid 64bit ?

Sorry, but 64 is a bit over budget for me. Am married with kids ;)

---

### Post by DannyBiker on 2009-03-14
Same problem here : when i want to proceed with Step 9 of the tutorial, I get the "no US-X2Y-compatible cards found" message. And my Tascam Device number keeps increasing everytime I try once more. Does someone have the solution for this ?
I am a total newbie in the linux universe and I'm still afraid of doing something wrong here...;)

Thanks !

---

### Post by rg_stephens on 2009-03-17
> **bryerhop said:**
> .... Here is the message I receive:

/usr/share/alsa/firmware/usx2yloader/us122fw.ihx: unable to open for input.

Can someone please help me?

I'm having the same problem. This device seems to work in Windows, but in Hardy I'm getting stuck at this point. Is there any other way to get the firmware loaded??

EDIT: I fixed it. My usx2yloader folder was in the wrong place. Works GREAT!!! Thanks!

---

### Post by fede_xyx on 2009-03-26
> **rg_stephens said:**
> I'm having the same problem. This device seems to work in Windows, but in Hardy I'm getting stuck at this point. Is there any other way to get the firmware loaded??

EDIT: I fixed it. My usx2yloader folder was in the wrong place. Works GREAT!!! Thanks!

I had that problem because i didn't installed alsa-firmware. After installing that it worked. Just go to synaptic, search for alsa-firmware, install it and it should work fine.

By the way, i tried all this in Ubuntu 8.10 Intrepid Ibex, and US122 loads every time i start ubuntu, but i can't hear sounds. i don't know if it's due to gnome or what. Anyone tried this in Intrepid?

---

### Post by fede_xyx on 2009-03-26
I managed to make US-122 on Ubuntu 8.10 Intrepid Ibex.

It must be done everything explained in the how-to [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122) and then on gnome go to system -> sounds and select the device there.

---

### Post by KevinD_Atl on 2009-05-01
I'm getting this output from my Hardy 8.10 on my   lsusb command...


Bus 007 Device 003: ID 0644:800e TEAC Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  



Is this going to work, or is the firmware drivers not good with the Hardy?

---

### Post by superaLeZap on 2009-05-02
> **DannyBiker said:**
> Same problem here : when i want to proceed with Step 9 of the tutorial, I get the "no US-X2Y-compatible cards found" message. And my Tascam Device number keeps increasing everytime I try once more. Does someone have the solution for this ?
I am a total newbie in the linux universe and I'm still afraid of doing something wrong here...;)

Thanks !
I get the same problem, first I tried on Linux Mint, then I installed ubuntu 9.04 but nothing has changed...

---

### Post by pneaveill on 2009-05-02
> **fede_xyx said:**
> I managed to make US-122 on Ubuntu 8.10 Intrepid Ibex.

It must be done everything explained in the how-to [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122) and then on gnome go to system -> sounds and select the device there.

Been working on this issue since early in the thread and still have not figured it out.

---

### Post by claudioaudio on 2009-06-17
I am completely confused. I just installed Ubuntu so im pretty much a NEWb. Could someone please post a youtube video showing how to do this step by step?? I would really appreciate it. Thanks in advance

---

### Post by pneaveill on 2009-06-30
> **claudioaudio said:**
> I am completely confused. I just installed Ubuntu so im pretty much a NEWb. Could someone please post a youtube video showing how to do this step by step?? I would really appreciate it. Thanks in advance

If someone would be willing to do so, would appreciate it.  Between the Jack issues and the Tascam/Teac issues -- argh :(

---

