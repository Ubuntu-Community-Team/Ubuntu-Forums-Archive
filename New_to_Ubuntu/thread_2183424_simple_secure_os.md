---
title: "simple secure os"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by omniaparatus on 2013-10-24
hey guys im looking for a simple secure os that will let me surf most websites,  watch youtube videos and possibly online banking and do it securely using a vpn or whatever.

i bought the newest ubuntu but i couldnt get it to install in my system.
i tried dozens of times but it wouldnt take.

so is open bsd or trusted bsd a better choice?
i want to install it on a newer laptop  and high powered desktop

---

### Post by omniaparatus on 2013-10-24
if it would work on a rasberrry too that would be awesome

---

### Post by mikewhatever on 2013-10-25
> **omniaparatus said:**
> hey guys im looking for a simple secure os that will let me surf most websites,  watch youtube videos and possibly online banking and do it securely using a vpn or whatever.

Sounds like you look for a dream OS that may or may not exist for you. Why? Because dreams are subjective. Many OSs can do all the above, Ubuntu and Windows included, prvided the user is not the weakest link. 
VPN is not about security, but rather about privacy. The two concepts are often confused.

> 
i bought the newest ubuntu but i couldnt get it to install in my system.
i tried dozens of times but it wouldnt take.

Really? Where did you buy it? How much did you pay?
Perhaps we can help you with the installation. What are the system specs? What was the problem exactly. I'd recommend starting a new thread, and explaining everything properly, if you choose to go that route.

> 
so is open bsd or trusted bsd a better choice?
i want to install it on a newer laptop  and high powered desktop
I am sure BSD is a greate choice, especially if it works for you, but this is an Ubuntu (not BSD) forum.
Give it a try to find out.

---

### Post by unixpcguy on 2013-10-25
Maybe you're installing it the wrong way. I would recommend a dual partition. Do not install side by side in the same OS. For example within Windows. If you did it correctly it would boot with a dual-boot menu loader. Ubuntu can surf any website on the web. It is a secure operating system. It's just a matter of preference. There's Kubuntu, Xubuntu, and all those. Research before you install.

---

### Post by ian-weisser on 2013-10-25
> **omniaparatus said:**
> i bought the newest ubuntu but i couldnt get it to install in my system.

Return it to the place you purchased it from. Perhaps your copy is scratched.
It installs well on a wide variety of systems.

---

### Post by omniaparatus on 2013-10-25
my system is a year old amd quad core with 4 gb ram i believe.
i tried installing it on a totally seperate drive and told it to take over the whole drive.
also tried the dual boot thing too.
i bought 3 disks from the uk for only like 10 or 20 bucks but shipping was almost same price so its not likely the disk is scratched nor is it worthwhile returning.
it just must be buggy with my system specs or settings in the bios or some little mistake in installing

i guess im just as concerned about privacy as im security, i do buy things online all the time with a high limit credit card and do online banking as well

but most of the time, like 99 percent im  just watching youtube or reading website news or watching news videos.
i rarely print anything
nor do any type of documents in open office
rarely edit photos.

ubuntu would suffice but i just cant get it to work

---

### Post by ian-weisser on 2013-10-25
Well, Ubuntu is free online...so don't pay for it again.
We could help you more if you could explain exactly what you see when the install fails.
Exact descriptions and/or error messages would help a lot.

Did the install complete but the system fails to boot at all?
Did the install complete but the system boots into something unexpected?
Did the installer give an error message and abort?
Did the installer give a warning message, but continue the installation?
Is this a dual-boot system, or is Ubuntu the only installed OS? Or some other complicated install?

---

### Post by omniaparatus on 2013-10-25
the reason i paid for it in first place cuz the download iso wasnt installing either, so i thought it was me messing up the iso but it wasnt apparently since i got the same errors.

its been a few months but i think it seemed to install properly, no  warning or issues but then after rebooting, nothing would work without  the install cd in the tray as if it didnt install at all?

---

### Post by ian-weisser on 2013-10-25
> **omniaparatus said:**
> [...]after rebooting, nothing would work without  the install cd in the tray as if it didnt install at all?

Do you mean that your system won't boot without the CD in the tray?
Or you cannot install new software without the CD in the tray?
Please be specific. Each of those is possible, and pretty easy to fix...but the fixes are very different.

