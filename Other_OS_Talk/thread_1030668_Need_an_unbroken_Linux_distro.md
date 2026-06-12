---
title: "Need an unbroken Linux distro"
date: 2009-01-04
forum: Other OS Talk
---

### Post by tech_wiz03 on 2009-01-04
Hi
   How to word this. Been using Mandrake 9 for many years on an pentium 4 and perhaps was spoiled by all the stable control it had on hardware. Now I have a New Toshiba laptop which won't run older versions primarily due to dual core and archetecture enhancements.

   Tried fedora 10 (won't install), Mandriva 2009 (won't recognize novatel usb modem, no kde, can't get new packages without using repositories [no individual package installs]), Ubuntu 8.04 & 8.10 (same results as for mandriva) and now kubuntu 8.04 which is trying to work but seems to have alziemers!!

   At every second or third boot kubuntu forgets the configuration of the drives (windows ones) that have been set to auto mount under
/media as /media/win_c & /media/win_d. I have to fight hours each time to convince the system these drives are to be assigned to me and root always and mounted at boot. The problem seems to be that mtabs and fstab are being restored to the original setup every third reboot!

   Kubuntu does give me the kde so i can work but unfortunately it keeps hanging because it can't access my USB flash drive or
windows drives. When I insert a flash drive the system shows it
but won;t grant users read or write access even where root says it's ok.

   I'm used to seeing my drives as icons on my desktop but after a reboot the icons point to nothing.

   My Novatel wireless USB stick keeps getting recognized as a USB flash drive so getting it to work as a modem works only once every 1000 tries or so.

   I need this distro to quit changing my settings or i'll have to scrap Linux as being a poor winblows simply because I can't connect to repositories to get very necessary config tools. I'm presuming they haven't eliminated them too.

   In short HELP! it will be appreciated.

---

### Post by kansasnoob on 2009-01-04
I know I'll be called a traitor, but for those who love the KDE desktop (I'm a Gnome guy and IMHO opinion no one does it better than Ubuntu) I recommend Simply Mepis:

