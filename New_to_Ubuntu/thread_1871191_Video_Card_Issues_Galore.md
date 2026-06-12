---
title: "Video Card Issues Galore"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by tbright on 2011-10-28
Hi all (first post), 

Im a newb (obviously) but have Ubuntu 11.10 up and running. On my 3rd day now.
When I did install, I had to modify my boot command like this:
"noquiet nosplash radeon.modeset=0"
I am running a Radeon Xpress 200M
If I didnt do this at startup, I would get a screen of white stripes and would have to force shut down.  

All was well after I made the change. Today, I made the change permanent in my etc/default/grub
When I shut down AFTER this, I noticed startup wasnt as smooth and there were some small changes to my display. It is usable tho, and working OK

I just wanted to give that all as background in case it is related to this problem:  I want to run some games like extremetuxracer, etc. So far, games will startup and run SUPER SLOW or will open and then immediately crash. Today, I tried Supertux and IMMEDIATELY got the same type of white screen of death I used to get at startup. When I had windows, I could run Call of Duty, NBA Live, and so on- so Id like to get that kind of performance from my card again.

What can I do? My understanding is that Ubuntu automatically uses the best open source drivers for my video card. But as far as I can tell, there are no proprietary drivers for my card that work in 11.10. Can someone verify this? I know my 3-d acceleration is active, bc I get "direct rendering:yes"

Any help or solution is welcome. Please direct your answers to a complete noob and be as specific as possible. Im hoping that even if I cant upgrade my driver, I can modify settings in some way. Thanks guys for the help. I searched diligently for an answer to this elsewhere, but I just cant figure it out.

Thomas

---

### Post by sadaruwan12 on 2011-10-28
First of all welcome to the forum.

For your problem now well it seems like you're having a issue with the drivers the free drivers for NVIDIA tends to the things you described.

So what I suggest is to install propitiatory drivers from the "hardware drivers" app.

Go to the dash and type in "hardware" from the first two letters you'll see it show up and click that and after refreshers it'll list the most current drivers select it and activate that driver.

Before doing that go to the system sources you can get it from the dash and enable the canonical partners repository as well.

If this doesn't work please tell us then we'll move into more drastic measures.

---

### Post by tbright on 2011-10-28
I guess "additional drivers" is the same thing? I went into the source and enabled those others. When it searches fro drivers it only returns with a wifi driver (which I dont need) and nothing about video drivers, etc.

:( whats next?

---

### Post by sadaruwan12 on 2011-10-28
You could install the drivers straight from nvidia installation package before that lets do this and see.

open the terminal and run this

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

then do this,

```
$sudo apt-get update
      $sudo apt-get upgrade
```

now see if this gives a upgrade to your drivers if this don't then you can install nvidia-graphic-drivers from the synaptic package manager.

Let us know what happened.

---

### Post by tbright on 2011-10-28
Ok. My card is ATI Radeon. So, do I really want nvidia drivers? lol

Edit: Not trying to be a smart @$$ but just wanted to make sure.--Thanks

---

### Post by Mark Phelps on 2011-10-28
WOW -- so NOBOBY even bothered to READ your initial post in which you clearly say that your video card is ATI??

Sorry, but the open source drivers, the one already installed by default, are the ones available for your card now.

AMD (who bought ATI) relegated your card, along with a lot of others, to "legacy" status some time back, meaning, they stopped writing drivers for it.

---

### Post by tbright on 2011-10-28
Ah, well thanks Mark. I thought it might end like this. Maybe I can invest in a new card. I still dont fully understand why I could get decent quality for the card on Windows and cant play more basic games on Ubuntu. I guess the windows drivers are just more up to date for this card? Thats why I was hoping there might be some simpler modification I could make, maybe something other that a driver. Its strange because I had a few games running and now those same ones wont even open. Just seeing some inconsistencies that dont really add up. Your response leaves little room for hope, but thats how it goes sometimes, lol. Thanks again for the help.

---

### Post by tbright on 2011-10-28
Well now that I think about it...
my card is integrated. no updating for me. 

Is there really NOTHING I can do?
the OS runs great but is there anything that could improve game compatibility/performance?

---

### Post by kaldor on 2011-10-28
The Radeon drivers (by Radeon I mean the open source default one) are the only ones available for that machine due to the age of your card. Sadly, game performance is not the best. Luckily though, the drivers are in active development and performance increases occur after every Ubuntu release (usually). 

But for now it looks like you're stuck with the open source ones. Though I have a similar card (xpress 300) and it works beautifully by default.

Edit: As for Windows games, you're most likely out of luck. Linux is not Windows, and in most cases Windows software will not run properly.

If you want a good Shooter, see if Urban Terror works well enough on your card. That's my favourite team based game :)

Edit 2:

ATI has a history for having very poor support for Linux. After being bought by AMD, things slowly improved. AMD has two different series of drivers: "Radeon" and Catalyst (aka fglrx).

Catalyst is a nearly bit-for-bit copy of the Windows driver. Some things are still hit and miss, but in most cases it works just as well as on Windows. But, only newer cards are compatible with this proprietary driver.

Radeon is the open source, community-driven (but funded by AMD) driver which is used by default in many Linux distros. Proprietary drivers are a huge problem for Linux due to the way they interact with the kernel (nutshelled). The open source drivers mesh together better with the OS as a whole and make things very stable, but their features are not nearly as good as the proprietary drivers. Development is active and continuous with breakthroughs now and then. The goal is to eventually provide complete support for all Radeon (as in the GPU, not open driver) cards, and since the project started in early 2008 it's going pretty well. I am quite optimistic that they will catch up in time. Someday, users will be able to boot their OS for the first time and never have to bother with display drivers at all. 

To an end-user, this probably just seems unimportant. But if you dig into Linux development you'll see why proprietary drivers are a problem and why it's important to have open drivers.

---

### Post by Jaybyrrd on 2011-10-28
Install the newest binary drivers developed for that card at the time (even if they are old, the newest for it). That could help possibly.

---

### Post by tbright on 2011-10-28
Yeah,
I dont want to play windows games, it just seems strange that I was playing windows games no problem, and now Im hung up on what seem to be graphically inferior games. But thanks for the help, I am seeing what my divers options are. Im actually not really that familiar with the open source drivers OTHER THAN what come automatically. Are there potentially others out there that are compatible and could work better?

---

### Post by Jaybyrrd on 2011-10-28
Like I said, there is a chance that you can use the Binary Drivers distributed by ATI for better performance, (it's possible but who knows). For more info go to:

 [http://ubuntuforums.org/showthread.p...nvidia+drivers](http://ubuntuforums.org/showthread.p...nvidia+drivers)

(Despite the lnk, this is not an nVidia Driver only thread, it actually handles many graphic issues involved with distribution upgrades).

---

### Post by kaldor on 2011-10-28
> **tbright said:**
> Yeah,
I dont want to play windows games, it just seems strange that I was playing windows games no problem, and now Im hung up on what seem to be graphically inferior games. But thanks for the help, I am seeing what my divers options are. Im actually not really that familiar with the open source drivers OTHER THAN what come automatically. Are there potentially others out there that are compatible and could work better?

I edited [_my post_]("http://ubuntuforums.org/showpost.php?p=11404750&postcount=9") with a short description of the driver situation.

Basically, Windows is using the official Catalyst driver. Your old card doesn't have the official drivers for Linux available anymore, so only the open source one is an option.

I **strongly** recommend not using outdated Catalyst drivers for stability's sake.

---

