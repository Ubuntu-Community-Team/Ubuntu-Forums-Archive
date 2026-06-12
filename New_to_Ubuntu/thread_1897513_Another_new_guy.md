---
title: "Another new guy"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by 40FiveSeventy on 2011-12-19
[COLOR=#222222][FONT=Arial][SIZE=2]Howdy all,[/SIZE][/FONT][/COLOR]
 
[COLOR=#222222][FONT=Arial][SIZE=2]Well, I took the plunge after I got malware'd. I have been running a windows computer for ... a very long time. I've never worked with any other OS or environment, but times change. Yesterday morning, I got a nasty little piece of malware on my computer and it basically wrecked me. Instead of reinstalling windows (that I no longer have the discs for - thanks movers), I rooted around and found an old disc my buddy gave me - "Ubuntu 10.04 LTS." I decided to give it a shot. I installed it and I should finish the upgrade up to 11 today. But, I am way, way lost. I mean, I can still get on the internet and such, but the learning curve is steep. So, hopefully I'll learn! Happy to be here.[/SIZE][/FONT][/COLOR]
 
[FONT=Arial][SIZE=2]The first hang-up I hit was with installation. I mean, naturally, right? Apparently my hdd is still partitioned with 2 different windows segments on it, and now ubuntu. After I get the full upgrade to 11+, I want to wipe clean those other partitions. I tried that once with the manual install, but I got a "no root designation" message. As a newbie that was pretty much Cantonese. So, if I can figure that out or get some direction, it'd be awesome. Thanks, all.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]-45S[/SIZE][/FONT]

---

### Post by lechien73 on 2011-12-19
Hi and welcome to the forums,

That's great that you've taken the plunge, I hope you enjoy using Linux as much as I do.

The default installation for Ubuntu is to leave your Windows partitions intact, so they likely are still there.

It would be useful to know your hard disk structure, so if you could open a terminal window and type:

```
sudo fdisk -l
```

then post the output here between CODE tags (the **#** button on the toolbar).

If you were sticking with 10.04, then I'd suggest using a GParted live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) to adjust your partitioning; however if you're going to be going to 11.10, then a fresh install would probably be better.

Hope this helps...enjoy the journey :D

---

### Post by sudodus on 2011-12-19
Now that you have Ubuntu 10.04 LTS running, don't upgrade it immediately. Keep it if it co-operates well with your hardware!

Then download several newer versions and other flavours of Ubuntu:

(vanilla) Ubuntu new version with Unity (new feeling, but tough on old hardware)
Kubuntu with KDE (advanced and fancy, tough on old hardware)
Lubuntu with LXDE (super light-weight, best choice on very old hardware)
Xubuntu with XFCE (light-weight)

and run them live from a CD or USB drive before you decide what to choose. It is much better to do a fresh install than to upgrade (since you do not have a lot of software and configuration yet).

Good luck and post your results for help and discussion :-)

---

### Post by 2F4U on 2011-12-19
My advice would be to stick with 10.04 LTS. First of all, it is a Long Term release, so many bugs have been ironed out. Secondly, it still has the classic Gnome interface, which may be more convenient for a Windows convert. Unity, the new default interface, is totally different and many people can't get used to it. Thirdly, in April 2012 the next LTS release comes out and you will be able to upgrade directly from 10.04 to 12.04.

---

### Post by 40FiveSeventy on 2011-12-19
If only I had the wisdom to come here last night! Sigh. 
 
I really appreciate the immediacy of the help, guys. Right now, I'm 1 update shy of the 11+ release. But, if I'm hearing this correctly, as a newbie, it might be best to re-install to 10.04LTS and work from there? Now, if I do that, one assumes I still need to run my upgrades, just not all the way to the newer version. Is that correct? 
 
As an aside - The reason I went ahead with the upgrade originally was because I couldn't figure out how to connect to my wireless internet in my house (is there an "ultimate shame" smiley over here on the right? No..? Okay, moving on). I figured with the upgrade it might get a little easier. Granted, I could have just looked up my SSID on my wife's computer, but I think that would have been far too easy. Anyway - I will probably re-install tonight, but I still have the partition issue to tackle. 
 
Lechien - after I get that done, I'll post up my disk structure. Don't have anything to drink, because it'll likely be laugh worthy. 
 
-45S

---

### Post by 2F4U on 2011-12-19
Yes, install 10.04 LTS. Upon the first boot when you login to your desktop, it will sooner or later inform you about new updates. Apply those updates and, since it will provide you with a new kernel, reboot the machine when it is finished.

---

### Post by sudodus on 2011-12-19
Yes, run updates within 10.04 (no dist-upgrades or upgrades to the new versions 10.10,11.04,11.10). Either you wait for it as suggested in the previous post, or you use apt-get from the command line
```
sudo apt-get update
sudo apt-get upgrade
```or via the GUI ***Synaptic***

And if/when you get curious, try some new versions and other flavours live from CD or USB without installing until you are sure that it works better. Two things that may work better with a new version (kernel) are wireless lan and graphics, particularly if you have new hardware. Old hardware probably co-operates better with 10.04 LTS.

---

### Post by 40FiveSeventy on 2011-12-19
A quick question about my setup so as not to thread hog. I did a search on partitioning and installing, and I'm going to try the "advanced" partioning method with installation tonight. I want to be sure that I have the right setup going forward. Should look like this, right?
 
300 MB ext /boot
2gb logical, beginning, swap area
8gb primary, beginning, ext 2/4 /
230gb primary, beginning, ext 2/4 /home
 
that'll leave me about 10gb of free space that I want to put a small windows install later. Do I have this right? And, will it work (installing windows later)?
 
Thanks for all the patience.

---

### Post by grahammechanical on 2011-12-19
You are getting a lot of advice. Be your own man or woman. Make your own decisions. 10.04 is being recommended because it is a Long Term Service release. The support for it lasts up until April 2013. Whereas, support for 10.10 or any non-LTS version is eighteen months. So, 10.10 support ends April 2012. Some will give you other reasons. That is true.

The next LTS release is 12.04 (April 2004) and it will be supported for 5 years.

You should know this: there is a big difference in the look and way of working between 10.10 and earlier versions and 11.04 and following versions. Do not spend the next six months or longer getting used to 10.04 or 10.10 only to upgrade to 12.04 and discover that you are back at the bottom of the learning curve again.

Take the tour at Ubuntu.com and notice the difference between what you have and what is the latest and the future of Ubuntu.

Regards.

P.S. As for partitioning, why not take a screenshot of your present disk partitions and start a new thread? That will be the best way to do it. You will get lots of help.

---

### Post by 40FiveSeventy on 2011-12-19
graham - you make a good point. When I get back to the house I'll do that. That is, I'll take the tour *and* I'll post up the screenshot. Hopefully, I wont ask too many dumb questions.

---

### Post by sudodus on 2011-12-19
> **grahammechanical said:**
> ...
P.S. As for partitioning, why not take a screenshot of your present disk partitions and start a new thread? That will be the best way to do it. You will get lots of help.

+1

It is good to separate the two issues (selection of Ubuntu version and flavour / HDD partitioning). In general, I would say that you have to think for a while until you decide if you need a Windows partition. Many people dual boot for a period until they are sure that they don't need Windows any more. But if you need Windows, I suggest that you allocate much more than 10 GB (maybe 40 GB). How much disk space does your present Windows system occupy?

---

### Post by I2k4 on 2011-12-19
I'm another newcomer - I spent several months trying out Live USB with Persistence, several versions of different stripes, before committing anything to a hard drive.  Not being a techie but being a not-so-dumb end-user since the mid-1980s, on Mac, Windows and now Linux, I like to look before leaping. 

One of the best things about Linux is the ability to do real world testing without commitment - Linux is the call girl of operating systems, enjoy it.

---

### Post by JKyleOKC on 2011-12-19
> **40FiveSeventy said:**
> that'll leave me about 10gb of free space that I want to put a small windows install later. Do I have this right? And, will it work (installing windows later)?Installing Windows later may easily destroy your Ubuntu bootloader; if you want a small Windows partition, install it first and shrink it to your desired size, then install Ubuntu afterward. You can repair the boot loader, but it's going the very long way around...

An alternate way to proceed would be to install Ubuntu to occupy the whole drive, then after updating the 10.04 LTS to its current level, install VirtualBox via the Synaptic package manager and create a virtual machine with a 30-GB virtual drive. You can then install Windows in that VM, and have it available from within Ubuntu with no need to shut down and reboot. For this approach to work best, your CPU needs to have at least two cores, and you need at least 2 GB of RAM; however I've run such a setup with an ancient single-core CPU and only 512 MB of RAM, and it works -- but is horribly slow with so little resources.

---

### Post by nothingspecial on 2011-12-19
Hi 40FiveSeventy, welcome to the forums :)

@everybody else, thank you all for contributing, but can we please keep to the first question which was

> **40FiveSeventy said:**
>  Apparently my hdd is still partitioned with 2 different windows segments on it, and now ubuntu. After I get the full upgrade to 11+, I want to wipe clean those other partitions. 

And the second

> I want to be sure that I have the right setup going forward. Should look like this, right?
 
300 MB ext /boot
2gb logical, beginning, swap area
8gb primary, beginning, ext 2/4 /
230gb primary, beginning, ext 2/4 /home
 
that'll leave me about 10gb of free space that I want to put a small windows install later. Do I have this right? And, will it work (installing windows later)?

Thank you.

---

### Post by BeMyManikin on 2011-12-19
> **40FiveSeventy said:**
> [COLOR=#222222][FONT=Arial][SIZE=2][/SIZE][/FONT][/COLOR][COLOR=#222222][FONT=Arial][SIZE=2]Well, I took the plunge after I got malware'd. I have been running a windows computer for ... a very long time. I've never worked with any other OS or environment, but times change. Yesterday morning, I got a nasty little piece of malware on my computer and it basically wrecked me.[/SIZE][/FONT][/COLOR][FONT=Arial][SIZE=2][/SIZE][/FONT]
Same thing happened to me, but I have the 11.10, and actually I like this a lot better than windows. It syncs up better with me better some how. Welcome!

---

