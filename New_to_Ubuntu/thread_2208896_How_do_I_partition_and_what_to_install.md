---
title: "How do I partition and what to install?"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by 393 on 2014-03-02
I just wiped out my hard drive with Dban.  How do I format and how and with which Ubuntu download should I install with?

Any help would be appreciated.

Thanks.

---

### Post by Odyssey1942 on 2014-03-02
Welcome to ubuntu forums from another beginner, who learned early on that in order to get the best response, it is good to give some idea of the subject that you need help on in the Title. For example, "Need advice on which version of Ubuntu to use and how to install including formatting", or whatever you feel best summarizes your needs. Many of those who can help you will just skip over "Help" without reading your post.

Good luck.

---

### Post by deadflowr on 2014-03-02
> **393 said:**
> I just wiped out my hard drive with Dban.  How do I format and how and with which Ubuntu download should I install with?

Any help would be appreciated.

Thanks.

It helps to know the machine.
Otherwise I would recommend plain ole Ubuntu from [Ubuntu]("http://www.ubuntu.com/download/desktop").

Since the disk is now empty, let it install using the installers own automated partitioner.
(Usually the top option when asked where to install)

---

### Post by Odyssey1942 on 2014-03-02
Hopefully you will receive additional guidance from more knowledgeable members, but this to give you something with which to begin. I assume that you intend to install Ubuntu. This will be a decision that will be informed by your hardware, especially the amount of RAM and your CPU spec., which if you will provide will be helpful.

12.04 is a LTS (Long Term Stable) version, will be supported for some time yet (unsure exactly how long, but I think another year), and has the benefit of considerable problem solving experience over the almost two years already of it's life. I think the next LTS is 14.04. Those in-between 6 monthly releases have a short support life and are mainly of interest to those who are at the cutting edge.

Installation from a Live DVD, which you can make up by downloading the ISO and burning (using an ISO burner, different from normal DVD burning) to a DVD, will take care of the formatting, but you should probably choose EXT4 as your format. 

There are many posts on this subject so use the search function and read. The posts in the Beginner Section will mostly be easier to understand.

---

### Post by Linuxratty on 2014-03-03
Once you have installed, you need your restricted software so you can watch  flash videos,movies, and such. Propriety NIVIDA drivers are a must as needed. 
 A lot of stuff will already be there,but you can check out the software center to get programs you might find useful. There are equivalent programs to what Windows offers, and Steam for games.
 If you hit a snag,lots of people will help you round the bend,so hang tuff.

---

### Post by Odyssey1942 on 2014-03-03
When installing, be sure to have an ethernet cable connected, if available, and during the install, check the two boxes for updates, extra packages, etc that will come up on one of the installation pages. Ubuntu will go out and add a lot of stuff that you will have to do later through an update. 

BTW, if you are baffled by the Unity Interface that will be automatically installed, there is a version of Linux called Linux Mint which has two versions, one called Linux Mint Mate, the other is Linux Mint Xfce, but both create a user experience much more familiar to Windows users. I think that Xfce may be designed to sort of duplicate a Win 7 desktop and may make easier to get started with Linux. I have never installed, so don't know if the advice in the first paragraph applies. Probably someone can give you guidance on these if you ask for it.

There is also something called Gnome Classic UI which I learned on 10.04 and can be installed on Ubuntu 12.04 which will be more like Windows and less like Apple.

---

