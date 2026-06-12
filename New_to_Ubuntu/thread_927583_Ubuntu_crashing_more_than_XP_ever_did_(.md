---
title: "Ubuntu crashing more than XP ever did :("
date: 2008-09-23
forum: New to Ubuntu
---

### Post by madu on 2008-09-23
So I made the conversion to Ubuntu about an year and havent looked back since.. bu since couple weeks Ubuntu is driving me nuts!

There system just freezes! I have to power off by switch and start again. This mostly happens when I'm in FF(3).. Javascripts or Youtube clips constantly make it freeze... so I deleted the urlclassier.sqlite file (which by the way was growing into one enormous file) and disabled the security options.. I cant say for sure, but it showed some improvement... But this also happens when I am watching something in VLC too...

The logs dont say anything.. but one thing I noted is that when it starts to slow down and getting ready to freeze, the root process Xorg is taking a lot of cpu.. something like 80% (running on a dual-core laptop) and so is FF..

This is really frustrating... now I have to force restart the system like half a dozen times everyday... is there anyway I can diagnose what is happening? 

Thanks heaps guys..

---

### Post by Orange_and_Green on 2008-09-23
Hello :)

I am sorry you are having these problems, it could really be a lot of things... A quick (and most certainly not exhaustive) brainstorm:

1) Hardware -> Ram. Have you tried running memtest?
2) Hardware -> Disk. What do fsck and/or badblocks say?
3) Hardware -> Graphic card... hard to diagnose accurately I suppose. Do you know what hardware you are using? What driver are you using? Does it crash in safe graphics mode as well? Or with a different driver?  
4) Software -> I suppose you are using the flashplugin-nonfree flashplayer. Have you tried downloading the installer for the latest version from the adobe website? Does it get any better? And do xine/totem/whathaveyou crash as well on the same videos VLC crashes on?
5) Did this behaviour arise after any particular event? Installing a package/update/settings change etc....?

I wish you the best of luck troubleshooting...:KS

---

### Post by Bucky Ball on 2008-09-23
Hardware is the first thing that pops in to my mind, nicely outlined in the last post. Seeing as it seems to be connected with graphics stuff, well ... :(

Because ... if you haven't made any drastic changes software-wise and your machine has just started doing this behaviour ...

But I could be wrong.

---

### Post by bigken on 2008-09-23
my money is on the graphics driver

---

### Post by madu on 2008-09-23
Thanks a lot mate.
'fsck' gave me:
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=2a81ec82-23c9-4d16-acff-b266a3babd3d'

Now running badbloacks.. lets see if it turns up anything..

This as I understand started recently but cannot think of anything particular that may have caused this...

I guess I will do a memtest too and see..

Thanks for the suggestions mate.

---

### Post by madu on 2008-09-23
Thanks bigken..

I run compiz in here and it doesnt show anything wrong.. 
Maybe I will turn it off and see.. but other than that what can I do to determine if its the graphics?

I'm inclined towards the hdd too.. like I said fsck gave that error and I have been downloading stuff extensively throughout.. I guess the hdd couldbe the culprit... lets see if badblocks would turn anything up..

thanks man..

---

### Post by Bucky Ball on 2008-09-23
Perhaps stash your valuables if you haven't already, madu ... (backup personal data just in case HDD). :)

---

### Post by legatek on 2008-09-23
Turn off compiz. I have the same problem as you when running videos in Totem, as well as viewing videos on Youtube. It doesn't happen every time on Youtube but about 30% of the time the screen suddenly goes black and I have to hard reboot. Turning off compiz before watching videos prevents the problem 100% of the time.

I tried other solutions from other threads describing this problem, but disabling compiz is the only thing that works in my case.

---

### Post by schibros on 2008-09-23
Since this computer has been working for over a year, i dont think it would be an hardware issue if no new device has been addd to the machine. fsck should solve the problem. If you are running Hardy 8.04, it should do this for you periodically. I had a similar problem with an older machine running Gutsy, and i solved it with fsck.

---

### Post by billgoldberg on 2008-09-23
> **madu said:**
> So I made the conversion to Ubuntu about an year and havent looked back since.. bu since couple weeks Ubuntu is driving me nuts!

There system just freezes! I have to power off by switch and start again. This mostly happens when I'm in FF(3).. Javascripts or Youtube clips constantly make it freeze... so I deleted the urlclassier.sqlite file (which by the way was growing into one enormous file) and disabled the security options.. I cant say for sure, but it showed some improvement... But this also happens when I am watching something in VLC too...

The logs dont say anything.. but one thing I noted is that when it starts to slow down and getting ready to freeze, the root process Xorg is taking a lot of cpu.. something like 80% (running on a dual-core laptop) and so is FF..

This is really frustrating... now I have to force restart the system like half a dozen times everyday... is there anyway I can diagnose what is happening? 

Thanks heaps guys..

For the firefox freeze, try the new flash player 10 RC and switch to ALSA while you are at it.

Other things could be a lot of things. 

Is you hardware still fine?

I would most likely do a reinstall. That should fix most problems in 20 minutes.

---

### Post by Orange_and_Green on 2008-09-23
> **madu said:**
> Thanks a lot mate.
'fsck' gave me:
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=2a81ec82-23c9-4d16-acff-b266a3babd3d'


That is not an "error" AFAIK... if you don't pass a parameter to fsck (a partition to check), it will look for one in fstab and get thoroughly confused because it does not know how to resolve the UUIDs...

To run fsck on your root partition, please boot from a live CD (the file system must be unmounted prior to doing the check) and then type
```
fsck /dev/sdaX
```

where X is the number of the partition. If you are not sure where your root partition is (if you have a single-boot system and you used the default install, it most certainly is sda1), you can ask ```
sudo fdisk -l
``` or gparted for help ;)

