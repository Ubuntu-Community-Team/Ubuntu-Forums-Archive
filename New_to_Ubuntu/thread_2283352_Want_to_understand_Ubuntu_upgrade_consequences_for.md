---
title: "Want to understand Ubuntu upgrade consequences for apps"
date: 2015-06-21
forum: New to Ubuntu
---

### Post by Advait on 2015-06-21
Hi All,

I searched the forums re this and didn't find any relevant threads. If there's a thread about this please reply with the link. 

I'm kind of a newbie so please answer with that in mind. I'm thinking of getting a new laptop and switching from Windows to Ubuntu. Every 6 months a new version of Ubuntu comes out. If I install a new version of Ubuntu does that wipe out all my apps such that I need to reinstall all of them? Or can I upgrade to a new Ubuntu version and all of my apps will continue working as normal? Is it rare for an app to not work with a new version? Or pretty common? I'm not a power user and will only use some common popular apps like LibreOffice, gimp, Chrome, VLC, Audacity, LAMP, etc...

If I remember correctly each new Ubuntu release uses the latest kernel. Does upgrading the kernel mean that I have to start from scratch and reinstall all my apps and settings? 

I want to see if doing an Ubuntu upgrade involves a lot of work.

Thanks,

---

### Post by nerdtron on 2015-06-21
Well it's true that Ubuntu releases a new version every 6 months, but not all releases are equal. There are Long Term Support release, 12.04, 14.04 are LTS release that are supported for 5 years while other releases like 14.10 and 15.04 are only supported for 9 months. 
When a release is no longer supported, you'll lose the ability to update your installed applications and install security patches, people on the forums will not be able to support you either if you use an "end-of-life" version. So  you may want to stick with LTS releases, currently Ubuntu 14.04 is a good choice.

As for kernel updates, if you only update the kernel from the software updater, you don't need to reinstall your apps. You can also rollback to a lower kernel version since old kernels are not deleted automatically.

---

### Post by sudodus on 2015-06-21
It is possible and sometimes encouraged to upgrade to the next (and newer) version as soon as it is released. It works sometimes at once - particularly if you have updated/dist-upgraded everything within the current version and removed PPAs and special programs, you have installed manually. Programs installed from the Ubuntu repositories are OK, and will normally survive. Often you need to tweak some settings (again) to make it work after an upgrade to the next (and newer) version.

But I would recommend that you install a long time release (LTS) and skip the other versions. The current LTS versions are Ubuntu 12.04 and 14.04 (with point releases ***12.04.5*** and ***14.04.2*** right now). Ubuntu 12.04 was released in April 2012 and is supported until April 2017, and Ubuntu 14.04 was released in April 2014 and is supported until April 2019. The other current releases are supported for only 9 months.

Staying with LTS versions means that you should upgrade or re-install after 2 years or 4 years, and if you want stability, you should wait for the first point release, which comes in in July or August after 3-4 months of 'extra debugging' after the original release. We expect that the next LTS will be 16.04 to be released in April 2016.

---

### Post by grahammechanical on 2015-06-21
Upgrading from one release to the next does not normally remove applications. This is especially true of those applications that are part of a default install which will themselves be upgraded to newer versions.

A fresh install will require the re-installing of applications as it will format the partition that Ubuntu is on. It is always best to install applications from the Ubuntu Software Centre. If we download and install Linux applications from some web site or other we may need to re-stall them because they are not in the Ubuntu software repositories.

Before upgrading it is best to revert the user interface back to a default condition and to switch from using a proprietary video driver to the default open source video driver. A new Ubuntu version uses newer kernels and newer proprietary video drivers and you may find, as I have done, that the latest proprietary video driver has dropped support for older video cards.

It is the responsibility of software developers to maintain their software and make sure that it works on the new versions. Each new version of Ubuntu has undergone a 26 week development period. And that gives the developers plenty of time to test their software on the new version before it is released.

I, myself, at this moment am using the development version of Ubuntu 15.10 and I have no problems using Libreoffice and Firefox which are the two applications that I use every day.

Regards.

---

### Post by Bucky Ball on 2015-06-21
All of the above. Default apps will not be removed, others it is unlikely.

Update prior to the upgrade, switch off manually installed PPAs, think about a clean install on the new machine of an LTS release if you don't fancy upgrading in a month and a bit for 14.10 or next January/Feb for 15.04. 14.04 LTS is solid.

