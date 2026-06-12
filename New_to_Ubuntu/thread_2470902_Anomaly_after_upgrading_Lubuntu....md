---
title: "Anomaly after upgrading Lubuntu..."
date: 2022-01-15
forum: New to Ubuntu
---

### Post by Innernet on 2022-01-15
Hi.  
Been running Lubuntu 20.04 for over a year;  today decided to see if there was a never version and yes, upgraded to 21.04
The desktop screen still shows 20.04 in light blue large image at bottom right.  Did it fail to upgrade?

---

### Post by GhX6GZMB on 2022-01-15
Running Lubuntu 20.04 myself.
Which large blue image bottom right?

---

### Post by Holger_Gehrke on 2022-01-15
You can upgrade from one release to the next or from one LTS release to the next. Releases happen two times each year in April and October (usually towards the end of those months). The releases in April of even numbered years are Long Term Support releases (5 support for Ubuntu, 3 years for most of the other flavours). So it really should not be possible to update from 20.04 - which is an LTS release - to 21.04 - which isn't - without first updating to 20.10 and 20.10 was a non-LTS release so it's out of support (9 month support for non-LTS) and shouldn't be available anymore. Actually, 21.04 is going to drop out of support soon. You should wait until the next LTS (22.04) if you missed the window to get on the short term release trail.

Holger

---

### Post by Bashing-om on 2022-01-15
Innernet; Hummm ...

> 
The desktop screen still shows 20.04 in light blue large image at bottom right. Did it fail to upgrade?


As I do not run Lubuntu I can not relate to what is seen on that desk top. However, we can check from terminal what release is installed:
```

cat /etc/issue
lsb_release -a
uname -a

```