### Post by endlessinstant on 2014-03-03
I will direct you to this tutorial:[URL="http://www.wikihow.com/Install-Ubuntu-Linuxbecause"] [http://www.wikihow.com/Install-Ubuntu-Linux](http://www.wikihow.com/Install-Ubuntu-Linux)

[/URL]because it specifically uses Ubuntu 12.04 LTS as its example.   For your purposes, mainly look at the first part of the article that explains installation from a CD. 
  
You should know that there are two kinds of releases, standard releases and LTS releases.  Standard releases come out every six months and only have a nine month life cycle.   LTS releases come out every 18 months (taking the slot of a standard release) and have support for several years.  These releases are comparable to Windows versions.  So whereas you wait 2-3 years between Windows, with Ubuntu you get something new every six months, though the LTS releases tend to be the most substantial upgrades.   LTS releases are built specifically for stability and while they don't have the latest and greatest features, they typically run the best on any given set of hardware.   They are ~THE BEST~ place to start as you don't want to be debugging hardware quirks of the rolling releases while trying to learn the system.

---

### Post by BlinkinCat on 2014-03-03
Are you sure that Link works?

---

### Post by endlessinstant on 2014-03-03
No, I'm not lol.   

[http://www.wikihow.com/Install-Ubuntu-Linux](http://www.wikihow.com/Install-Ubuntu-Linux)

There is something screwy with my Chromium that I have only just noticed.  Had to post with Iceweasel to get formatting working right.   *mutter* I'll be debugging tonight

---

### Post by Bucky Ball on 2014-03-03
Welcome. LTS releases have five years support. 12.04 LTS is supported until April 2017. It is very stable and directly upgradeable to 14.04 LTS when it is released in April (and any time after that) via the Software Updater (or Update Manager in 12.04). A good place to start.

You can let the Ubuntu installer 'automagically' do its work, but you may not like the way it partitions the drive. If you'd rather manually partition, you can do that choosing 'Something Else' at the partitioning section. *_Very_* basic set up would be:

/ = Ubuntu, 15-20Gb fine, EXT4 filesystem;
/home = your personal data and settings, the rest of the drive (EXT4 filesystem) and leave enough room at the end for;
/swap = the equivalent of a Windows pagefile. 2Gb is fine, unless you intend to hibernate, in which case, make it the same size as your installed RAM (or a bit bigger). (Note: You don't need to choose a filesystem type for /swap; just allocate it as 'swap space' and it will do the rest.

And that's about it. Those mount points (/, /home, /swap) you will find as default mountpoints during the partitioning section of install.

Be aware that in a regular install (not UEFI) there is a four partition per each physical hard drive limitation. A way of getting around this is to create a large extended partition and then logical partitions inside that. Theoretically, there is no limitation to how many logical partitions you can have. Ubuntu will happily exist on a logical partition inside an extended.

Good luck. ;)

---

### Post by newb85 on 2014-03-03
> **Odyssey1942 said:**
> When installing, be sure to have an ethernet cable connected, if available, and during the install, check the two boxes for updates, extra packages, etc that will come up on one of the installation pages. Ubuntu will go out and add a lot of stuff that you will have to do later through an update. 

BTW, if you are baffled by the Unity Interface that will be automatically installed, there is a version of Linux called Linux Mint which has two versions, one called Linux Mint Mate, the other is Linux Mint Xfce, but both create a user experience much more familiar to Windows users. I think that Xfce may be designed to sort of duplicate a Win 7 desktop and may make easier to get started with Linux. I have never installed, so don't know if the advice in the first paragraph applies. Probably someone can give you guidance on these if you ask for it.

That's not entirely complete.  The Mint download site has versions of Mint with Cinnamon, Mate, KDE and XFCE.  Unless you download a version labelled "OEM" or "no codecs", the audio/video codecs you need to play restricted formats will be automatically included without your needing to install them.  On the other hand, there are some other differences between the way Mint and Ubuntu work, and if you have trouble in those areas with Mint, you won't find the Ubuntu forums near as helpful.

Meanwhile, Cinnnamon, KDE, and XFCE are all included in the Ubuntu repositories.  That means that if you install Ubuntu and then decide you want one of those other Desktop Environments, you can simply install the DE you want from the Software Center (which works a lot like Apple's App Store or Android's Play Store).  You aren't permanently tied down.

---

### Post by Bucky Ball on 2014-03-03
> **newb85 said:**
> ... if you have trouble in those areas with Mint, you won't find the Ubuntu forums near as helpful.



In fact, Linux Mint is not officially supported on these forums at all, although you can try your luck for support in the 'Other OS Support' section. Linux Mint has an active forum of its own for support questions, though.

---

