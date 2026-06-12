---
title: "Trying to make the switch from Mac to Ubuntu"
date: 2014-11-06
forum: New to Ubuntu
---

### Post by linuxguy2 on 2014-11-06
I'm not new to Ubuntu, but I am finally trying to make the full switch from the Mac. There are tree main issues keeping me on the Mac, however. I was hoping the community here could direct me to some viable alternatives.  These are:  1.) A way of syncing my music collection with my iPod: I tried running iTunes via WINE and it didn't work.  2.) A way of converting sound files to MP3s via the Fraunhofer MP3 encoder: I currently do so with iTunes- LAME does not cut it for what I need.  3.) A replacement for Photoshop Elements: I have limited experience with GIMP, but don't get the idea that it is a proper replacement.  Thank you!

---

### Post by whitesmith on 2014-11-06
My thoughts:

(1) iTunes is notoriously proprietary and throughly uncooperative with Wine. If you browse iTunes in Wine's database of applications ([https://www.winehq.org/search?q=itunes](https://www.winehq.org/search?q=itunes)), you'll see that most versions are listed as unsupported -- known **not** to work.
(2) The Fraunhofer MP3 encoder is totally unknown to me. Sounds high-endish, though. I do my listening through a really high-end system (all computer-controlled with EAC/flac/Audacity/Clementine) so mp3s aren't my issue. FLACs are, and there's a converter in Audacity for just that, as well as many standalone converters. I've scoped them all with borrowed lab equipment and stand convinced they're more or less equivalent. Quality is simply flawless no matter how you go. FLAC is definitely for perfectionists since Some Assembly is Required. If you love music, as I do, it's worth every second.
(3) I use GIMP all the time; it does everything I want or need. Perhaps the community can assist you in comparing it to Elements, which was never my cup of tea.

I hope this point is at least a beginning and wish you the best of luck.

---

### Post by mastablasta on 2014-11-07
using proprietary locked down software and not prepared to use any alternatives (as in similar but not the same) - I would say stay with Mac OS. it's a descent OS. why do you want to switch?

---

### Post by Bucky Ball on 2014-11-07
> **mastablasta said:**
> using proprietary locked down software and not prepared to use any alternatives (as in similar but not the same) - I would say stay with Mac OS.

If this is the case, might be the best plan. Or dual-boot. I still dual-boot on the desktop with XP for audio/video. Have Win7 on the laptop just ... cos! Gets used about .5% of the time for specific things, and there's not many of them.

---