---

### Post by dino99 on 2015-06-21
When you install ubuntu, you have 2 choices:
- let the 'installer' doing the decisions for you: creating/setting the partitions then installing the OS and the default apps list
- or select the 'manual' installation (its my own choice)

With the first choice , the installer does not ask questions, as it decide itself for you. But i does not like its way because i prefer managing the processes myself and do the installation i like. I usually start by creating the required partitions by booting with 'gparted live' cd/usb:
- with hardware having a 'bios' (compared to recent having a 'uefi'), we cant set more than 4 'primary' partitions. So we usually create only the first one as 'primary' and the a big one as 'extended' into we then can create the other partitions without limitations.
- when 'gparted live' is booted, create 3 partitions: / (root) as ext4 and about 15 gb, swap about 4 gb, and finally /home as ext4 and as huge as you need for all your apps & settings.
- then you start the ubuntu installation, and when the installer will ask where to do the installation, select 'something else' option to reuse the previously created partitions.
- later the installer will ask where to set 'grub' (the boot loader), and you select /dev/sda

That is, the installation is complete, remove the cd/usb installation disk, and reboot. Depending on the graphic card/chipset used, sometime we need to manually set a better driver than the default one selected by the installer.

---

### Post by oldfred on 2015-06-21
One of the issues of very new hardware is how well is it supported. Vendors do not directly support Linux. Even Intel does, but it releases updates to kernel, support software & video drivers. But those updates have to be approved into each software and then each distribution has to add the approved software into its distribution. Depending on timing, it can take a release or two before newest hardware is well supported. Often some testing type users create easier ways (ppa) to download software that has been released but not yet into a distribution. And if very new hardware that may be required.

So it depends a lot on what system & model you buy. A high end bleeding edge system will all the bells & whistles may not fully work. But a middle of the road system with mostly standard hardware and a current version of Ubuntu should would well.

If a new system, you also need to read up on the differences between the old BIOS with MBR partitioning and the newer UEFI with gpt partitioning now used. Install is different.

I do prefer clean installs, but you have to export a list of applications and have a separate /home or good backup of /home, so you can easily reinstall all apps you have installed and restore settings & files in /home. Upgrades will reinstall all the same software, but as already mentioned, any proprietary drivers or ppas may prevent upgrade from completing correctly. 

Good backups always recommended whether upgrading or reinstalling.

---

### Post by Advait on 2015-06-21
Hi All, 

Thanks for the replies. Now I understand better. Let me try to summarize. Upgrading from one 6 month release to the next should go smoothly if I first consider/do the following:

