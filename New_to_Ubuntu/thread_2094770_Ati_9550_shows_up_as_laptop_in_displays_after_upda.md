---
title: "Ati 9550 shows up as laptop in displays after update to 12.04"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by D_E_H0987 on 2012-12-14
My guess is this is on here somewhere but I have searched and even tried looking at bunch of other similar video problems and couldn't find a way that works.  
  My ATI 9550 shows up as laptop in displays after update to Ubuntu 12.04, how do I fix this?

I can't run 3d mode and Displays shows laptop and all the settings  but one won't work on my monitor.

I found the following command on another post "sudo lshw -c video". I get this when I run that command it shows, 

" *-display:0 UNCLAIMED
       description: VGA compatible controller        product: RV350 AS [Radeon 9550]        vendor: Hynix Semiconductor (Hyundai Electronics)        physical id: 0        bus info: pci@0000:01:00.0        version: 00        width: 32 bits        clock: 66MHz        capabilities: agp agp-3.0 pm vga_controller bus_master cap_list        configuration: latency=32 mingnt=8        resources: memory:c0000000-cfffffff ioport:c000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff   *-display:1 UNCLAIMED        description: Display controller        product: RV350 AS [Radeon 9550] (Secondary)        vendor: Hynix Semiconductor (Hyundai Electronics)        physical id: 0.1        bus info: pci@0000:01:00.1        version: 00        width: 32 bits        clock: 66MHz        capabilities: pm cap_list        configuration: latency=32 mingnt=8        resources: memory:d0000000-dfffffff memory:e5010000-e501ffff"


  This way more info than the command showed in he other post and as far as I can tell right. 
  This doesn't look to me like a laptop video would list?
  I also see this command "xrandr" it shows this,

"xrandr: Failed to get size of gamma for output default Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024 default connected 1280x1024+0+0 0mm x 0mm    1280x1024       0.0*     1024x768        0.0
   800x600         0.0
   640x480         0.0  "

  This is what basically shows in displays for resolutions but only the 1280x1024  works the others produce tearing in the video.
  I have tried ATI/AMD drivers the new one won't load and older ones  won't work.    I found out the newer driver no longer supports the 9550.

---

### Post by Mark Phelps on 2012-12-15
Sorry, but that's a very old video chipset and AMD dropped Linux driver support for it years ago.

---

### Post by D_E_H0987 on 2012-12-16
> **Mark Phelps said:**
> Sorry, but that's a very old video chipset and AMD dropped Linux driver support for it years ago.

Yea I found that out, I think that's why the 12.04 got messed up, I had tried to load ATI/AMD drivers on the older Ubuntu I updated, but they never worked, I think when I updated it tried to use the ATI driver.

I have found out I will have to get a new video card before I can do a 12.10 upgrade.

I would have stayed with 11.10 but I found I had to update to use some video editing software I wanted to run.

The Open source driver is said to work fine on the 9550 in 12.04, I just need to find out how to get the open source driver loaded on this critter.

I have tried a few terminal commands that were supposed to work but it would seem there is a change in 12.04 over 11.10 and as far as I can tell I need a different set of commands.   

OH by the way my 9550 is the ultra version, I haven't seen any info to show they are different as far as the open source driver for 12.04 though.

I'll keep looking, thanks for the reply.

---

### Post by D_E_H0987 on 2012-12-16
I finally crashed Ubuntu, it would launch, come up then flash, come up again and finally shut down.   So I got ticked, down loaded 12.04 ISO, burned a CD and am now in the process of reloading from scratch.    It will probably take me most of the next year to download stuff and get it back the way I had it.  OH well!

Next I'm gona have to figure out how to program, as this is BS, a bunch of old command line utilities that don't seem to be documented completely anywhere to configure a modern GUI operating system.   ROTFLMFAO!

I only found like a dozen different ways that were to get back to open source drivers, none of them worked, and the last one I found after spending hours on Google that was listed for Ubuntu 12.04 makes the system unusable.  