[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by Innernet on 2022-01-15
Thank you.   Attaching a screenshot.  (I have also Ubuntu 20.04 besides Lubuntu and choice to boot at startup in this laptop)  

[ATTACH=CONFIG]289806[/ATTACH]

---

### Post by Bashing-om on 2022-01-15
Innernet; Hey hey -

Your last confirms that you remain on the 20.04 release. However, you are behind on updates.
```

 sysop@2004x-c:~$ cat /etc/issue
Ubuntu 20.04.[color=green]3[/color] LTS \n \l

```

In respect to the other posters' advise you are also advised to update the current install prior to anything else that you decide to do for an in-place release upgrade.

[INDENT]what do do ?
[INDENT][INDENT]there are options 
[/INDENT][/INDENT][/INDENT]

---

### Post by guiverc on 2022-01-15
Firstly I'd definitely **NOT **upgrade to 21.04 - its in its [last ~hours of supported life]("https://lists.ubuntu.com/archives/ubuntu-announce/2021-December/000275.html"); also refer [https://discourse.lubuntu.me/t/lubuntu-21-04-is-nearing-its-end-of-life/3008](https://discourse.lubuntu.me/t/lubuntu-21-04-is-nearing-its-end-of-life/3008).

I'd also agree with ^ Bashing-om; as an updated 20.04 system will currently report as 20.04.3 (but will switch to 20.04.4 very soon).  [This will show the ISO release date as August 2021]("https://fridge.ubuntu.com/2021/08/27/ubuntu-20-04-3-lts-released/") but that date represents the release of the ISO, as installed systems upgraded week(s) before to 20.04.3

Sorry I don't understand what the real issue is though so can't given anything helpful sorry.

Additional [Lubuntu 20.04.3 release link if wanted here]("https://lubuntu.me/focal-3-released/"); *I'm a Lubuntu team member, but I do see Lubuntu really as just Ubuntu*.

---

### Post by guiverc on 2022-01-15
> **Holger_Gehrke said:**
> So it really should not be possible to update from 20.04 - which is an LTS release - to 21.04 - which isn't - without first updating to 20.10 and 20.10 was a non-LTS release so it's out of support (9 month support for non-LTS) and shouldn't be available anymore. Actually, 21.04 is going to drop out of support soon. 

Long ago non-LTS releases had 15 months supported lives; but when the 15 was reduced to 9 months some issues were *complicated* with the *release-upgrade* process, and this was *resolved* by allowing the *do-release-upgrade* tool to upgrade to the next supported release instead.

So once 20.10 reached EOL ("*Supported: 0*" on [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) which the *release-upgrade *tools look at) the `do-release-upgrade` tool will upgrade from 20.04 to 21.04... In a few days *hirsute* will be "*Supported: 0*" too and it'll allow upgrade to 21.10.

A few QA-tests were added/changed for this on iso.qa.ubuntu.com (eg. [http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/242806/testcases/1310/results;](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/242806/testcases/1310/results;) *there's a clearer example than this sorry, but it only shows late in cycle if I remember correctly*) but it's largely CI testing.  It's not an encouraged path; but technically it is a supported one  (*it didn't used to be!*).

---

### Post by Innernet on 2022-01-15
Thanks, gentlemen.  Will attempt to do updates step by step instead of jumping to something just by smell.

Seems also I have no clear concept of what is unsupported; 
-  If that means the forums do not assist in solving problems to that version any more,  
- or the version stops working at such end-of-support moment;  
- or the version is not obtainable/downloadable/installable/useable any more, 
- or applications for it become then non-operational, 
- or other...   
Can anyone clarify to get that doubt out of the way ?   Correct, am a not that bright old fart but running Ubuntu since 5.10 I want no other OS...
But would be nice some message/warning that upgrading from such-to-such is not recommended when attempting to do so because this and that and the other...:(

---

### Post by Bashing-om on 2022-01-15
Innernet; :D

1) The Forum is always here to help - you are expected to think and learn from the experience
2) Nope - will continue to work - Just at End_Of_Life there are no further updates
3) Old releases that are no longer supported, the software repository is (re)moved
4) Nope - applications will continue to work - just be a aware of all the bad guys out there and there are NO security fixes available
5) for other See [https://help.ubuntu.com/community/EOL](https://help.ubuntu.com/community/EOL) and [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) for more info. Looking to upgrade from an EOL release? See [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
//
You have a Long Term Support release installed that has 3 years support on the desk top and 5 years support for kernel space( 20.04 == April of 2020). Is there a reason you desire to migrate off the current stable release ?

To get your current install up-2-date run terminal commands:
```

sudo apt update
sudo apt upgrade

```

[INDENT]there is method
[INDENT][INDENT]to Canonical's madness :D[/INDENT][/INDENT][/INDENT]

---

### Post by guiverc on 2022-01-15
**Support**.

Before I upgrade, I'd always recommend reading (*or at least skimming*) the release notes. I provided some links in my prior reply in a link I provided ([*warning about 21.04 reaching EOL; thus I provided what I'd read for the jump to 21.10*]("https://discourse.lubuntu.me/t/lubuntu-21-04-is-nearing-its-end-of-life/3008")), ie. since it's a Lubuntu install I'd recommend what Lubuntu suggested (*what we/the Lubuntu Team discover in QA/Quality Assurance will be noted there*) plus Ubuntu's notes *(the upgrade is not done by Lubuntu tools, but performed by the Ubuntu base all flavors use - thus those notes apply!*  *Hey I even said I consider Lubuntu as a Ubuntu* system)

The [Lubuntu downloads link]("https://lubuntu.me/downloads/") provides a chart on support, which for 20.04 (*2020-April release*) shows 3 years of dark blue where all sites will support you, including the Lubuntu team. A further 2 years of light-blue brings it to 5 years, where Lubuntu no longer provide support, but you can ask questions still on sites such as this, askubuntu.com etc.  During those two years you may get reminders that parts of your system is *unsupported* (*security fixes have ceased & you may be vulnerable to some attacks*) which are intended to encourage you to upgrade, but it's your choice. Some members won't provide support after *official* EOL (*so your support base is likely smaller*) but you won't be off-topic on sites so can still seek support.

Software keeps working when support ends; you're just *more *at risk of security attacks.  eg. I still use 32-bit laptops & have Lubuntu installed on at least one; are the last release for *i386* or 32-bit was 18.04 LTS  (*yes 18.10 & 19.04 were later; but not being LTS they reached EOL sooner*) so mine still runs Lubuntu 18.04.  That's a release that is EOL; ie. [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/) & I've blogged about quite a bit on [Lubuntu's discourse]("https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466").  How I use that machine now differs, in that it's mostly used off-line...  If the EOL status did worry me; I'd re-install a Debian system onto it (*it runs, as I QA-test Debian as well as Ubuntu having used that box for Debian testing too*), but with my own usage, I don't see it as worth the effort (*yet anyway*).

Security/Privacy are the major concerns for me with EOL software, not just for yourself, but using an EOL device also puts those on the same network at more risk...

With Ubuntu releases, I'll provide the following ....