* don't have any PPAs installed (I'm a simple user so I don't think I'll need PPAs)
* Only use apps from the official Ubuntu Repo (I'm a simple user so I think the official Ubuntu Repo apps will be all I need)
* Use official apps that use "standard" video drivers. (I don't think I'll have a need to install something with some other video driver. VLC should cover my needs.)
* Revert Unity back to its default state before upgrading to new release. (I like Unity so I probably will not change it much or replace it).
* Update all apps before upgrading to new release.
* Backup all user and data files. (I will probably also do a bit-for-bit full image backup)

What is an example of something that would have a non-standard proprietary video driver that would cause problems during a version upgrade? Examples would be helpful.

I'm a simple user - would I ever need to use a PPA? If yes, what would be a common example?

My goal is the ability to upgrade from one release to the next without spending time formatting and reinstalling everything. I prefer to do 6 month upgrades so I have the latest kernel. So I would likely upgrade every June and Dec.

I'm guessing that upgrading from one LTS to the next LTS is more difficult than upgrading to the next 6 month release? Is it true that upgrading from one LTS to the next LTS likely requires a format and fresh re-install of all apps?

I'm a newbie who does not know command line so keep this in mind when you reply. dino99's reply went over my head. Thanks.

---

### Post by oldfred on 2015-06-21
You should be able to directly upgrade from one LTS to another. It usually does not offer that for a while after the newer LTS is released.
But 2 years often has a lot of changes, so depending on what has changed, it may be different, or not.

I like to install in a 25GB / (root) partition the new version and test it. Then I know it works and what the major differences are.

The issue on video drivers is often nVidia or AMD. If you install the proprietary drivers, an update or new install will not reinstall those. Depending on changes the open source driver may work as it has a lot of updates, or you may still have to have the proprietary driver. If upgrading, you need to revert to open source drivers before upgrading.

---

### Post by nerdtron on 2015-06-22
> I'm a simple user - would I ever need to use a PPA? If yes, what would be a common example?

My goal is the ability to upgrade from one release to the next without  spending time formatting and reinstalling everything. I prefer to do 6  month upgrades so I have the latest kernel. So I would likely upgrade  every June and Dec.


I'm not using any PPA's on my system either. If you are contended with what the software center offers, there's no need for PPA's.

hhhhmmmmm why does a new user need to always update to the latest kernel? For example, Ubuntu 14.04 will also receive kernel update, just not the latest ones but willl have kernel patches along it's life cycle. 

As for "in-place" upgrades like upgrading every 6 months to the new ubuntu version without reinstalling, I'm still not convinced it's safe. Some users reported successful upgrades, some with minor issues, some are left with unbootable systems which can be hard to troubleshoot when you are a newbie user.

As for upgrading, I prefer to re-install every 6 months. I just dedicate a partition on my hard drive as the "data" partition where I save everything. Then when I need to upgrade to the latest Ubuntu, I just re-install the OS and still keep my "data" partition intact.

---

### Post by Bucky Ball on 2015-06-22
> **Advait said:**
> 
... if I first consider/do the following:

* don't have any PPAs installed (I'm a simple user so I don't think I'll need PPAs)
* Only use apps from the official Ubuntu Repo (I'm a simple user so I think the official Ubuntu Repo apps will be all I need)
* Use official apps that use "standard" video drivers. (I don't think I'll have a need to install something with some other video driver. VLC should cover my needs.)
* Revert Unity back to its default state before upgrading to new release. (I like Unity so I probably will not change it much or replace it).
* Update all apps before upgrading to new release.
* Backup all user and data files. (I will probably also do a bit-for-bit full image backup)



... then you'd be good to go! Video drivers don't come with each app. You use one video driver installed in the operating system that all the apps use. If you are using the open-source driver, great! :)

Run this command and we can have a look if you need us to:

```
sudo lshw -C network
```

Good luck. And yes, why not go LTS to LTS? Once every two years instead of every six months. :)

---

### Post by vasa1 on 2015-06-22
> **Advait said:**
> ...
My goal is the ability to upgrade from one release to the next without spending time formatting and reinstalling everything. **I prefer to do 6 month upgrades so I have the latest kernel**. ...
Why do you want the latest kernel? Even kernels of the LTS versions get security updates.

---

### Post by Bucky Ball on 2015-06-22
You want the latest kernel so you can have practice fixing and learn about Linux?

If you want the latest latest kernel, see [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/"). Install the daily build daily. You can't get more up to date than that.

---

### Post by Advait on 2015-06-24
> **nerdtron said:**
> hhhhmmmmm why does a new user need to always update to the latest kernel?

Just my nature ;) . . . If its not too much trouble, I always like having the latest and greatest (that includes the latest kernel and latest version of Ubuntu).

> **nerdtron said:**
> As for "in-place" upgrades like upgrading every 6 months to the new ubuntu version without reinstalling, I'm still not convinced it's safe. Some users reported successful upgrades, some with minor issues, some are left with unbootable systems which can be hard to troubleshoot when you are a newbie user.

As for upgrading, I prefer to re-install every 6 months. I just dedicate a partition on my hard drive as the "data" partition where I save everything. Then when I need to upgrade to the latest Ubuntu, I just re-install the OS and still keep my "data" partition intact.

Doesn't that take a long time to download and reinstall and configure all your programs and settings? Seems like a lot of work every 6 months. One of the nice things I hear about Windows 10 is that there will be no more major versions, just incremental upgrades. That way (supposedly) I would never need to rebuild my whole setup. Sweet.

I'll research and see how difficult it is to make sure Ubuntu installs to a certain partition during install. Before I research I'll ask if that's easy? Is it one of the choices during the standard install process? Or does it require some command line expertise? (which I don't have).

Thanks!

---

### Post by Advait on 2015-06-24
> **vasa1 said:**
> Why do you want the latest kernel? Even kernels of the LTS versions get security updates.

Mostly its that I prefer having the latest version of Ubuntu. I usually really like the tweaks and updates in each release. And the thought of having the latest kernel gives me a warm fuzzy. Just my nature . . . 