---

### Post by aysiu on 2013-10-25
I think you're making this overly complicated. You don't need to buy Ubuntu. You don't need to set up separate partitions or separate disks. You don't need a CD or DVD.

Just use the Ubuntu Windows installer:
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

Sets up Ubuntu as a dual-boot without repartitioning. No muss, no fuss.

P.S. If you can't install Ubuntu, BSD is not going to be any easier.

---

### Post by unixpcguy on 2013-10-25
Sounds like a case of over complicating things. Just follow instructions. If you're a noob, then read more on it.

---

### Post by omniaparatus on 2013-10-25
my windows hdd is only a 60 gig sd drive and mostly full already so im thinking i need to install it on a different hdd, even if its in a dual boot config which i kinda wanted to shy away from since ive had problems with grub bootloaders in the past 

my system wont boot without cd in tray making me think the os didnt install at all or grub boootloader didnt install?

---

### Post by omniaparatus on 2013-10-26
just downloaded and made a new iso and tried installing on my old desktop and still got errors!

this time it failed cuz it said install disk too small but it asked for at least 2.5 gigs and i tried giving it all 15 gigs but i was limited to moving the cursor to a max of 10 gigs out of the 15 but nevertheless it still should have been way more than needed

so why didnt it allow me to choose whole disk by moving slider all the way?
why did it fail saying not enough disk space? ....does it require more than 10 gigs after it downloads all new packages  or what?

then i try install security enhanced openbsd and also get errors.
i didnt know all the internet connections  hosts domains, ipv4 gateway, name server adress etc and wasnt able to complete install maybe cuz of this but maybe something else?

---

### Post by oldfred on 2013-10-26
Moved to Absolute Beginners.

Is ISO valid, you can check with md5sum.
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If booting issues with Live installer on flash drive it may be a video issue.
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Installer has not changed a lot. examples of several versions, but should be almost same for all.

 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by omniaparatus on 2013-10-26
well i checked it twice with md5sum and one version got all 233 files as errors, the zip file only found 1 error.
now what?
redownload iso or re write?[ATTACH=CONFIG]247263[/ATTACH]

---

### Post by oldfred on 2013-10-26
Any error is a problem, you should redownload.
Many suggest using torrent as that also does verify.

I download daily, and then use zsync so it only downloads changes & verifies that download matches. But I do that from Ubuntu, do not think there is anything like that in Windows.

---

### Post by omniaparatus on 2013-10-27
ok i tried the install from store  bought disk , chose to install alongside windows 7 and split my empty  1.5 tb drive in half and installed it there  but still get same problem.

i also tried installing  not alongside windows  and tried installing on the empty 1.5 tb drive but could not figure out how to partition it properly, some error about no root directory specified in partition tables

anyways, it seems to go through all the motions, no errors, completes install but if i reboot with cd in tray it just boots off the live cd and if i boot without it in the tray i get this error;

[initramfs] unable to find medium containing a live file system

do i need to change boot disk order to hdd first?
do i click on esc to get etra boot options at startup?

---

### Post by omniaparatus on 2013-10-27
ok i cant even seem to get into my bios right now, might have to reset cmos.
extr boot options didnt help either.
i dont get why this is so hard?

---

### Post by ian-weisser on 2013-10-27
Perhaps you have a hardware issue.
Ubuntu does not change your system's BIOS.

---

### Post by ikt on 2013-10-27
> **omniaparatus said:**
> i dont get why this is so hard?

You're installing an operating system, something 99.9% of people will never do, you're on the bleeding edge here ;)

> **omniaparatus said:**
> [initramfs] unable to find medium containing a live file system

Does your BIOS have an option in it to select:

boot with others (or multiple) and not just a boot with only windows (> Advanced&#65279; Bios Features > Installer OS Select > Windows / *Other*)

?

---

### Post by omniaparatus on 2013-10-27
not sure about that bios option but this is at least partially solved as i was able to download and install 13.10 and am using it right now on first reboot. hopefully subsequent reboots will also work.
maybe it was a bios option or hardware issue. this install did say 12.04 was there and needed to be upgraded or writtten over. i chose rewrite

now im trying to install the 12.04 on my laptop but had to scrifice windows for a complete install as im still clueless about this root problem when choosing someplace to install.

---