Its good the system was just for playing movies and such, as I don't think I would be reinstalling Ubuntu if I had lost something important.

If I had money I'd probably get a new computer and forget about the Linux idea but I'm poor and don't figure I'll be getting rich anytime soon.   With my luck I'll win the lottery the day after I die.

---

### Post by mastablasta on 2012-12-17
> **D_E_H0987 said:**
> I 
I only found like a dozen different ways that were to get back to open source drivers, none of them worked, and the last one I found after spending hours on Google that was listed for Ubuntu 12.04 makes the system unusable. 

 
did you follow the one on ubuntu help pages?

---

### Post by JHawk56 on 2012-12-17
Of course I cannot find it now, but a day or two ago I read in another forum that AMD/ATI had recently removed the 9550 from active driver support and now supports the card only through the legacy driver set. It went on to say that the core in Ubuntu 12.10 doesn't support the legacy drivers, so you have to stay with 12.04 if you want to run propietary driver. There was also some mention of using an OpenGL driver as an alternative, I think. I will continue to try to find the thread.

My own experience with the 9550, for what it's worth (I'm a Linux noob), was to start with 12.10. My display was identified as a laptop. Because I want to use full 3D drivers, and because it's not just my video card that is low-spec, I tried dropping back to 12.04, on Lubuntu. The installation is hanging, and shows signs of being a video issue.

---

