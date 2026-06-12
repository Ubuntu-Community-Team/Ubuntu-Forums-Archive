---
title: "new to ubuntu14.04... errors in browser(s)"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by houseofyeti on 2014-05-26
browser (firefox and chromium) keeps saying "please update internet explorer"  or "firefox is out of date. please update" and trying to run a file called "update.exe"  
I cant get to yahoo or youtube and frequently while browsing it just takes over the browser. can't close the pop up  as any click on the pop up downloads the file. :confused:

---

### Post by oldfred on 2014-05-26
Ubuntu does not use .exe files, and only a few applications directly update from the application. You normally update from the repository.
You may have an .exe in .wine, but many things do not work well from wine. Only wine has Internet  Explorer.

Post this from terminal in Ubuntu:
sudo parted -l
       cat /etc/*release

 echo $DESKTOP_SESSION

---

### Post by houseofyeti on 2014-05-28
ok..  here is what shows in terminal for those 3 

tim@tim-ThinkCentre-M82:~$ sudo parted -l
[sudo] password for tim: 
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical


Model: ATA WDC WD3200AAKS-0 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  320GB  320GB  primary  ntfs         boot


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4089MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4089MB  4089MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 496GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  496GB  496GB  ext4


Error: /dev/mapper/sda5_crypt: unrecognised disk label                    

tim@tim-ThinkCentre-M82:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"
NAME="Ubuntu"
VERSION="14.04, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
tim@tim-ThinkCentre-M82:~$ echo $DESKTOP_SESSION 
ubuntu
tim@tim-ThinkCentre-M82:~$

---

### Post by oldfred on 2014-05-28
It looks like you have Ubuntu in a full drive LVM with encryption on your 500GB drive and one NTFS partition on your 320GB drive.

But neither Firefox nor Chromium should have anything to do with Internet explorer. 

Are you at some proprietary site that only works with IE and is trying to download IE, or some site trying to download a virus.

---

### Post by jakke1975 on 2014-05-29
You want to update your browsers to use flash... well, there's something annoying about Linux - I truly agree!
Either install Google Chrome (instead of the open-source chromium), which installs flash automatically BUT, is closed-source!
OR
You can use the pepperflash plugin following this article:
[http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html](http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html)
This works for both Chromium and Firefox.

---

### Post by houseofyeti on 2014-05-29
Well...  I can't get to youtube at all or to yahoo home page. I loaded the flash player and can watch on other sites. No sites visited that require explorer that I am aware of as used to run Firefox  and never had a problem when on windows 7 pro.

 Virus? Perhaps.  Don't know. Always had anti virus running but that is no guarantee.

---

### Post by Impavidus on 2014-05-29
A message saying "please update internet explorer" when you're not running internet explorer, an update.exe that won't work on Linux to update firefox where every sensible human would direct you to the mozilla website to download the latest firefox, popup windows that don't have a close button but only act as a download link... I think somebody tries to trick you into downloading and running some malware. Don't do it.

Things to try: use a fresh firefox profile, disable plugins. Some people report a better experience with plugins to block ads. I don't have any plugins, except for flash, which I keep deactivated most of the time, and it gives me a good experience.

I don't think you already have a virus or worm. Why? First, any hacker would try to conceal his presence, not bombard you with tricks to let you install more malware. Second, because it takes more to break into a Linux system. These tricks are targeted against a Windows system. Had you run Windows, that update.exe could have done lots of nasty stuff.

Don't listen to popups telling you to update firefox. The ubuntu package manager takes care of it. Just install all updates it proposes.

---

### Post by houseofyeti on 2014-05-29
I have reset firefox have only one plugin and that is the flash player from adobe. I intentionally did not load a bunch of plugins til I get used to ubuntu.

---

### Post by houseofyeti on 2014-05-29
ok.. here is a snapshot of a frame that showed up in place of an embeded youtube video on a  vBulletin® Version 3.8.5 page.[ATTACH=CONFIG]253589[/ATTACH]

as you can see the update now and the remind ne later both point to setup.exe 
None of the other buttons go anywhere valid.

---

### Post by user_of_gnomes on 2014-05-30
```

```Could you post the content of about:plugins from Firefox?

---

### Post by houseofyeti on 2014-05-30
[ATTACH=CONFIG]253598[/ATTACH]

ok.  more plugins than i thought.... must have loaded with ubuntu when it intalled as I didnt add them.  ;)

---

### Post by houseofyeti on 2014-05-30
So according to my server I have a Adobe flash virus... its slowing my internet access and redirecting the isp.

Gah! 

now what?

---

### Post by houseofyeti on 2014-06-05
nothing? 

damn. was hoping for a way to remove it.  Perhaps getting rid of flash player entirely.  I dont know how to go about any of that in ubuntu.

---

### Post by Rob Sayer on 2014-06-05
> **houseofyeti said:**
> [ATTACH=CONFIG]253598[/ATTACH]

ok.  more plugins than i thought.... must have loaded with ubuntu when it intalled as I didnt add them.  ;)

I've installed a number of ubuntu versions/DEs on a few machines.  I can CATEGORICALLY say they were not installed by ubuntu.  Never seen or heard of any of them before.

At this point I'm starting to wonder where you got your live CD iso.

---

### Post by jdeca57 on 2014-06-05
It's not so difficult to disable a plugin but on the screenshot you added it seems that the flash plugin is already disabled. You can troubleshoot flash:
[https://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems](https://support.mozilla.org/en-US/kb/keep-flash-up-to-date-and-troubleshoot-problems)
But many people probably wonder how you managed to insert a virus. If it's local I'd also consider deleting ~/.mozilla/firefox (or simply rename it)

---