- Format of releases is *year.month*. so 20.04 tells you it's the 2020-April release.
- No release occurred before 2004; so you just add 2000 to the year; how 20 becomes 2020.
- non-LTS releases have 9 months of supported life (*that has changed over the decades*) so 21.04 was the 2021-April release + 9 months & you can work out month... Should you want a day of the month as well; grab a calendar & it'll usually  be the 3rd or 4th Thursday (*releases are always a Thursday with Ubuntu*).
- The first release on an *even* year is a LTS; ie. that's been 6.06, 8.04, 10.04, 12.04, 14.04, 16.04, 18.04, 20.04, and will be 22.04 next... The reason I said first release (and not April) is that in 2006 it was late & didn't come out till June; thus 6.06 LTS...   Ubuntu has always kept to April since then though and I'd expect that to continue.
- releases are scheduled for April & October; thus the common .04 & .10; only exception being the aforementioned 6.06 which was late & occurred in 2006-June.

One advantage of SNAP packages is they are the same for all releases; so if you're using Lubuntu 20.04, or Lubuntu 21.10, Snap packages would be identical for both systems.  Contrast that with Lubuntu's text editor `featherpad`

```
 featherpad | 0.12.1-1build1 | focal/universe   | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 featherpad | 0.17.1-1       | hirsute/universe | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
 featherpad | 0.17.1-1       | impish/universe  | source, amd64, arm64, armhf, ppc64el, riscv64, s390x
```

where you'll see a much older version in focal (20.04) when contrasted with 21.10  (I've copy/pasted from a terminal query using `rmadison` but you can also look online via [https://packages.ubuntu.com/search?keywords=featherpad&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=featherpad&searchon=names&suite=all&section=all))

Ubuntu 16.04 LTS has now completed it's *standard support* and now is only supported via ESM.. For some packages that were supported as *deb* packages during the *standard* support cycle; they're [now only supported via *snap* packages]("https://wiki.ubuntu.com/SecurityTeam/ESM/16.04"); as that allows 16.04 to run same software as later releases.

Sorry this is long; but hopefully something is useful.

---

### Post by Innernet on 2022-01-15
Thank you for your detailed patience.

Bashing-om: ----> Is there a reason you desire to migrate off the current stable release ? <----

Yes, there is a daily freezing with Ubuntu and that made me try Lubuntu which behaves better but not as well as the unforgettable perfection 8.04 had.:p  And in previous consultations to the forum, am unable to understand the explanations or there is no explanation for the behavior.  With little knowledge and skills to diagnose, I sporadically try something else to see if it behaves better. And has partially worked.

----> 3) Old releases that are no longer supported, the software repository is (re)moved <---

The installation CDs I keep since 1995 versions can be installed, good thing !   done it, and have served me well a few times :P  

It would be too much of a dream for an Ubuntu expert on the forum to do a remote handling/inspection/diagnosing of my compfuser.  But dreaming is free. :redface:

---

### Post by guiverc on 2022-01-15
Do ensure you have *swap* enabled if you're encountering *freezing*. 

See

- [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)
- [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)