### Post by JHawk56 on 2012-12-17
I got a few of the details wrong (for one thing, it's not specifically about the 9550), but here's the thread: 
[http://community.secondlife.com/t5/Second-Life-Viewer/Ubuntu-12-10-with-legacy-AMD-ATI-cards-to-play-SL/m-p/1708327#M16653](http://community.secondlife.com/t5/Second-Life-Viewer/Ubuntu-12-10-with-legacy-AMD-ATI-cards-to-play-SL/m-p/1708327#M16653)

Also, you might look at this if you haven't already: 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by mikewhatever on 2012-12-17
> **D_E_H0987 said:**
> ...

Next I'm gona have to figure out how to program, as this is BS, a bunch of old command line utilities that don't seem to be documented completely anywhere to configure a modern GUI operating system.   ROTFLMFAO!

I only found like a dozen different ways that were to get back to open source drivers, none of them worked, and the last one I found after spending hours on Google that was listed for Ubuntu 12.04 makes the system unusable.  



An open source Radeon driver should be used by default - no need to program or get back ... The [last proprietary driver release for Radeon 9550]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English") was in March 2009. That's almost four years ago, so, obviously, it won't work on any of the supported Ubuntu releases. Trying to install it is asking for trouble.

---

### Post by JHawk56 on 2012-12-17
> **mikewhatever said:**
> The [last proprietary driver release for Radeon 9550]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English") was in March 2009. That's almost four years ago, so, obviously, it won't work on any of the supported Ubuntu releases. Trying to install it is asking for trouble.I had just finished reading that same page when I saw your post, and was afraid of that...sigh.

@ D_E_H0987: I'm unclear what driver you were using successfully with 11.10. The native 11.10 driver? How did it work?

---

### Post by D_E_H0987 on 2012-12-19
> **JHawk56 said:**
> I had just finished reading that same page when I saw your post, and was afraid of that...sigh.

@ D_E_H0987: I'm unclear what driver you were using successfully with 11.10. The native 11.10 driver? How did it work?

I was using the native open source driver in 11.10, I had tried to load a newer ATI/AMD driver but never got it switched in, I think the problem was I downloaded a version of the ATI/AMD driver that was not for 11.10.  The 9550 on Ubuntu 11.10 in Unity 3d worked well on my old P4 2.8Ghz, with 1.5gig ram, using a swap partition, no video problems, videos and DVD's played well, you could run multiple apps at the same time, etc.

I think you should stay with the open source driver and read up on things to get your system configed right and get your system working well before even thinking of the ATI/AMD drivers.   I'm pretty cranky about systems that are click wait, click wait, that just bugs the hell out of me and I would not ever say a machine that was running that way was working fine.  I know people who can use a machine like that, but I would be pulling my hair out or tossing the machine out the window if I had to use a box that way.

You can do lots of things to speed up your system, things like removing background apps you are not using, for instance in my case I shut off bluetooth as I don't have a bluetooth interface in my computer so an app loaded and looking for bluetooth devices doesn't make much sense.  Then there are things like switching off some of the fancy special effects and then there is using swap partition, Ubuntu's install doesn't create one by default.  Also settings in "Open GL" for your video card can speed things up.  

From what I have read while meandering around the web while I was trying to get my video fixed after the 12.04 upgrade so it would work in 3D and have the right settings for my monitor, most of the posts on ATI/AMD drivers have basically the same info .   I had looked on Ubuntu forums, askUbuntu, Ubuntu.com, Google and other tech sites.   It ends up that "some people have good luck with the native driver and others need to get the right ATI/AMD driver for their system to work well".   From what I read It seems to be differences in the model of video card, differences in memory on the card, and other system options, from chip sets, to other cards, to on board devices, to system ram, etc.  that determines which driver will work best for you.

Here is a link to what I recall was the most informative or at least best worded explanation(best for me to understand and with things spelled out, and not just do this magic terminal command and it will work, yea right, and how much swampland are you trying to sell me.) of how to do the ATI/AMD video settings bit.  But don't use it if you can get the open source driver and your system configured to work well, as that is the safest way as ATI/AMD no longer supports the 9550 so upgrades, etc. will be hard to do.   This page is for Ubuntu 11.10(Some of the older versions too, I think.), this is not in any way shape or form for 12.04 or 12.10 as things have been changed.   These instructions will not work past 11.10, I found this out the hard way after crapping things up.    
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I think 12.04 will work fine on the 9550 but I'm still settings things up again and right now while it runs fast enough there are some qwerks, such as apps with video artifacts, and a weird Firefox problem(See below.).   I found info that 12.10 and up will not work in Unity 3d on the 9550, but some of the other Ubuntu's without Unity are said to work, but I have not seen them and don't know the people who said it works, so I can't tell if what they think is working is the same as I would say is working.


Ah well, its been a good learning experience.   

Something I will tell everyone to do is once ya get the critter the way you like it, make a backup, even if the machine hosts nothing important, as it takes forever to get things back the way you want them, and to load all the software you use. 

Now I figure if I knew more about Ubuntu and Linux in general I probably could have booted up another way, maybe the live cd or something, and got some of my settings and an App list to make redoing the system faster.    I was ticked when it stopped working and I had been getting frustrated by all the time wasted hunting for info and asking about all the mystic command line this and that, so I just said hell with it.   I had wasted too much time screwing around with this mess and so I downloaded the ISO and burned a new CD.  Its not like I was loosing more than the settings and config on the machine.   All the apps I had loaded can be reinstalled.    So it wasn't like I was loosing a bunch of work or something. 

I'm pretty good on coping off stuff to an archive drive that I need to save.  I like the newer ideas like software center.  But there is a benefit to the old way of download or pick up software and install it.   That is you have the program as long as you save the file or disk.   With things like software center, app stores, etc. you can still get everything back but it takes for fricken ever.

Something else I have learned after my killing Ubuntu is a swap partition on your hard drive is much better than a swap file.  I had read a bit on how to setup a Ubuntu system and found out about the swap partition bit, there wasn't any info about the swap file bit in that document or I mite have tried that.   Latter I found out about the swap file bit, I thought it mite be a better way, then I'd just have one big partition and if disk space got low I could cut the swap file down a bit.  But in running Ubuntu both ways now I know the swap partition works better than a swap file.   I have no clue why, but its a lot faster on a partition, then as a file on the same drive.  You end up with a lot of lags when running several apps all at the same time with the swap file, something I never saw when I had a swap partition.   I have another drive that was in the machine,  I took it out as I had a few things saved on it and didn't want them getting hosed when I reinstalled Ubuntu.   I'll save the files somewhere else and partition the drive with a swap partition  and then change from the swap file to the swap partition as it works a lot better.  

The 12.04 seems to use the same install program as 11.04, 11.10, I really think it needs to be fixed.   The Ubuntu installers partition app defaults to setting up a 1 gig partition and no swap and leaves most of the drive unpartitioned.   Why it was setup this way is beyond me, it simply makes no sense, its not a usable config as there is no room for more apps or even things one creates or downloads.    Also why the partition app in the installer doesn't explain the partition types and boot types doesn't make much sense either.   And then we have little qwerks in the installer like the screen switching on and off, and the mouse working and then not.   The most troublesome thing is the installer asks for some info but as your typing the screen pops off.    Maybe they figure your on a system with 4 processors, each with 12 cores or something, but the installer should not need more processing power than the operating system its installing.   And while it may show your programing skills, doing things in the background while people are filling in a form is a pain in the "bleep".


While looking up config settings like getting rid of those annoying new style scroll bars, etc. I noticed a little weird problem in Firefox, on popup windows, like saving a bookmark, the little box that pops up is invisible and the only way you know it popped up is it makes kina a shadow/highlighted box.   Its funny if you move your mouse around in the box, stuff is there, as you can get the mouse pointer to change to a text prompt but since nothing is visable its useless.   Also the machine seems to switch into slow motion or is running something in the background while this blank box is on the screen as the mouse moves sluggish, the menus don't popup and when you push "Esc" it will remove the box but it takes forever, once the box is gone things are back to normal.

I'll have to make a post for it if I don't find anything,  I want to spend a bit more time looking though, it was late last night and I was tired so I went to bed.


OH and sorry for the long winded post, I seem to do that far too often.

---

### Post by mastablasta on 2012-12-19
> **D_E_H0987 said:**
>  
I think you should stay with the open source driver and read up on things to get your system configed right and get your system working well before even thinking of the ATI/AMD drivers. I'm pretty cranky about systems that are click wait, click wait, that just bugs the hell out of me and I would not ever say a machine that was running that way was working fine. I know people who can use a machine like that, but I would be pulling my hair out or tossing the machine out the window if I had to use a box that way.
to keep opensource drivers to latest version you can use xorg edgers PPA.
 
> 
and then there is using swap partition, Ubuntu's install doesn't create one by default. 

It created one for me: ram x 2
 
 
> 
... It ends up that "some people have good luck with the native driver and others need to get the right ATI/AMD driver for their system to work well". From what I read It seems to be differences in the model of video card, differences in memory on the card, and other system options, from chip sets, to other cards, to on board devices, to system ram, etc. that determines which driver will work best for you.

yes, it works well on supported cards. you card's support (as well as mine) got dropped by ATI.
 
 
 
> 
The 12.04 seems to use the same install program as 11.04, 11.10, I really think it needs to be fixed. The Ubuntu installers partition app defaults to setting up a 1 gig partition and no swap and leaves most of the drive unpartitioned. [etc] 

 
i never had the installer issues you are talking about. are you sure you have a good image download (md5sum checks out)?
 
i did have once ATI 9600 XT recognised as ATI mobility radeon. however one of the updates seems to have fixed that. if oyu hav/see an issue bug report it on launchpad. it cant'/wont' get solved unless someone that is "crushing bugs" doesn't know about it.

---

### Post by D_E_H0987 on 2012-12-19
> **mastablasta said:**
> ...snip...
i never had the installer issues you are talking about. are you sure you have a good image download (md5sum checks out)?
 

Since its two different versions of Ubuntu 11.04 and 12.04 and two different CDROM's I have burned, and both do exactly the same thing.  It doesn't make sense that it is a bad ISO download and I'm sure its not two bad ISO downloads.  I'll bet the odds against two bad downloads of two different ISO's of two different versions of Ubuntu producing the same effects is billions to one.  

It maybe a difference in where the download was from, I got mine direct from Ubuntu.com and used the 32bit desktop version.  There are several versions on Ubuntu's download page.   Or it simply mite be you use the partitioning app and create your own partition scheme and don't even think of it, I know I do this on windows, I've had people go "hey what are you doing there"' while I was setting up a new windows system.   I started back in the day and just do things, but what I do is far from what the average windows user does.   And what you mite do on installing Ubuntu mite be something far different than I did as a new user just clicking the defaults.   It may also be something to do with the system, the amount of ram, or config, or .... as to why the partition app does different things.

Others have mentioned the problem with the installer creating the 1gig partition (I'm sure the developers of Ubuntu know about it as its an old problem.),  one of those posts is where I got the information on putting in a swap partition.   

It could be something to do with a raw drive versus a used windows drive that makes the difference in the partition app.   When I select the option that pops up "use the whole drive and delete everything."  the partition app should at least make one big partition that is the full size of the drive not a one gig partition.   If there was more infomation in the partition app it wouldn't matter if there was something it finds on some systems that causes the one gig partition to be created, as people would know up front to use the "something different" option and create a partition scheme that works.   Anyway I just ran the 12.04 at defaults to see if it was still the same and the partition app produces the 1gig partition by default.   I know to do things different now but people should not have to read up on how to configure a partitioning app that is part of a modern install installation.

According to things I have read the video the 9550 is fully supported in Ubuntu 11.04 and 11.10.  In 12.04 its only supported on the open source driver.  And on 12.10 it is not supported at all.  There are other versions of Ubuntu 12.10 like Lubuntu and Edubuntu that still support the 9550.  And while it is not supported, it is possible to use an old ATI/AMD driver in 12.10 there are a few different posts around on the web that tell how to do it.

I'm gona look for a little newer video card, but not for a month or two as prices are way up for Christmas as always.  The 9550 was a lower end video card and out of date when new, so its showing its age.

---

### Post by mastablasta on 2012-12-20
> **D_E_H0987 said:**
>  
According to things I have read the video the 9550 is fully supported in Ubuntu 11.04 and 11.10. In 12.04 its only supported on the open source driver. And on 12.10 it is not supported at all. There are other versions of Ubuntu 12.10 like Lubuntu and Edubuntu that still support the 9550. And while it is not supported, it is possible to use an old ATI/AMD driver in 12.10 there are a few different posts around on the web that tell how to do it.

 
you read wrong. it's support was dropped after 9.10. opensoruce driver is still supporting it.

---

### Post by JHawk56 on 2012-12-20
> **D_E_H0987 said:**
> According to things I have read the video the 9550 is fully supported in Ubuntu 11.04 and 11.10.  In 12.04 its only supported on the open source driver.  And on 12.10 it is not supported at all.
> **mastablasta said:**
> you read wrong. it's support was dropped after 9.10. opensoruce driver is still supporting it.
Yes, my 9550 worked in Ubuntu 12.10 with the native driver, albeit in 2D.

Looks like we've been working in parallel, reading the same resources! Difference is, you started with earlier Ubuntus and are trying to work your way forward; I started with 12.10 and am working my way backward. As I said, 12.10 was fine for 2D. I switched to Lubuntu for the 12.04, and am having problems that may be video related, which would surprise me unless Lubuntu contains fewer native drivers (which I doubt). But I'm actually more eager to try 11.10 anyway, based on your experience.

Overall it looks like getting good 3D from a recent Ubuntu distro with a 9550 is a daunting task. I'd also like to try the ATI driver, but it appears it only works with x.org 7.4 at the latest. As far as I can determine, that means Ubunto no newer than 9.04 (I could be off a bit; I notice mastablasta says 9.10 and he likely knows better than I do). I'm wondering about the downsides of running so old a version.

---