[http://www.mepis.org/](http://www.mepis.org/)

Read the installation notes though! It's not vastly different but there are a few differences!

I install so much I can't remember for sure but I think Mepis requires you to enter passwords like "demo" and "root" to do certain things from the Live CD.

Or maybe consider a Gnome alternative like Linux Mint:

[http://linuxmint.com/](http://linuxmint.com/)

Mint is based on Ubuntu, and it's my second favorite distro!

---

### Post by Twitch6000 on 2009-01-04
Try Open Suse or Linux Mint KDE edition they both have great hardware support and are easy to use.

I would say use Open Suse 11 first though as you are use to using .rpm's

---

### Post by tomtom1982 on 2009-01-04
Well, give debian lenny a try.

[http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-kde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-kde-CD-1.iso)

---

### Post by mdsmedia on 2009-01-04
> **kansasnoob said:**
> I know I'll be called a traitor, but for those who love the KDE desktop (I'm a Gnome guy and IMHO opinion no one does it better than Ubuntu) I recommend Simply Mepis:

[http://www.mepis.org/](http://www.mepis.org/)

Read the installation notes though! It's not vastly different but there are a few differences!

I install so much I can't remember for sure but I think Mepis requires you to enter passwords like "demo" and "root" to do certain things from the Live CD.

Or maybe consider a Gnome alternative like Linux Mint:

[http://linuxmint.com/](http://linuxmint.com/)

Mint is based on Ubuntu, and it's my second favorite distro!

I Don't think you're a traitor. I didn't like Kubuntu and most KDE users (I think) will tell you that Kubuntu isn't the greatest KDE distro.

I've got Ubuntu on my laptop, since 5.04, and haven't found anything I like better in Gnome. On my desktop I've now got Mandriva One 2009 (KDE). Since my laptop is my main work machine and my desktop is for play I haven't spent much time with Mandriva, but it seems very nice. Being an RPM distro and KDE it'll take some getting used to, but that's why it's there.

I haven't tried Mepis yet, but then I tend to try what comes on my magazine cover DVD.

---

### Post by HavocXphere on 2009-01-04
USB modems are going to be tricky under any *nix atm...I know of ppl getting them to work in <10s with Kubuntu8.10 and others who struggled for hours.

Try Opensuse as suggest...I'm told their kde implementation is good.

As for the alzheimer/lost settings, I noticed that too at the beginning with KDE 4.1 but it seemed to have sorted itself out now...not sure what changed. Seems to be connected to crashes somehow...as if its resetting setting if something goes pear-shaped.

As for the drive mount, the latest kubuntu auto-mounts everything (NTFS w/ write, USB HDD, flash) if fstab doesn't include any info. To access it one needs to complete the kdesudo prompt in dolphin on first use....haven't figured out how to fix that. As soon as I edit the fstab then the specific drive doesn't mount anymore.

Hope you get it sorted out.:KS

---

### Post by tech_wiz03 on 2009-01-04
I appreciate the comments about distro's and spent a few minutes checking out mepis and linuxmint reference articles. From what I saw they wouldn't be any better at addressing the issue of giving me control over my op system. 
    Ideally, I need Kubuntu using a root terminal rather than a regular terminal. to use su command fix things rather than sudo command at each step. In essence, the mount issue in fstab needs to be locked so no system change can remove what I set. Reviewing logs which because I can't copy contents to my windows drive so I can report them thru my windows based internet connect, indicate HAL (Hardware Abstraction Layer) is not loading all the time or in a consistant manor.

---

### Post by kansasnoob on 2009-01-04
> **tech_wiz03 said:**
> I appreciate the comments about distro's and spent a few minutes checking out mepis and linuxmint reference articles. From what I saw they wouldn't be any better at addressing the issue of giving me control over my op system. 
    Ideally, I need Kubuntu using a root terminal rather than a regular terminal. to use su command fix things rather than sudo command at each step. In essence, the mount issue in fstab needs to be locked so no system change can remove what I set. Reviewing logs which because I can't copy contents to my windows drive so I can report them thru my windows based internet connect, indicate HAL (Hardware Abstraction Layer) is not loading all the time or in a consistant manor.

Seriously! I'm way too much of a noob to understand that!

It's simply over my head ................. or I'm not understanding:confused:

---

### Post by tech_wiz03 on 2009-01-04
Ok trying bitorrent download of opensuse vers 11 but man will this be slow only 2.4kb/s and it's eta is 40 wks for install dvd. hope connection speed improves to my normal of 850kb/s.

will check back here for any new suggestions.

---

### Post by tech_wiz03 on 2009-01-04
> **kansasnoob said:**
> Seriously! I'm way too much of a noob to understand that!

It's simply over my head ................. or I'm not understanding:confused:

Sorry, been dealing with computers since 1975, and sometimes forget others may not have. Basically, we all get use to using certain programs to do things, over enough time we forget other programs or ways to do same things. 

when we choose to use a different operating system we try to do things the same way we used to use. The new system may not have the abilities or may require doing things differently.

Thusly a learning curve is involved.

---

### Post by MisfitI38 on 2009-01-04
Try [Arch.]("http://archlinux.org/")

---

### Post by wolfen69 on 2009-01-04
i would go with debian lenny. rock solid stable.

---

### Post by fistfullofroses on 2009-01-04
No GNU/Linux distro is really "broken" by default... however, I would recommend Slackware and/or Arch if you are looking for system control with good hardware support.

---

### Post by txcrackers on 2009-01-05
FYI, if you want to go the "su" route, there's nothing preventing you from assigning a password to the root user.

---

### Post by tech_wiz03 on 2009-01-08
> **Twitch6000 said:**
> Try Open Suse or Linux Mint KDE edition they both have great hardware support and are easy to use.

I would say use Open Suse 11 first though as you are use to using .rpm's

    Ok finally back online :( . Opensuse wiped my windows partition and only installed a partial system. Thank god for separate data partitions. Now I got opensuse 11 & windows vista co-existing. Drives and settings good, kde apps ok. 

   Issuing a worded thanks to you and all who tried to help since I couldn't get the thankyou icon to work.

   Question to you ... package seams to be missing su, usbview, lpusb, modprobe, usbserial so configure of novatel mc950d can't be done according to novatel instructs. Any idea's??

---

### Post by chachawpi on 2009-01-08
Are you sure they just aren't in /sbin/ and /sbin/ isn't in your path?

---

### Post by disturbed1 on 2009-01-08
..

---

### Post by namegame on 2009-01-08
> **txcrackers said:**
> FYI, if you want to go the "su" route, there's nothing preventing you from assigning a password to the root user.

A bash alias could also be defined for "su." Granted, it's not truly su, but it will "look" like it.

---

### Post by Hallvor on 2009-01-08
> **tech_wiz03 said:**
> 
Question to you ... package seams to be missing su, usbview, lpusb, modprobe, usbserial so configure of novatel mc950d can't be done according to novatel instructs. Any idea's??

To find e.g. modprobe type ```
locate modprobe
```. Here it is located in /etc/modprobe. Instead of just typing modprobe, I type etc/modprobe to make it work.

---

### Post by oswaldkelso on 2009-01-08
I tried a Novatel mc930d usb 3g modem on Debian Lenny using the vodafone gpl'd driver in a phone store just to see if it was recongnised. It was but I did'nt have permission to activate to card :) [https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/)

---

### Post by tech_wiz03 on 2009-01-20
> **oswaldkelso said:**
> I tried a Novatel mc930d usb 3g modem on Debian Lenny using the vodafone gpl'd driver in a phone store just to see if it was recongnised. It was but I did'nt have permission to activate to card :) [https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/)

Thanks, here's what I have found out. the Novatel mc930d modem must be first activated under windows (tm). After activation it may be configured under mac os or linux. The modem is recognized under debian, ubuntu, opensuse etc. with or without the vodafone driver but until you defeat it's primary usb_storage mode the system will see it but can't access it's modem subsystem. So your attempt at the phone store was not giving full disclosure. 
      steps ... 1 Activation modem using MS Windows XP or later.
                2 Install vodafone driver or implement wvdial, or
                  kppp dialer access information.
                3 defeat usb_storage which requires root write
                  access and modifications to system files
                4 create usb_modem mods to system files
                5 restart linux
                6 plug in usb modem and revisit step 2 to finalize settings. Then it should work every time the modem is
plugged in.
      Where I have had trouble is with step 3 on 8 different distro's as settings keep returning to usb_storage every 3rd reboot.

---

### Post by tech_wiz03 on 2009-01-20
> **chachawpi said:**
> Are you sure they just aren't in /sbin/ and /sbin/ isn't in your path?

/sbin/ is in my path, sudo is present but su is not. This is true in kubuntu, ubuntu, mandriva2009, and opensuse 11.1. Other key items needed for configuration are also missing like lsusb usbserial etc. I did find docs stating they are not installed by default due to security risks but can be obtained from repositories if you need them. Great:( download from internet repository the features you need to gain internet access.

---

### Post by tech_wiz03 on 2009-01-20
> **Hallvor said:**
> To find e.g. modprobe type ```
locate modprobe
```. Here it is located in /etc/modprobe. Instead of just typing modprobe, I type etc/modprobe to make it work.

modprobe found in /etc/ problem turned out to be the named device usbserial.
    Issued : modprobe -r usbserial
    reply  : no such file or device
    Issued : modprobe usbserial vendor=4400 product=1410
    reply  : no such file or device
  ** thus it's usbserial device not modprobe that's missing.

---

