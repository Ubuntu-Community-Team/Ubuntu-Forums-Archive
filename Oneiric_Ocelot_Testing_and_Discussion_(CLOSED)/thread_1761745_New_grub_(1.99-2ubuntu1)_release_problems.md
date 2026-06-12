---
title: "New grub (1.99-2ubuntu1) release problems"
date: 2011-05-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-18
Well I downloaded the new grub2 packages from Launchpad.
They will soon be available in Oneiric repos (right now the state is "new").

But, at least with nvidia--current, the "set gfxpayload=keep" does not work anymore.
Thus Plymouth disappeared, ugly big text appeared instead. :(

Here:
[https://launchpad.net/ubuntu/oneiric/+source/grub2/1.99-2ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/grub2/1.99-2ubuntu1)

---

### Post by Harry33 on 2011-05-21
Now the grub 1.99 is in official repos and upgradable.
The installation pulls in also the packeges grub-pc-bin and grub2-common.

Well at least for me (with NVidia GTX 285 and nvidia-current_270.41.19) the gfxpayload=keep does not work.
I do not see Plymouth any more. It does not get loaded because gfxpayload=keep is broken.

Does anyone else with a Nvidia card experience this?

---

### Post by dino99 on 2011-05-21
on actual config files (rc1) i dont have gfxpayload, so it cant break plymouth :)

so remove/purge then reinstall grub2

---

### Post by VinDSL on 2011-05-21
> **Harry33 said:**
> [...] Plymouth disappeared, ugly big text appeared instead. :(

> **Harry33 said:**
> Does anyone else with a Nvidia card experience this?
Same here... sort of...  :)

The Ubuntu logo and scrolling marque appear, but they're low res and ugly.

I've seen this before - the 10.10 dev release comes to mind.

I don't remember it ever happening during the 11.04 tests.

Now, it's back...  LoL!

---

### Post by Hanmac on 2011-05-21
the reason i think is that plymouth does not work with the nonfree drivers so it only can show txtmode

---

### Post by arpanaut on 2011-05-21
No Not nVidia but ATI card w/open source drivers is working fine.

Just got all my dependency issues cleared up today and plymouth is working fine for the first time in a long time so I was reluctant to go for it so late tonight, but what the hey, this is testing so why not.
@Harry33
Really appreciate all your "heads ups" on all this new stuff coming down the pike!

---

### Post by dino99 on 2011-05-21
ok, latest grub2 installed:
- all changes accepted (00_header, xen)
- then reboot

boot is ok: 
- grub menu as usual
- OO boot start: black screen and about 10s later get ubuntu logo with dots
- then gdm

starting startup-manager to set grub menu resolution: in my case 1024x768x24

so only get that black screen at start (10s) instead of plymouth at the very beginning 

card=8500gt, nvidia-current (genuine OO)
have tested with startup-manager settings: enabling/disabling misc. choices, but that dont change anything

---

### Post by Quackers on 2011-05-21
I installed the grub2 packages earlier and though I don't use "set gfxpayload=keep", I do use "GRUB_GFXPAYLOAD_LINUX=1920x1200" in /etc/default/grub (does that do the same thing?).
On boot I now get a black background to the grub menu (as opposed to the previous purple affair) and on selecting OO I get a black screen (no cursor) for about 15 seconds then Plymouth flashes up with its dots turned red for about 3 seconds (in proper resolution) then booting completes.
So it's a bit different but no Plymouth resolution problems.

---

### Post by kansasnoob on 2011-05-21
I'd skipped that update (busy) but when I ran todays update I noticed it was super slow generating grub.cfg,

When I say slow I mean slooooooooooooooow as mud.

Afterwards I wanted to double check and even running "grub-install" took nearly two minutes, but most amazingly running "update-grub" took nearly 15 minutes to find all of this:

> lance@lance-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found background image: desktop-grub.png
Found linux image: /boot/vmlinuz-2.6.38-9-generic
Found initrd image: /boot/initrd.img-2.6.38-9-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.38-7-generic
Found initrd image: /boot/initrd.img-2.6.38-7-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found Ubuntu 11.04 (11.04) on /dev/sda1
Found Linux Mint 10 Julia (10) on /dev/sda10
Found Debian GNU/Linux (6.0.1) on /dev/sda11
Found Ubuntu 10.04.2 LTS (10.04) on /dev/sda12
Found Peppermint One (One) on /dev/sda13
Found Ubuntu 11.04 (11.04) on /dev/sda14
Found Linux Mint Debian Edition (1) on /dev/sda15
Found Ubuntu 11.04 (11.04) on /dev/sda16
Found Ubuntu oneiric (development branch) (11.10) on /dev/sda17
Found Ubuntu 10.10 (10.10) on /dev/sda2
Found Ubuntu 10.04.2 LTS (10.04) on /dev/sda3
Found Ubuntu 11.04 (11.04) on /dev/sdb1
done


Of course I was then running it from sda17.

I guess it looks really deep now, deep enough to allow for a coffee making break or a potty break, or maybe both :p

---

### Post by MAFoElffen on 2011-05-21
> **Quackers said:**
> I installed the grub2 packages earlier and though I don't use "set gfxpayload=keep", I do use "GRUB_GFXPAYLOAD_LINUX=1920x1200" in /etc/default/grub (does that do the same thing?).
On boot I now get a black background to the grub menu (as opposed to the previous purple affair) and on selecting OO I get a black screen (no cursor) for about 15 seconds then Plymouth flashes up with its dots turned red for about 3 seconds (in proper resolution) then booting completes.
So it's a bit different but no Plymouth resolution problems.
Try to set the 3rd optional parm (depth) of that and see what is does.
```

GRUB_GFXMODE=1920x1200x24

```In the /etc/default/grub file. 

One of the current workarounds is to add a line:
```

GRUB_GFXPAYLOAD_LINUX=text

```to the /etc/default/grub, which tells the kernel to ignore graphics modesets.  Haven't seen it used as you have it, with WIDTHxHEIGTH... That would be ignored because of invalid parms, right? 

(dino99's way works with startup-manager, but writes directly to grub.cfg, which every update on grub will then overwrite and lose those changes.)

Not experiencing any additional problems here *yet *on nvidia graphics that I didn't already resolve during natty testing... But I do still have 2 open upstream bugs with GNU Grub 1.99 on other related issues.. One on theming issues, one on passing invalid graphics data when GRUB_GFXMODE is set to it's default, auto.

---

### Post by VinDSL on 2011-05-21
> **kansasnoob said:**
> I'd skipped that update (busy) but when I ran todays update I noticed it was super slow generating grub.cfg,

When I say slow I mean slooooooooooooooow as mud.[...]
I've noticed the slowness too.

Last night I got rid of a superfluous kernel (2.6.39rc7) - 2.6.39 is out now.

Grub must have been performing enhanced interrogation on my hdd.  LoL!  :D

It was like watching water slowly drip on my system, sucking the life out of it!

---

### Post by Quackers on 2011-05-21
I forgot about that! update-grub is indeed much slower now.

---

### Post by ranch hand on 2011-05-21
They really ought to stick to pulling things from the Debian unstable repo instead of the experimental repo.  Things are not really ready to use from there.

At this point in the cycle this should not be a problem though.  Should be fixed pretty fast.

---

### Post by VinDSL on 2011-05-21
> **ranch hand said:**
> They really ought to stick to pulling things from the Debian unstable repo instead of the experimental repo.[...]
Heh!  I aimed to do this, but was afraid to pull the trigger.  :D

```

vindsl@Zuul:~$ cat /etc/apt/sources.list | grep -v "##"

# deb cdrom:[Ubuntu 11.04 _Oneiric Ocelot_ - Release i386 (20110504)]/ oneiric main restricted

deb http://archive.ubuntu.com/ubuntu oneiric main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted multiverse universe

deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted multiverse universe

deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted multiverse universe

deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

# deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main

deb http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed restricted main multiverse universe

[B][COLOR="Red"]# deb http://ftp.de.debian.org/debian sid main
# deb-src http://ftp.de.debian.org/debian sid main[/COLOR][/B]

vindsl@Zuul:~$ 

```

There were 100's of changes.

Maybe I'll try it, before I install Alpha 1, just to see what happens.

---

### Post by ranch hand on 2011-05-21
> **VinDSL said:**
> Heh!  I aimed to do this, but was afraid to pull the trigger.  :D

Maybe I'll try it, before I install Alpha 1, just to see what happens.
It is a very bad idea to mix the repos for Ubuntu and Debian.

There are many packages that you can get away with it on but Ubuntu changes some of the paths and some of the files all together.  This is probably to improve speed or to make things compatible with other packages that they use.

Just as an example all of your (or most anyway) images used in Ubuntu are in /usr/share/backgrounds.  Most in Debian are in /usr/share/images/desktop-base.  These are just images.  Little changes like that in a system file and you have some major problems.

There are also things like the package name itself.  If you have a call for a package from somewhere in Ubuntu and you have replaced that with a package from Debian with a slightly different name there will be a problem even if the packages are identical which is not certain at all.

If you have more than one box it is interesting to look at these things in Synaptic.  My wifes laptop runs 10.04.  I have an install of Squeeze.  These are about as close as you can get to a match.  There are some fairly major differences in key areas between them.

Here on this forum, having to do with ralink cards, ronacc points out that there is no "firmware-linux-nonfree" package in Ubuntu and that he can get the same fail in Debian by installing that package there.  As he points out this is probably due to Ubuntu incorporating that firmware in the kernel.

You could probably install grub from one to the other.  If you put the Debian grub on Ubuntu you are going to have problems getting your menu background to work as Debian has edited the files so that the only place grub looks for that image is still in /usr/share/images/desktop-base.  Can't recall what the image name that it called for is as I have changed that in all my installs.

But, as you can see, a whole sale dumping of Debian packages onto Ubuntu, or the reverse, is going to cause a broken system that will probably require a reinstall to fix.

I find it interesting that Kanotix Hellfire, based on Debian, uses the Ubuntu kernel (recompiled) and Wine 1.3.19 (per Lucid PPA).  They must be very careful, as must the Ubuntu devs, in this mixing.  One package wrong and the whole thing may collapse.

I was just over on my transplanted Lounge Lizard install that went from Ubuntu 11.10 to Debian Sid.  It works great.  The home directory is set up the same.  I removed (saved some in another folder) all ~/.whatever files from the /home partition.  Installed Debian on the / partition with format and the /home partition without formatting.  That way I avoided the problem of mixing repos.

I would not install more than one at a time from that repo and be very careful what I picked.  Not sure I have the guts to risk an install like that at all.

---

### Post by Harry33 on 2011-05-22
> **Hanmac said:**
> the reason i think is that plymouth does not work with the nonfree drivers so it only can show txtmode

Nope,
Plymouth works very well with Nvidia proprietary drivers (nvidia-current).
And it has been working up to this grub2 update (1.99).
It can be set to work with this command:
gfxpayload=keep.

The system gfxpayload is set to work is by means of a gfxpayload lists.
You have a package called grub-gfxpayload-lists installed.
During boot process grub checks from that list, does your graphics card support gfxpayload=keep, and if it does, it is enabled automatically;
if it does not, then text mode is enabled.

There is bug report on this issue:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/784981](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/784981)

Funny, that bug report is a monologue now.
Now, this latest update of grub_1.99, this does not work anymore.
The text mode is used now.

---

### Post by dino99 on 2011-05-22
adding comments to previous #7:

on shutdown now i dont get plymouth but screen filled by shutdown comments (not a big deal but)

---

### Post by Quackers on 2011-05-22
Harry, I'm not getting text mode here. Plymouth is normal but briefly shown.
As I said earlier I have the extra line in /etc/grub/default but have made no change to grub-gfxpayload-lists

---

### Post by Harry33 on 2011-05-22
> **Quackers said:**
> Harry, I'm not getting text mode here. Plymouth is normal but briefly shown.
As I said earlier I have the extra line in /etc/grub/default but have made no change to grub-gfxpayload-lists

Do you have Nvidia graphics card and nvidia-current in use?
This issue is bad only with proprietary drivers and at least with default grub settings.

---

### Post by Quackers on 2011-05-22
I have Nvidia 8600M GT using 270.41.06

---

### Post by Hanmac on 2011-05-22
i have ATI Radeon HD 3300 Graphics with fglrx and it does not work

---

### Post by coffeecat on 2011-05-22
> **ranch hand said:**
> 
Here on this forum, having to do with ralink cards, ronacc points out that there is no "firmware-linux-nonfree" package in Ubuntu and that he can get the same fail in Debian by installing that package there.  As he points out this is probably due to Ubuntu incorporating that firmware in the kernel.

You need to shuffle the words about a bit. :) There's been a linux-firmware-nonfree package in Ubuntu since Karmic. In Jaunty they split the nonfree stuff out of "linux-firmware". It's still there - linux-firmware-nonfree that is - I've just checked in Oneiric's Synaptic. I don't know whether it will help with ronacc's ralink problem, but the contents of the package are put in /lib/firmware.

**EDIT**: Oops, sorry - grossly off-topic. I just happened to notice the comment and thought it would be helpful to point out the existence of linux-firmware-nonfree.

---

### Post by Harry33 on 2011-05-22
> **Quackers said:**
> Harry, I'm not getting text mode here. Plymouth is normal but briefly shown.
As I said earlier I have the extra line in /etc/grub/default but have made no change to grub-gfxpayload-lists

That extra line in /etc/default/grub may override the gfxpayload checking.

---

### Post by Harry33 on 2011-05-23
This issue is still not fixed in todays update of 1.99-4ubuntu1.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/grub2/1.99-4ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/grub2/1.99-4ubuntu1)

And once again, downgrading to 1.99 rc1 version solves the issue.

---