### Post by buzzingrobot on 2014-11-07
I used Macs for years for photo work. As far as I know, no direct replacement for Photoshop Elements exists for Linux. Gimp, like full-fledged Photoshop, is considerably more than a photo editor, with a similar learning curve. If you work with RAW images, there are a number of pretty good Linux tools that are actively developed and maintained. One I like is Darktable ([http://www.darktable.org/](http://www.darktable.org/)), which is in the Ubuntu repositories and from the developer's PPA (check the site). The PPA will have the most recent release.

A few useful sites rounding up using open source tools in photography exist. Googling something like "open source photo processing" or "open source photography" will find them.

---

### Post by Mark Phelps on 2014-11-07
> trying to make the full switch from the Mac.

Unfortunately, you're running into the same dependencies that forces some of us to keep Windows around in dual-boot mode -- some native applications for which there is no drop-in replacement in Linux.

As I continue to keep and use Windows for the few apps I really need, my recommendation to you is to keep the Mac SW around in dual-boot mode. That way, you can have the best of both worlds.

---

### Post by JayKay3OOO on 2014-11-07
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

A way to synch your iphone. It's not easy though.

[https://uk.answers.yahoo.com/question/index?qid=20130813143843AAyqZSX](https://uk.answers.yahoo.com/question/index?qid=20130813143843AAyqZSX)

Quick comparison of gimp and ps. I'm no pro editor, but it's the only image editor on Windows, Mac and Linux that I use. It's still a pain to learn it with a confusing arrangement of menus. Even if it's not better. It's about the best fee image editor for Linux. 

FLAC is the best audio container, but file sizes are quite big. I converted 90% of my music library from CD to mp3 using Linux and some in flac (before I decided my low end equipment can't tell the difference) without any problems. k3b is fairly good for general ripping. It can do flac too, but you might need to sudo apt-get install flac at the terminal prompt.

K3b is also good for backing up your DVDs once you have libdvdcss (search for it, it's super easy) installed.

Overall I have Windows in a virtual machine on my Linux server. I find it useful now and again. I would advise you run Linux in a vm or parallels to really get a feel for it and learn the free applications. I've switched from Linux to Windows several times and have only now after about 3 years decided that my work flow is compatible with Linux. I still need to know Windows and to a lesser extent Macs for work, but if what you use now works then why change?  

I'd stick with the mac. You're using the 'if Linux had lots of money' os and it works great (inb4 unix).

The grass is not always greener.

My current solution was to install Linux Server version (its a barebones ubuntu) and then drop on the KDE desktop, gnome and unity with a set of applications I'm familiar with. I sometimes like to work in KDE, other days gnome and the odd month unity.

Have fun though.

---

### Post by buzzingrobot on 2014-11-07
IMO, both Gimp and Photoshop are much less than ideal choices for the kind of photo processing typically done by anyone who doesn't earn a living at it, and perhaps even then.  In both, photo processing represents only a small portion of their toolset, most of which is geared to graphics and preproduction

Excellent photo tools exist for OS X from vendors other than Adobe, happily..  That's why I used them for years.  However, today, I would not buy a Mac just to process photos.  Ymmv.

---

### Post by linuxguy2 on 2014-11-08
> **whitesmith said:**
> My thoughts:  (1) iTunes is notoriously proprietary and throughly uncooperative with Wine. If you browse iTunes in Wine's database of applications ([https://www.winehq.org/search?q=itunes](https://www.winehq.org/search?q=itunes)), you'll see that most versions are listed as unsupported -- known **not** to work.  I don't need iTunes specifically. I just need something or some things that will do the same thngs for me: sync with my iPod and encode MP3s.  > (2) The Fraunhofer MP3 encoder is totally unknown to me.  As far as Fraunhofer, it's not about my personal preference. It is simply part of the some work I do- where MP3s are prefferred for thier ubiquity, rather than other, superior audio formats.  > (3) I use GIMP all the time; it does everything I want or need. Perhaps the community can assist you in comparing it to Elements, which was never my cup of tea.  I don't care for some of Elements' "features" either- but the ones I need are there and are easy to use. Frankly, I use quite an old version. I won't upgrade because I don't believe in renting software, which is what Adobe does now. I will have to gain some more experience with GIMP, but I was just wondering if there was anything else out there that might compare.  > I hope this point is at least a beginning and wish you the best of luck.  Thanks  > **mastablasta said:**
> using proprietary locked down software and not prepared to use any alternatives (as in similar but not the same) - I would say stay with Mac OS. it's a descent OS. why do you want to switch?  Why do you assume that? I clearly stated in my post: "There are tree main issues keeping me on the Mac, however. I was hoping the community here could direct me to some viable alternatives."  I have been a hobby Linux user for a long time (I've tried many distros, but have stuck with Xubuntu since probably before the switch to Unity and certainly after), and a Mac user for even longer (pre-Mac OS X). The Mac has served me well. But Apple is just moving in the wrong direction for me now, with locked-down, un-upgradable systems and so on. Linux is less polished, but more free and I can run it on any hardware I desire.  Still, moving from having Linux be a hobby to it being my main system is not a trivial thing, and I need to be sure I have alternatives for the tools I use regularly.  > **Bucky Ball said:**
> If this is the case, might be the best plan. Or dual-boot. I still dual-boot on the desktop with XP for audio/video. Have Win7 on the laptop just ... cos! Gets used about .5% of the time for specific things, and there's not many of them.  Dual-booting is an option- But not really ideal. If I am going to have to dual-boot to Mac OS regularly to sync my iPod and encode MP3s, I figure I might as well just continue using it as my main OS. These are not once-in-a-while activities. If they were (such as those things you do with XP) then it'd be a lot more doable. Frankly though, I hate having my data sprawled about two systems.  > **buzzingrobot said:**
> I used Macs for years for photo work. As far as I know, no direct replacement for Photoshop Elements exists for Linux. Gimp, like full-fledged Photoshop, is considerably more than a photo editor, with a similar learning curve. If you work with RAW images, there are a number of pretty good Linux tools that are actively developed and maintained. One I like is Darktable ([http://www.darktable.org/](http://www.darktable.org/)), which is in the Ubuntu repositories and from the developer's PPA (check the site). The PPA will have the most recent release.  A few useful sites rounding up using open source tools in photography exist. Googling something like "open source photo processing" or "open source photography" will find them.  Thank you- I will look into those programs.  > **JayKay3OOO said:**
>  I'd stick with the mac. You're using the 'if Linux had lots of money' os and it works great (inb4 unix).  The grass is not always greener.  I have to say I am a bit taken back by these responses. Maybe I have been away from the forums for a while, these aren't the typical responses I expected. Perhaps the average Linux user is a bit different these days. I can certainly get your point, though.  > **buzzingrobot said:**
> IMO, both Gimp and Photoshop are much less than ideal choices for the kind of photo processing typically done by anyone who doesn't earn a living at it, and perhaps even then.  In both, photo processing represents only a small portion of their toolset, most of which is geared to graphics and preproduction  Excellent photo tools exist for OS X from vendors other than Adobe, happily..  That's why I used them for years.  However, today, I would not buy a Mac just to process photos.  Ymmv.  Honestly, my use is not mostly for photos. It's occasional web and print graphic design.  Thank you for all the replies. I will continue to check back here.

---

### Post by Bucky Ball on 2014-11-08
Thankyou for your thorough response, linuxguy2. As for converting audio, may i recommend Sound Converter. It is a gnome app and may drag in a few things, but will change anything to anything, just about. One step beyond is perhaps Audacity. Both are available from Software Centre or Synaptics.

---

### Post by Impavidus on 2014-11-08
> **linuxguy2 said:**
> Frankly though, I hate having my data sprawled about two systems.That's why we can have shared data partitions. You can make a partition on your hard drive for your mp3s and access it from both systems. Without installing extra tools, FAT32 format is the only partition type available for reading and writing in both Linux and Mac.

Edit: It seems Mac nowadays supports some more. You may have to look into which file systems it supports and whether you need to install additional software to get read-write access.

---

### Post by sudodus on 2014-11-08
> **linuxguy2 said:**
> >                      [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **whitesmith**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13161635#post13161635")                 

(3) I use GIMP all the time; it does everything I want  or need. Perhaps the community can assist you in comparing it to  Elements, which was never my cup of tea.
I don't care for some  of Elements' "features" either- but the ones I need are there and are  easy to use. Frankly, I use quite an old version. I won't upgrade  because I don't believe in renting software, which is what Adobe does  now. I will have to gain some more experience with GIMP, but I was just  wondering if there was anything else out there that might compare.


I use ***gimp***, it takes time to learn, but can do a lot, so together with the tools for RAW images (mentioned by buzzingrobot) and ***inkscape*** for vector graphics, I think you have enough tools in linux. There are also good tools for batch processing of images, for example ***ImageMagick***.
> 

> **Bucky Ball said:**
> If this is the case, might be the best plan.  Or dual-boot. I still dual-boot on the desktop with XP for audio/video.  Have Win7 on the laptop just ... cos! Gets used about .5% of the time  for specific things, and there's not many of them.  Dual-booting  is an option- But not really ideal. If I am going to have to dual-boot  to Mac OS regularly to sync my iPod and encode MP3s, I figure I might as  well just continue using it as my main OS. These are not  once-in-a-while activities. If they were (such as those things you do  with XP) then it'd be a lot more doable.

There are many tools for ***making mp3*** files in linux, tools for single file jobs and tools for batch processing. This is the the smallest problem. Connecting to the iPod might be more cumbersome.
> 
Frankly though, I hate having  my data sprawled about two systems.

This should be no problem. In a dual boot system, you can have a common ***data*** partition with a file system, that can be read by both operating systems. That way you can keep your data separate from the operating system(s). It also makes the backup of the data easy to do.
> 
> **buzzingrobot said:**
> I used  Macs for years for photo work. As far as I know, no direct replacement  for Photoshop Elements exists for Linux. Gimp, like full-fledged  Photoshop, is considerably more than a photo editor, with a similar  learning curve. If you work with RAW images, there are a number of  pretty good Linux tools that are actively developed and maintained. One I  like is Darktable ([http://www.darktable.org/](http://www.darktable.org/)),  which is in the Ubuntu repositories and from the developer's PPA (check  the site). The PPA will have the most recent release.  A few useful  sites rounding up using open source tools in photography exist. Googling  something like "open source photo processing" or "open source  photography" will find them.  Thank you- I will look into those  programs.  > **JayKay3OOO said:**
>  I'd stick with the mac. You're  using the 'if Linux had lots of money' os and it works great (inb4  unix).  The grass is not always greener.  I have to say I am a  bit taken back by these responses. Maybe I have been away from the  forums for a while, these aren't the typical responses I expected.  Perhaps the average Linux user is a bit different these days.
I can  certainly get your point, though.

Maybe we have discussed with too many ambivalent people, who are not ready to leave the tools they know and like. Maybe we also think that it is difficult to perform some tasks in linux. It makes it easy to keep all doors open with dual boot systems (or to run the less used system in a virtual machine if it is legal). Particularly if you need ***advanced professional application programs*** or access to some ***peripheral devices***, that do not work properly with linux because the manufacturer does not provide [good] linux drivers.
> 
> **buzzingrobot said:**
> IMO,  both Gimp and Photoshop are much less than ideal choices for the kind of  photo processing typically done by anyone who doesn't earn a living at  it, and perhaps even then.  In both, photo processing represents only a  small portion of their toolset, most of which is geared to graphics and  preproduction  Excellent photo tools exist for OS X from vendors other  than Adobe, happily..  That's why I used them for years.  However,  today, I would not buy a Mac just to process photos.  Ymmv.   Honestly, my use is not mostly for photos. It's occasional web and print  graphic design.  Thank you for all the replies. I will continue to  check back here.


---

### Post by Thee on 2014-11-08
> I don't care for some of Elements' "features" either- but the ones I need are there and are easy to use.
What are the features that you use? I am sure they can be found in GIMP too.
If you want free, there is no better alternative to GIMP. There are however some similar paid software for Linux.

---

### Post by Bucky Ball on 2014-11-08
> **Impavidus said:**
>  FAT32 format is the only partition type available for reading and writing in both Linux and Mac.

Not quite. NTFS, BTRS (I think it's called) and I think there is a couple more. FAT32 is the most archaic and inefficient.

---

### Post by Impavidus on 2014-11-09
> **Bucky Ball said:**
> Not quite. NTFS, BTRS (I think it's called) and I think there is a couple more. FAT32 is the most archaic and inefficient.
OK, I must have been reading outdated information.

---

### Post by Bucky Ball on 2014-11-09
I use NTFS for all shared data partitions (in fact, just one which all my installs are symlinked to). ;) All good. We're here to learn and expand.

---

### Post by oldrocker99 on 2014-11-09
> **Thee said:**
> What are the features that you use? I am sure they can be found in GIMP too.
If you want free, there is no better alternative to GIMP. There are however some similar paid software for Linux.

The money you pay for Photoshop does include automation of various tasks. One example is rotating a picture. In Photoshop, you draw a line on, say, the croooked horizon, and select the Rotate command, and that's it. In GIMP, you select the grid, then align the picture. GIMP does 99% of what Photoshop does, it is true, but, as I said, you do have simpler and faster tools.

Not that I use Photoshop any more; GIMP is more than suitable for my graphics editing.

---

### Post by mastablasta on 2014-11-10
> **linuxguy2 said:**
> Why do you assume that? I clearly stated in my post: "There are tree main issues keeping me on the Mac, however. I was hoping the community here could direct me to some viable alternatives."  I have been a hobby Linux user for a long time (I've tried many distros, but have stuck with Xubuntu since probably before the switch to Unity and certainly after), and a Mac user for even longer (pre-Mac OS X). The Mac has served me well. But Apple is just moving in the wrong direction for me now, with locked-down, un-upgradable systems and so on. Linux is less polished, but more free and I can run it on any hardware I desire.  

Mac has always been locked down system. it's not really moving anywhere it was like that before. 

also I assume since you have a "must have" applications and hardware that is connected to some of those apps and locked down.

---

### Post by pfeiffep on 2014-11-10
> **linuxguy2 said:**
> I'm not new to Ubuntu, but I am finally trying to make the full switch from the Mac. There are tree main issues keeping me on the Mac, however. I was hoping the community here could direct me to some viable alternatives.  These are:  1.) A way of syncing my music collection with my iPod: I tried running iTunes via WINE and it didn't work.  2.) A way of converting sound files to MP3s via the Fraunhofer MP3 encoder: I currently do so with iTunes- LAME does not cut it for what I need.  3.) A replacement for Photoshop Elements: I have limited experience with GIMP, but don't get the idea that it is a proper replacement.  Thank you!I made a similar decision about switching from Microsoft Windows to Ubuntu a couple of years ago. I finally gave up and took a pragmatic approach - settled on dual booting my main HP tower because I was unable to find a personally suitable Linux replacement for:[INDENT]Photo Shop Elements
iPhone sync
Tax Preparation[/INDENT]
I have yet to decide about sound manipulation - I currently use Roxio but have dabbled with a couple Linux alternatives.

---

### Post by mastablasta on 2014-11-11
> **pfeiffep said:**
>  I finally gave up and took a pragmatic approach - settled on dual booting my main HP tower because I was unable to find a personally suitable Linux replacement...

oh yes, that is the way to go especially if you do not use those programs too often.

---

### Post by Bucky Ball on 2014-11-12
Good plan.

---

### Post by Bloodcage on 2014-11-12
All you have to do is get used to Ubuntu. There are so many possibilities and even I have switched from Win 7 on my netbook and win 8 on my desktop to ubuntu because I always found an advice or a solution to get the programs I need to work. And Linux especially ubuntu (maybe linux mint 17 LTS too) are the best systems to me now. 
I've had many things to consider about but it was definitely the best decision.
Gimp is a very powerful tool and for all the rest you wrote about, there are many sides and groups you can ask for and I'm sure you'll find a solution. Besides, the frauenhofer mp3 codec is one standart in ubuntu if you install the codecs pack and there are many media-programs which are able to convert, record or whatever you want to do.

---

