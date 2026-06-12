---
title: "Upgrading 10.04 to 12.04"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by sal55 on 2013-06-30
As a beginner I can't get my Linux system to do much at all without having to install a number of packages each time I try something (despite having apparently tens of thousands of files already present!).

From my first thread ('X programming') it seemed that my 10.04.01 system is too old, packages are no longer available, or don't exist for my hardware (ARM). Today, I wanted to set up file sharing with Windows, and instructed it to install whatever it had to, via a series of dialogs. At the end it just said 'Sharing installation service failed.' without further details (just like anything else I try and do on this damn machine! Nothing works.)

So I thought I'd upgrade to 12.04 by following these instructions:

[http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-ubuntu-10-04-via-the-terminal/](http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-ubuntu-10-04-via-the-terminal/)

However, it just says: 'Authenticating the upgrade failed. ... problem with the network or with the server'.

What is someone supposed to do next? (Not that I have much confidence it will manage to go through the entire process, which I imagine is fairly involved, without at least one more fatal error coming up. Nor that 12.04 would be much better anyway!)

---

### Post by newb85 on 2013-06-30
First of all, before attempting an upgrade, you should back up your important files.  Upgrading doesn't always go smoothly.

Secondly, the instructions you tried to follow are out-of-date.  Those instructions would have worked prior to April 2013, when support for 10.04 ended.  At that point, the repositories were moved.  (That's also the reason you received the "Sharing installation service failed" message.)

You need to redirect your sources file to the new location.  Open the file using a text editor.  (I recommend gedit rather than vi, because for the average user, it's easier.)

```
sudo gedit /etc/apt/sources.list
```

The source lines you need to edit will look like this:
```
deb *http://address-of-mirror/archivename/* lucid repository-name
```

Replace the address so that it looks like this
```
deb *http://old-releases.ubuntu.com/ubuntu* lucid repository-name
```

(I italicized what you should change for clarity.  Don't attempt to italicize them in the file.)

Then save and close the file.

You can then proceed with
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoremove
```
and then move on with the upgrade process.

---

### Post by arpanaut on 2013-06-30
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

This should work but the other option is to do a fresh install of 12.04 which many consider to be better. 
There were many significant changes between 10.04 and 12.04.

Back Up your important data before you begin!

---

### Post by fantab on 2013-06-30
Doing a clean install of 12.04 is a good idea. Just Backup your important DATA first. Upgrading internally from 10.04 to 12.04 will NOT be without issues, and it can get messy. Fresh 12.04 install is recommended.

---

### Post by sal55 on 2013-07-01
> **sal55 said:**
> 

So I thought I'd upgrade to 12.04 by following these instructions:

[http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-ubuntu-10-04-via-the-terminal/](http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-ubuntu-10-04-via-the-terminal/)


Wrong link! It was actually the gui version:

[http://www.liberiangeek.net/2012/03/upgrade-from-ubuntu-10-04-to-ubuntu-12-04/](http://www.liberiangeek.net/2012/03/upgrade-from-ubuntu-10-04-to-ubuntu-12-04/)

However, I changed the sources.list file as suggested by newb85 and still had the same authentication error. (I'll try it the way it says in arpanaut's link in a minute.)

If I wanted to do a fresh install, how does that work exactly? Doesn't it need to be provided by the manufacturer of my machine, or does a Ubuntu distribution exclude hardware-dependent components? (I wondered about that also when using the generic 'old-releases.ubunto.com/ubuntu').

(There are also questions about the exact mechanics of how the new distribution gets inside my machine, which has internal flash memory, but I guess that can be answered with an on-line search!)

---

### Post by mastablasta on 2013-07-01
double post

---

### Post by mastablasta on 2013-07-01
> **sal55 said:**
> If I wanted to do a fresh install, how does that work exactly? Doesn't it need to be provided by the manufacturer of my machine, or does a Ubuntu distribution exclude hardware-dependent components? (I wondered about that also when using the generic 'old-releases.ubunto.com/ubuntu').

 
you can download UBuntu and boot from a USB stick, see if everything works and it works fast and then do a reinstall. there are two options one is with no disk formatting (overwrite the old and adds new files) and the other one formats the disk (erases all files). either way your settings are lost.

and if i may add you can get a list of hardware componets with *lshw* command you can then mark and copy it here if you want others to tell you of any incompatibilities.

---

### Post by snowpine on 2013-07-01
Tell us about your hardware... Manufacturer, model number, hardware specs?

---

### Post by sal55 on 2013-07-01
> **snowpine said:**
> Tell us about your hardware... Manufacturer, model number, hardware specs?

It's a netbook based on the ARM processor (not the same model as used in Raspberry pi; google for 'ecafe ex hd hercules').

So I guess that makes it trickier. I wouldn't mind just using a Linux running on my Windows desktop (either dual-boot or in a virtual PC; but I lack the confidence to install a dual-boot system now (will my Windows still work!), while my experiments using Virtual PC didn't work well (at best got a minimal system in text mode. And trying to run Ubuntu 12.04, it has serious problems driving the virtual display.)

This standalone machine should have been less hassle...

---

### Post by mastablasta on 2013-07-01
some arm are supported, some are not. you need the ARM image then.

as for installiing in virtual i suggest you follow this guide and use Lubuntu instead as it is much lighter on resources: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

i am runnign Xubuntu on single core, i gave it 512MB ram in v box. it runs reasonably well. though sometimes i wish i had more RAM to give it and more CPU power.

---

### Post by sal55 on 2013-07-01
> **mastablasta said:**
> 
as for installiing in virtual i suggest you follow this guide and use Lubuntu instead as it is much lighter on resources: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)


Thanks. Installed Virtual Box, gave it the same ISO file I'd used for Virtual PC, and it installed beautifully - until I had to restart it!

Then, it kept telling me to remove a disk then press Enter (but it was dead); then it couldn't find my graphics setup and ran only in console mode (despite the installation using the graphics mode perfectly!); typing 'startx' was also hanging after a few lines... why don't these things just work!

Anyway, online somewhere it said edit 'etc/X11/xorg.conf', so I tried that, but no such file. Only xorg.conf.failsafe. So copied from that and it worked! I even managed to download libx11-dev, and compile a Hello World program for 'X' (after trying twenty different ways to link it - every online resource said something different!).

(It was also very fussy about my machine name, rejecting practically everything I tried, even random keypresses, because they were 'already in use'. I now have a machine name consisting of a dozen random digits..)

BTW how do I run Terminal from the GUI? I did it eventually, but can't remember how.

---

### Post by Nr90 on 2013-07-01
Your machine is listed as a cortex A8, which should be supported by Ubuntu. You should be able to install the arm image natively.

I'm unsure if you need a specific image or if a generic arm image would do.

---

### Post by snowpine on 2013-07-01
> **sal55 said:**
> It's a netbook based on the ARM processor (not the same model as used in Raspberry pi; google for 'ecafe ex hd hercules').

So I guess that makes it trickier. I wouldn't mind just using a Linux running on my Windows desktop (either dual-boot or in a virtual PC; but I lack the confidence to install a dual-boot system now (will my Windows still work!), while my experiments using Virtual PC didn't work well (at best got a minimal system in text mode. And trying to run Ubuntu 12.04, it has serious problems driving the virtual display.)

This standalone machine should have been less hassle...

Afraid I don't have any experience with ARM... but I am actually in the market, so let me ask, how do you like it?

---

### Post by sal55 on 2013-07-01
> **snowpine said:**
> Afraid I don't have any experience with ARM... but I am actually in the market, so let me ask, how do you like it?

Apart from this netbook (800MHz Cortex), I've also used a raspberry pi running debian (700MHz ARM, earlier processor).

I found both machines under-powered. Unless there was something wrong the the netbook (eg. running something in the background I wasn't aware of), everything took forever. I thought my low-end Windows netbook (1GHz Atom or something) was slow, but it runs at a much more practical speed.

As an example, youtube via Firefox was so slow as to be unusable.

ARM is/was used in iPhones and things so it is obviously capable, but that's not apparent from the two Linux examples I've tried!

---