But if there's a chance an upgrade would wipe out my install then I may need to go with LTS. I may try the 6 month upgrade to see if there's problems and then switch to LTS if needed. I'll research the separate partition idea.

---

### Post by sudodus on 2015-06-24
You have what it takes to help developing Ubuntu or one of the community flavours (Kubuntu, Lubuntu, ... Xubuntu). Welcome to [iso-testing]("http://iso.qa.ubuntu.com/") and the discussions in [the development forum]("http://ubuntuforums.org/forumdisplay.php?f=427") :-)

---

### Post by nerdtron on 2015-06-24
> Doesn't that take a long time to download and reinstall and configure  all your programs and settings? Seems like a lot of work every 6 months.  One of the nice things I hear about Windows 10 is that there will be no  more major versions, just incremental upgrades. That way (supposedly) I  would never need to rebuild my whole setup. Sweet.

I'll research and see how difficult it is to make sure Ubuntu installs  to a certain partition during install. Before I research I'll ask if  that's easy? Is it one of the choices during the standard install  process? Or does it require some command line expertise? (which I don't  have). 

When I was exploring ubuntu, I was installing every 6 months since a lot of changes come on each release, now I don't see much difference so I stick with LTS release. And before that I was installing Linux Mint which have most of my applications pre-installed so I just add a few hours after the installation and I'm good to go.

Another recommendation here (although not for complete newbies, but not very advanced) is to install a rolling release distro like Debian. Install it once and just update indefinitely.
If you like to have the latest kernels and applications, then Arch linux would be worth a shot. Newbie friendly derivatives of Arch like ArchBang and Manjaro linux. They have GUI installers and are rolling release distros.

---

### Post by Advait on 2015-06-24
> **nerdtron said:**
> If you like to have the latest kernels and applications, then Arch linux would be worth a shot. Newbie friendly derivatives of Arch like ArchBang and Manjaro linux. They have GUI installers and are rolling release distros.

That's one of the side benefits of posting questions here; you experts give me all kinds of little tips and tricks that I would have never thought of. Thanks for this info.

*Question:* Does Arch, ArchBang and/or Manjaro include access to the Ubuntu Software Store GUI where I can click and easily download apps? I would only use a distro that had this capability. I like to try various apps and if I have to go thru all kinds of command line shenanigans to get and install them (and update them) then I would not use such a distro.

Only GUI point and click for me. Once I retire and have some free time then I'll sit down and learn the command line. Thanks,

---

### Post by Geoffrey_Arndt on 2015-06-25
So Advait, where do you think Windows got the "inspiration" for rolling releases (Linux), and for virtual desktops, (Linux), and for official software "repos" (aka software stores) . . (Linux & Apple), . . . the list could go on and on.

---

### Post by Bucky Ball on 2015-06-25
> **Advait said:**
> 

*Question:* Does Arch, ArchBang and/or Manjaro include access to the Ubuntu Software Store GUI ...

Arch is not a derivative of Ubuntu so no. They probably have their own package manager, but I am not au fait with Arch so hopefully someone else can help there. 

I also have no idea about the strength or vibrancy of their support community.

---

### Post by Advait on 2015-06-25
> **Geoffrey_Arndt said:**
> So Advait, where do you think Windows got the "inspiration" for rolling releases (Linux), and for virtual desktops, (Linux), and for official software "repos" (aka software stores) . . (Linux & Apple), . . . the list could go on and on.

I'm in total agreement. :-) MS is slowly getting a clue, which is good for everyone. It will take me a week or more to rebuild my system on Win10 and hopefully it will be the last time.

---

### Post by Advait on 2015-06-25
> **Bucky Ball said:**
> Arch is not a derivative of Ubuntu so no. They probably have their own package manager, but I am not au fait with Arch so hopefully someone else can help there. 

I also have no idea about the strength or vibrancy of their support community.

OK, thanks. Probably better for me to stick with the major distros that are newbie friendly.

---

### Post by newb85 on 2015-06-25
+1 nerdtron.  If the kernel you have installed from xx.04.0 works great on your hardware, what's the point in upgrading the hardware enablement stack?

---

### Post by newb85 on 2015-06-25
If I remember from my very short trial of Arch, it uses pacman instead of apt.

---

