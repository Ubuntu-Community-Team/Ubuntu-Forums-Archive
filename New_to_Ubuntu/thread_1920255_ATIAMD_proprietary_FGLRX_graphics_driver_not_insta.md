---
title: "ATI/AMD proprietary FGLRX graphics driver not installing?"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by Dameentsia on 2012-02-04
Whenever I go to System Settings, Hardware, and then Additional Drivers, I see this:
[IMG]http://img59.imageshack.us/img59/8190/selection252.png[/IMG]
Even though I have installed the 'ATI/AMD proprietary FGLRX graphics driver' and restarted on two different occasions, somehow it is not in use.  I saw on the internet when I was searching my problem (which I couldn't find anything to help me on the issue) that it is much better to go to the ATI/AMD site and install the software for my graphics card directly from there.  So, I got the .run file for it, I run it, try to install it, and it says:
[IMG]http://img443.imageshack.us/img443/4472/selection253v.png[/IMG]

What should I be trying to do?  Should I be trying to fix a problem with the software installed by Ubuntu?  Preferably, I would like to uninstall the software that Ubuntu put on my computer, and install the one I got from the ATI website.  But hey, whatever works.

Oh, and it might be important to note that 'ATI/AMD proprietary FGLRX graphics driver (post-release updates)' just completely refuses to install at all.

It probably is also important to note that the reason this bothers me is because games are pretty sluggish, and if I am, say, playing a video, I often get the horizontal line of death if there is a lot of movement on the screen.  This happened to me on Windows also, and when I installed my graphics card's software, the problems were solved.  One can only assume that it would be the same for Ubuntu (but, obviously I am a noob at it).

---

### Post by partloer on 2012-02-04
I had a similar problem when I tried to install my drivers I think this is what I did for mine (but could be wrong).  

The driver below work for most but double check yours

```
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-1-x86.x86_64.run
chmod +x amd-driver-installer-12-1-x86.x86_64.run
sudo ./amd-driver-installer-12-1-x86.x86_64.run --force

```

---

### Post by Dameentsia on 2012-02-05
> **partloer said:**
> I had a similar problem when I tried to install my drivers I think this is what I did for mine (but could be wrong).  

The driver below work for most but double check yours

```
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-1-x86.x86_64.run
chmod +x amd-driver-installer-12-1-x86.x86_64.run
sudo ./amd-driver-installer-12-1-x86.x86_64.run --force

```

Alright, I did all of that, seemed to work, installed the software, and rebooted.  When I try to start up Ubuntu, it doesn't work.  It shows the Ubuntu loading screen for a second, then it just flashes off and I get a black screen, and both of my monitors go on standby.  I tried waiting through it for about ten minutes, still nothing.  I am currently running in safe mode, what can I do to fix this?  (It was the right driver, btw)

---

### Post by Krytarik on 2012-02-05
> **Dameentsia said:**
> When I try to start up Ubuntu, it doesn't work.  It shows the Ubuntu loading screen for a second, then it just flashes off and I get a black screen, and both of my monitors go on standby.
Try the "nomodeset" fix:

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Hope that works.

---

### Post by Dameentsia on 2012-02-05
> **Krytarik said:**
> Try the "nomodeset" fix:

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Hope that works.

No luck, however, the nomodeset makes it so some text pops up on the screen before the screen goes black and my monitors go to sleep.

Should I try reinstalling the ATI software while in recovery mode?  Not exactly sure how I should go about this.

EDIT:  After looking in my installed apps, I have two "AMD Catalyst Control Center"s and also two of the administrative version of it.  At this point, I am kind of guessing that it would be best to uninstall both of the versions of the AMD/ATI software that I have and reinstall just one of them.

---

### Post by mastablasta on 2012-02-06
how about some system specs? are you maybe using switchable graphics? what GPU do you have? did you perform some upgrade maybe(since it says it already has a fglrx version)?
 
to remove the driver: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
 
you can reinstall it afterwards.

---

### Post by Dameentsia on 2012-02-06
> **mastablasta said:**
> how about some system specs? are you maybe using switchable graphics? what GPU do you have? did you perform some upgrade maybe(since it says it already has a fglrx version)?
 

Specs: (Not exactly sure what matters)
Intel i3 550 @ 3.20 GHz (Dual-core)
6GB RAM
1TB Hard Drive (Ubuntu running on a 100gb partition)
Ubuntu 11.10 x64
1 ATI Radeon 5770 as my GPU, Not switchable as far as I know.

And, I don't recall preforming upgrades, I'm pretty sure it's the other guy's fix that caused me to have two.

But I will try uninstalling, thanks much.

---

### Post by mastablasta on 2012-02-06
it says here that i3 550 does have GPU on some systems: [http://ark.intel.com/products/48505/Intel-Core-i3-550-Processor-(4M-Cache-3_20-GHz](http://ark.intel.com/products/48505/Intel-Core-i3-550-Processor-(4M-Cache-3_20-GHz))
 
ok, well then try purging and reinstall maybe it will help.

---

### Post by QIII on 2012-02-06
After you installed and before you rebooted, did you run the following in the terminal?

```
sudo aticonfig --initial
```

---

### Post by Dameentsia on 2012-02-06
Alright, uninstalled the driver software and now only have one of each of the AMD config (whatever) apps.

> **QIII said:**
> After you installed and before you rebooted, did you run the following in the terminal?

```
sudo aticonfig --initial
```

And, no, I did not.  I will try that now and reboot, and try to start normally.
EDIT: Just tried it and got: 
```
sudo: aticonfig: command not found
```[FONT=monospace] 
EDIT 2:  I tried rebooting just to see if it would do anything, and now neither regular boot or recovery mode will work. ;-;  If I run recovery mode, all I get is a terminal text interface. (I am currently running my Windows 7 partition right now) At this point, I think I can safely say that reinstalling Ubuntu would be the best option.

EDIT 3:  Okay, I've reinstalled Ubuntu, and I want to get things right this time.  Should I install the ATI software from System Settings>Additional Drivers, or should I install it from the AMD website?
[/FONT]

---

### Post by northwestern on 2012-02-06
I do not bother with the additional drivers now. Whenever a upgrade appears I use the "unofficial AMD" site, works like a charm every time. Just follow the instructions.
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

Hope this helps.
Regards
Northwestern

---

### Post by larrypg on 2012-02-06
Hello,

I would use the additional drivers.  I would not use the post update drivers but the one below that.  You must choose the activate button.

---

### Post by Alexislavie on 2012-02-23
Check this post : [ http://ubuntuforums.org/showthread.php?p=11712748]("http://ubuntuforums.org/showthread.php?p=11712748")

---

### Post by imzack on 2012-03-18
I am brand new to the linux/ubuntu software...

I was having the same problem the original poster had.
I did what the one indivudual suggested to install the ati driver,

After installing i ran the sudo aticonfig --initial

then i restarted my computer

now when i restart, it loads up, i enter in my password, and then i type in startx to start, but it runs startx then says something of the sort
"segmentation fault at address 0x708"
"caught signal 11(segmentation fault). Server aborting"

and some other lines


I went to the [http://ubuntuforums.org/showthread.php?p=11712748](http://ubuntuforums.org/showthread.php?p=11712748)  page and ran those lines of code provided, and still the same thing happens when i attempt to run startx


any one know whats up, or how i fix this?


Thank you,

Zack

---

### Post by imzack on 2012-03-18
[http://forums.opensuse.org/english/get-technical-help-here/applications/453012-gnome-no-longer-starts-after-update-suse-11-3-ati-graphics.html](http://forums.opensuse.org/english/get-technical-help-here/applications/453012-gnome-no-longer-starts-after-update-suse-11-3-ati-graphics.html)

This seems like he had the same error as me, i dont understand this stuff to know what he did to get it working though

---

### Post by Mark Phelps on 2012-03-19
> **imzack said:**
> I am brand new to the linux/ubuntu software...

Hey, don't feel bad -- that was true of ALL of us at one time.

But, Linux is not Windows; meaning, you don't need to go hacking around with drivers to get things working.

Unless you are an intensive 3D gamer, you don't really NEED the AMD drivers installed.  That's more trouble than it's worth.

Instead, you should remove the AMD drivers and replace them with the default open-source drivers.  Instructions below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by amajewicz on 2012-06-26
Hey, 

I'm in a similar spot - both normal boot and recovery boot led to the black screen. Is the best option really to reinstall the OS? There has got to be a better way! Right now I'm not even sure how to get the command line working. I tried nomodeset but that didn't do anything. Any help would be greatly appreciated! 
Thanks!






> **Dameentsia said:**
> Alright, uninstalled the driver software and now only have one of each of the AMD config (whatever) apps.



And, no, I did not.  I will try that now and reboot, and try to start normally.
EDIT: Just tried it and got: 
```
sudo: aticonfig: command not found
```[FONT=monospace] 
EDIT 2:  I tried rebooting just to see if it would do anything, and now neither regular boot or recovery mode will work. ;-;  If I run recovery mode, all I get is a terminal text interface. (I am currently running my Windows 7 partition right now) At this point, I think I can safely say that reinstalling Ubuntu would be the best option.

EDIT 3:  Okay, I've reinstalled Ubuntu, and I want to get things right this time.  Should I install the ATI software from System Settings>Additional Drivers, or should I install it from the AMD website?
[/FONT]

---