---

### Post by madu on 2008-09-23
Hey thanks a lot fellows...

I will try the fsck after I finish the badblocks..

Will turn off compiz and try the other flash-plugin...
Yeah..a fresh install would do.. but I really don't want to..
Seems it doesnt matter if I am using Ubuntu or XP I am destined to reinstall once in a while...  :(

Thanks Orange and Green.. thought its an error.. I think I should have let Hardy run those periodical hdd checks at the startup.. I always skip then :confused:

thanks a million for all the help fellows...

---

### Post by madu on 2008-09-23
> **billgoldberg said:**
> For the firefox freeze, try the new flash player 10 RC and switch to ALSA while you are at it.

Other things could be a lot of things. 

Is you hardware still fine?

I would most likely do a reinstall. That should fix most problems in 20 minutes.

thanks mate.

Does it mean I have to un-plug the plugin I already have?
I have that non-free plugin which I downloaded from Adobe..
The RC 10 plugin.. where can I get it from...?

---

### Post by madu on 2008-09-23
Hello..

So the badblocks test finished and reported there are NO bad blocks..
You think doing fsck could still help or if badblocks return no errors then it would be redundant to run fsck?

Thanks again guys.

---

### Post by Orange_and_Green on 2008-09-23
In general, no, I don't think it would be completely redundant as fsck will correct "software" errors too while badblocks is on the hunt for damaged hardware; however if badblocks reported no errors, I think you can rule out a hard disk hardware failure pretty confidently.

Disabling compiz, possibly safe graphics mode and a memtest seem the most promising path to me right now, frankly.

I wish you the best of luck:KS

P.S.:If you do need to reinstall after all as billgoldberg suggested, may I interest you in a few fine backup tools being developed by folks on this very board (that includes my humble self too, please forgive the self ad :lolflag:)

[http://ubuntuforums.org/showthread.php?t=678665]("http://ubuntuforums.org/showthread.php?t=678665")
[http://ubuntuforums.org/showthread.php?t=915712]("http://ubuntuforums.org/showthread.php?t=915712")

---

### Post by madu on 2008-09-23
> **Orange_and_Green said:**
> In general, no, I don't think it would be completely redundant as fsck will correct "software" errors too while badblocks is on the hunt for damaged hardware; however if badblocks reported no errors, I think you can rule out a hard disk hardware failure pretty confidently.

Disabling compiz, possibly safe graphics mode and a memtest seem the most promising path to me right now, frankly.

I wish you the best of luck:KS

P.S.:If you do need to reinstall after all as billgoldberg suggested, may I interest you in a few fine backup tools being developed by folks on this very board (that includes my humble self too, please forgive the self ad :lolflag:)

[http://ubuntuforums.org/showthread.php?t=678665]("http://ubuntuforums.org/showthread.php?t=678665")
[http://ubuntuforums.org/showthread.php?t=915712]("http://ubuntuforums.org/showthread.php?t=915712")

Thanks a million buddy.
I guess a fresh install would solve a lot of things.. I have never done a backup in Ubuntu (linux).. Re-installations are one of the main reasons I switched from XP since installing all those apps again is a nightmare..
Will definitely have a look at the backing up threads mate.. thanks a lot again....

---

### Post by Orange_and_Green on 2008-09-23
I am glad I could be of help my friend:KS 

> **madu said:**
> Re-installations are one of the main reasons I switched from XP since installing all those apps again is a nightmare..

In that case, I dare hope my "aptautosave" program can help you out. The latest version I posted last night is still labeled "alpha" but works pretty fine I think. Just launch it and it will generate a script (into a directory named "aptautosave" in your home) that will reinstall all your packages. Just make sure you re-enable any third-party repositories immediately after reinstalling (LaRoza's System Restore backs them up too).

Speaking of reinstalls, if you haven't done so already, it is advisable to mount your /home on a separate partition of your HD. That way, after you reinstall (using the same username), you log in and have the majority of your settings back.
If your /home is not on a separate partition, I suggest that you copy all of its contents (ESPECIALLY the hidden files & directories, press CTRL+H to unhide them) onto a removable medium and bulk-replace after reinstall.

Please let me know how things go :)

Good luck:KS

EDIT: I re-uploaded the latest version of aptautosave including the README, which unfortunately "slipped" when I uploaded the latest version last night. The stable version is still 2.0 so if anything goes wrong please try that. The code is ugly but it does have been tested more extensively...:)

---

### Post by madu on 2008-09-23
Thanks buddy...
Copying the /home folder now... :)

---