Swap has returned to being a default from 21.04/*hirsute* and up; but it was manual (*in setup*) for prior LXQt releases of Lubuntu (unless a swap partition or *swapfile* already existed).

Re: old-releases.. on EOL they repositories are moved rather than dropped (*mirrors are free to drop them if they wish*) to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)  to use it is a manual step as no automatic tool does it (they *release-upgrade* you to a *supported *release which is the preferred option).  See [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) for full details.

---

### Post by Innernet on 2022-01-15
> **Bashing-om said:**
> 
To get your current install up-2-date run terminal commands:
```

sudo apt update
sudo apt upgrade

``` [/INDENT][/INDENT][/INDENT]

As instructed above; the compfuser downloaded/installed something and the terminal later asked if I wanted to remove like 3,000 files?  or Mbytes?  that were not necessary anymore.  
I responded yes and were deleted.  Restarted power, and the lower right corner still shows 20.04 as in the screenshot posted before.

Suggestion: do not get old, it is the shits.  Bad memory and clumsiness are more frustrating than a midget with a yo-yo :D

---

### Post by Bashing-om on 2022-01-15
Innernet Well - well ----

unforgettable perfection 8.04 had >> Oh Noes; that was 10.04 :P

If you are seeking reliability on OLD hardware - I can hardily recommend you try 20.04 (X)ubuntu.
I too run on old old hardware and I find that xubuntu runs well. However, I do build up from a minimal install such that all I have installed is only what I particularly desire to have and use. Reduces the overhead and headache muchly.
 [https://unit193.net/xubuntu/](https://unit193.net/xubuntu/)
If you are handy with the terminal and have some familiarity with the software repository.

> 
Yes, there is a daily freezing with Ubuntu and that made me try Lubuntu


wont take much at all to burn a DVD (21.10) and run it in "try ubuntu" mode; see here if the system still freezes:
[https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

Dealing with system freezes is a thing of patience and can take a loooong time. Lots of logs to read and understand  and tools to employ to try and isolate. 

[INDENT]been there done that
[INDENT]it ain't no fun
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2022-01-15
Innernet; Update :)

Bet now if ya look:
```

lsb_release -a

```
ya see now "Description:	Ubuntu 20.04.3 LTS rather than the .2 indication.

all we did here was update the current install - is a different set of commands ( and some tweak of system files) to release-upgrade to 21.10 - such can be a hazard to ones well being :)

Now as to age - you may be surprised that you have nothing on me - I am 72 and though not as good as I once was - I am as good once as I ever was - just COPD and can not hold out long  - thus I spend a lot of time on this terminal :P


Oh Gosh
[INDENT]where did all the time go ?
[/INDENT]

---

### Post by guiverc on 2022-01-15
This box of mine is a 2009 dell.  If I were to use it in QA-testing I'd list its specs as

```
dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)
```

My system (Lubuntu *jammy*) is **not**lean like Bashing-om's, having multiple desktops installed on it. My disk is **bloated**with software, but it's what co-exist in RAM that I concern myself with (*unless I have disk space issues*), but that's generic computer knowledge.

The biggest issue I've had recently (*last couple of years*) is my browser pausing... (*impacted both firefox & chromium*) and it turned out being extensions. If I removed all extensions the issue was gone, but I preferred using some extensions so I live with them installed.  

In my case; I keep a terminal tab open showing `htop` running, and when it feels *slow* I switch to `htop` & look for *memory leak* growing to an *unreasonable* size, I just close the browser, wait a bit (the linux kernel will clean up the RAM), then re-open the impacted browser...  My *freezing* thus *averted*.. and I got to keep my *leaky* browser extensions.. 

I only reboot my box about once a fortnight, but find I have to close, wait & restart the browser every *day or two* to keep performance good. 

The same occurs if using LXQt/Lubuntu, XFCE/Xubuntu, GNOME/Ubuntu ...on this box; and part of it maybe my old CPU that doesn't handle some of the Spectre etc fixes that well (*Intel reported that as part of reason for dropping support for older CPUs*), but I can't do much about that...

---

### Post by Innernet on 2022-01-16
Thank again for your assistance, gentlemen.
Same mileage here but feels like 92 and is not temperature :frown:

Did the last, here is a screenshot image.  Am sorry I never remember how to do it properly as code?

[ATTACH=CONFIG]289810[/ATTACH]

I run the leanest possible machine in such way that I would not know how to make it leaner.  And would need a brain to do so.
The 'freezes' actually occur when browsing the net; and from previous expert suggestions there is no log to review as the compfuser stops logging in that 'freeze' state where the hard drive light stays on and nothing happens: no mouse, no keyboard response.  The power switch-off does work.

---

### Post by Bashing-om on 2022-01-16
Innernet; Humm 

Real odd that you are still on the .2 release.

Show now - between code tags on this post - the results of terminal commands:
```

sudo apt update
sudo apt full-upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Where again all we are attempting to do is get the system updated to the .3 release of 20.04.

As to discovering why the system freezes with Firefox. May I suggest that you open 2 additional TTYs and
in the first run ' top' and keep an eye on the memory usage
in the second run ' journalctl -f ' to have a running commentary of what the kernel is doing and if the kernel screams and hollers.

[INDENT]Gots to be a reason
[/INDENT]

---

### Post by Innernet on 2022-01-16
Screen images for the above :

[ATTACH=CONFIG]289816[/ATTACH]

[ATTACH=CONFIG]289817[/ATTACH]

---

### Post by Bashing-om on 2022-01-16
Innernet; Huh !

Does not compute -

What shows 
```

dpkg -l | grep linux-
uname -r

```

we got some strange kernel thing going on here ?

[INDENT]could be yes
might be not so yes
[/INDENT]

---

### Post by Impavidus on 2022-01-17
May I pop in as well?

It may be good to see your software sources. That is, the contents of your file /etc/apt/sources.list and of the directory /etc/apt/sources.list.d. If there are any files in the latter, the contents of those files may be relevant, but I only expect a google repository there for chrome. To do this in terminal:```
cat -n /etc/apt/sources.list
ls /etc/apt/sources.list.d
```
That will show the sources.list file with line numbers. It tells where your computer fetches the updates from. If something's wrong there, you won't get the updates you expect.

Bashing-om showed how to use code tags.

---

### Post by Innernet on 2022-01-17
Here we go, if I paste it right ...

> externet@externet-presariocq57notebookpc:~$ dpkg -l | grep linux-
ii  linux-base                                    4.5ubuntu3.1                        all          Linux image base package
ii  linux-firmware                                1.187.9                             all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-20.04                       5.11.0.46.51~20.04.23               amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.11.0-43-generic               5.11.0-43.47~20.04.2                amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP                           
ii  linux-headers-5.11.0-46-generic               5.11.0-46.51~20.04.1                amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP                           
ii  linux-headers-generic-hwe-20.04               5.11.0.46.51~20.04.23               amd64        Generic Linux kernel headers                                                        
ii  linux-hwe-5.11-headers-5.11.0-43              5.11.0-43.47~20.04.2                all          Header files related to Linux kernel version 5.11.0                                 
ii  linux-hwe-5.11-headers-5.11.0-46              5.11.0-46.51~20.04.1                all          Header files related to Linux kernel version 5.11.0                                 
rc  linux-image-5.11.0-34-generic                 5.11.0-34.36~20.04.1                amd64        Signed kernel image generic                                                         
rc  linux-image-5.11.0-36-generic                 5.11.0-36.40~20.04.1                amd64        Signed kernel image generic
rc  linux-image-5.11.0-38-generic                 5.11.0-38.42~20.04.1                amd64        Signed kernel image generic
rc  linux-image-5.11.0-40-generic                 5.11.0-40.44~20.04.2                amd64        Signed kernel image generic
rc  linux-image-5.11.0-41-generic                 5.11.0-41.45~20.04.1                amd64        Signed kernel image generic
ii  linux-image-5.11.0-43-generic                 5.11.0-43.47~20.04.2                amd64        Signed kernel image generic
ii  linux-image-5.11.0-46-generic                 5.11.0-46.51~20.04.1                amd64        Signed kernel image generic
rc  linux-image-5.8.0-41-generic                  5.8.0-41.46~20.04.1                 amd64        Signed kernel image generic
rc  linux-image-5.8.0-43-generic                  5.8.0-43.49~20.04.1                 amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04                 5.11.0.46.51~20.04.23               amd64        Generic Linux kernel image
rc  linux-modules-5.11.0-34-generic               5.11.0-34.36~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-36-generic               5.11.0-36.40~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-38-generic               5.11.0-38.42~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-40-generic               5.11.0-40.44~20.04.2                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.11.0-41-generic               5.11.0-41.45~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.11.0-43-generic               5.11.0-43.47~20.04.2                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.11.0-46-generic               5.11.0-46.51~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-41-generic                5.8.0-41.46~20.04.1                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-5.8.0-43-generic                5.8.0-43.49~20.04.1                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-34-generic         5.11.0-34.36~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-36-generic         5.11.0-36.40~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-38-generic         5.11.0-38.42~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-40-generic         5.11.0-40.44~20.04.2                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.11.0-41-generic         5.11.0-41.45~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.11.0-43-generic         5.11.0-43.47~20.04.2                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.11.0-46-generic         5.11.0-46.51~20.04.1                amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-41-generic          5.8.0-41.46~20.04.1                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.8.0-43-generic          5.8.0-43.49~20.04.1                 amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.04~git20190206.bf6db5b4+dfsg1-2 all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu9                amd64        Bootloader for Linux/i386 using MS-DOS floppies
externet@externet-presariocq57notebookpc:~$ 
/[QUOTE]

[QUOTE]externet@externet-presariocq57notebookpc:~$ uname -r
5.11.0-46-generic

and for Impavidus , your headache is back :
> externet@externet-presariocq57notebookpc:~$ cat -n /etc/apt/sources.list
     1  # Automatically generated by Calamares on 2021-02-08.
     2  # Lines starting with "deb" are mandatory, while lines starting with "deb-src"
     3  # are for more detailed package information.
     4
     5  ## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     6  ## newer versions of Lubuntu.
     7  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal main restricted
     8  # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal main restricted
     9
    10  ## Major bug fix updates produced after the final release of Lubuntu.
    11  ## Have you noticed a regression? Please report it!
    12  ## [https://wiki.ubuntu.com/StableReleaseUpdates#Regressions](https://wiki.ubuntu.com/StableReleaseUpdates#Regressions)
    13  # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates main restricted
    14
    15  ## Software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu team.
    16  ## Also, please note that software in Universe WILL NOT receive any review or
    17  ## updates from the Ubuntu security team directly. Updates in this repository
    18  ## are provided by volunteers, but most come from Debian.
    19  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
    20  # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
    21  # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe
    22
    23  ## Software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu team,
    24  ## and may not be under a free licence. Please satisfy yourself as your rights
    25  ## to use the software. Also, please note that software in Multiverse WILL NOT
    26  ## receive any review or updates from the Ubuntu security team directly.
    27  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
    28  # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
    29  # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse
    30
    31  ## Software from this repository contains tested security updates from the
    32  ## Ubuntu security team.
    33  # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
    34  # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
    35  # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
    36
    37  ## Software from this repository may not have been tested as extensively as
    38  ## software contained in the main release, although it includes newer versions
    39  ## of some applications which may provide useful features. Also, please note
    40  ## that software in Backports WILL NOT receive any review or updates from the
    41  ## Ubuntu security team.
    42  # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
    43
    44  ## Uncomment the following two lines to add software from Canonical's
    45  ## "partner" repository.
    46  ## This software is not part of Ubuntu, but is offered by Canonical and the
    47  ## respective vendors as a service to Ubuntu users.
    48  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
    49  # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
    50  deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) focal-security universe restricted multiverse main


> 
externet@externet-presariocq57notebookpc:~$ ls /etc/apt/sources.list.d
google-chrome.list  google-chrome.list.save 


Hope pasted correctly this time instead of screenshot.

---

### Post by Bashing-om on 2022-01-17
Innernet; Welp !

> 
externet@externet-presariocq57notebookpc:~$ uname -r
5.11.0-46-generic


That is the latest and greatest repo kernel for 20.04 - so you must be up on the 20.04.3 release.
You only have 2 kernels fully installed and nothing I note that is a problem.

> 
!info linux-generic-hwe-20.04 focal
18:12 < ubottu> linux-generic-hwe-20.04 (5.11.0.46.51~20.04.23, focal): Complete Generic Linux kernel and headers. In component main, is optional. Built by linux-meta-hwe-5.11. Size 2 kB / 19 kB.


what shows:
```

cat /etc/issue

```

In your dpkg list are a bunch of "rc" ( removed but config files remain) files . You may remove these strays - clean up the clutter and gain just a bit of hard drive space -  with terminal command:
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

[INDENT]what can I say -
[INDENT][INDENT]so far so good
[/INDENT][/INDENT][/INDENT]

---

### Post by Innernet on 2022-01-17
Thanks, boss.
Came back with :

> externet@externet-presariocq57notebookpc:~$ cat /etc/issue
Ubuntu 20.04.2 LTS \n \l


and
Purged a bunch of somethings

Will see how it behaves...  =d>

---

### Post by Bashing-om on 2022-01-17
Innernet; yukkie poo

Too deep for my little mind. Will take one more familiar with the inner workings to know why the system is reporting as .2 release when clearly the .3 kernel is installed and booted from.

I too now be in a learning environment.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT]other times
[INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Impavidus on 2022-01-18
focal-updates is not in the software sources. focal-security is there, so you get the important security updates (including the 5.11 kernel), but not the less important updates. The release number 20.04.3 is packaged in the base-files package, which has been updated through the normal updates, not through the security updates.

Unless you want really rock-solid stability, it's usually best to keep the normal updates enabled. Go to your settings for software sources and make sure that at least all recommended updates are enabled. If you can't find it, we can tell you how to manually modify the sources.list file.

BTW, you used quote tags instead of code tags. Almost there.

---

### Post by Innernet on 2022-01-18
Thank you Impavidus.
Well,  enabled-checked the 'recommended' updates selection that wasn't; after a while an 'upgrade notifier' popped up,   Did it and cycled power when done and prompted to restart.

Desktop still shows Lubuntu 20.04 which is irrelevant if the guts are in order.  Will see how it behaves in the next days.  :P

---

