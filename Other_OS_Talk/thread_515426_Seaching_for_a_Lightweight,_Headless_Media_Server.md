---
title: "Seaching for a Lightweight, Headless Media Server"
date: 2007-08-02
forum: Other OS Talk
---

### Post by talkingwires on 2007-08-02
I am building a media server out of an old Point-Of-Sale system. Since the touchscreen monitor isn't working right, it will have to be headless until I get a replacement. I am having a trouble finding a suitable distro, though. Some of my goals:[LIST]
[*]Linux-based. The best one-stop solution I've found so far is [http://www.freenas.org/"]FreeNAS]("), but its a BSD-based distro.
[*]Small, and easily embedded. The system is a Celeron 733 with only 128MB of RAM. The OS is running of a 512Mb thumbdrive. Media is stored on a 500Gb USB hard drive.
[*]Configurable. I want to be able to unplug the external storage at will. I want to easily sync an iPod with the music stored on the external drive. I want to use it as my music library in Amarok on several systems. I need UPNP, preferably [TwonkyMedia]("http://www.twonkyvision.de/"), to connect to my Xbox 360.[/LIST]I'm currently using Debian 4.0, which I installed to the USB thumbdrive. But it's not a live distro, so it spends a lot of time writing unnecessary temporary files to the thumbdrive. It also hogs more memory than some light-weight distros, like [DSL]("http://damnsmalllinux.org/"). Other potential solutions, like [GeeXbox]("http://geexbox.org/en/index.html"), load X and a window manager, which are a waste on a headless system with small resources. Does anybody know of a distro that I can build off of to create this system, or am I stuck rolling my own from scratch?

---

### Post by talkingwires on 2007-08-03
Well, FreeNAS is out. I can't get it to boot off any USB thumbdrive. It complains about an "invalid slice". Google isn't much help, and I don't feel like learning the deep, inner-workings of BSD to figure out what's going on.

Does anybody have any suggestions, or do have to to [roll my own]("http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/")?

---

### Post by talkingwires on 2007-08-10
I hate to be one of those jackasses that bump their own threads, but seriously, there's not a distribution out there like the one I described? I've been working on my Debian Etch-based solution (I've been having trouble getting it to boot lately. Syslinux may be the cultprit.) and once I get it tweaked the way I like, I may release it as a torrent. Surely there's a demand for a live (flash or CD live) headless media and file server?

---

### Post by kerry_s on 2007-08-10
DSL> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

load it into ram and the thumb drive out.

---

### Post by talkingwires on 2007-08-16
> **kerry_s said:**
> DSL> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

load it into ram and the thumb drive out.
Read my original post. DSL was one of the first options I looked at. But my setup will be headless, and DSL loads X and a window manager by default, which is a waste of memory on a machine with no monitor and only 128Mb of RAM. It probably has a boot option not to load X, but without a keyboard or monitor attached, I can't really select it, can I?

I know you can add modules to DSL, but the core distro is pretty much set in stone. If I'm going to "roll my own", I'll probably just stick with stock Debian.

Another option I've found is [SLAX Frodo Edition]("http://www.slax.org/"), a variation of a lightweight live Slackware distro, expandable with modules and with nothing the kernel and core utilities installed. I may play around with it, but I've been using Debian and Debian-based distros for seven years now. I'd rather not have to learn the ins and outs of a new distro just for this project.

---

### Post by bread eyes on 2007-08-16
I can't think of anything Debian based.

---

### Post by talkingwires on 2007-08-16
> **bread eyes said:**
> I can't think of anything Debian based.Okay, I'm flexible. Do you know of another distro either fits my criteria or is easily customizable? Or were you just doing a +1 to your post count?

I've been beating my head against a wall trying to get [Debian Live]("http://debian-live.alioth.debian.org/") to work. I can boot it from my USB drive, but it absolutely, positively refuses to see the vmlinuz kernel in the root directory. (Help!)

A full Debian install on the drive worked perfectly (well, with the exception of the whole non-RAM-disk/destroying-my-flash-drive's-R/W-cycles thing), but Debian Live appears to be just broken.

---

### Post by talkingwires on 2007-09-27
*Bump*

---

### Post by razorbuzz on 2007-10-12
...speaking of people just +1ing their post count.


But on a serious note.  Most of the pre-rolled LinuxMC's are going to be too heavy for what you're wanting.  The biggest problem to output to a TV is the "no X" you're stuck on.  Using your TV as a monitor may be the easiest option to achieve your goal if playing video files directly to TV.

As for as the audio hitting your stereo for playback, the two easy methods I foresee are:
   1) Use a Y-split cable to split the audio-out from your soundcard to the left/right input channels on your stereo.

   2) Buy an Airport Express from Apple.  Connect to stereo.  Voila...wireless audio to the stereo.


On the thought of Apple products, have you thought of looking in to the AppleTV? Wireless built in, video out, audio out, nice small form factor. Can install Linux on it, connect a USB hard drive to the "service only" USB port on the back.  Tuck both small items (AppleTV and USB harddrive) into a cabinet.  Or buy the AppleTV with the larger HD and forego the USB HD.

Just a few thoughts.

:popcorn:

---

### Post by talkingwires on 2007-10-19
> **razorbuzz said:**
> Most of the pre-rolled LinuxMC's are going to be too heavy for what you're wanting.  The biggest problem to output to a TV is the "no X" you're stuck on.  Using your TV as a monitor may be the easiest option to achieve your goal if playing video files directly to TV.Okay, I didn't really give any background on my project. Here goes: Basically, I can't afford any new hardware. I work a crappy restaurant job ($7.50/hr FTW!). I can afford to pay rent, bills, and the loans on my aborted college education and not much else. The Point-Of-Sale was one of the several computers I've dug out of the dumpster in the ground floor of the office building my restaurant is located in, and the most promising. First, it's the most powerful. The others are Pentium Pros or Pentium II servers bought over a decade ago, and recently stripped of their EDO RAM, ATA-33 disk drives, and thrown away. Second, it's also pretty tiny (a ******* Micro-ATX format) and quiet, which is ideal for any media server (better seen than heard). Third, it doesn't use much power, which, as you can imagine, is also very convenient.

So, my goal for the computer is to be a light-weight media server built out of parts I have laying around. More of a file-server, really. My modded Xbox can stream any videos I want to play to my television.  I basically need a UPNP music server for my Xbox 360 and laptop and a file server for my original Xbox. One that can handle a removable drive. The iPod thing doesn't matter anymore, since my 4G iPod I won in a drawing died the other day and I can't afford to buy a replacement. (I'd only dropped the thing once, three years ago, but the HDD lost its will to live the other day.)

> **razorbuzz said:**
> As for as the audio hitting your stereo for playback, the two easy methods I foresee are:
   1) Use a Y-split cable to split the audio-out from your soundcard to the left/right input channels on your stereo.That's my current setup...

> **razorbuzz said:**
>    2) Buy an Airport Express from Apple.  Connect to stereo.  Voila...wireless audio to the stereo.And, Volia...I don't eat. drink, or by cigarettes this month! (Alright, already! I'm trying to quit!)

Seriously, though, I know of several different retail paths, and they all seem much easier than what I want to pull off.  But I have to work with what I've got. A Celeron 733 with only 128MB of RAM in a quasi-Micro-ATX form-factor with an OS running off of a USB stick. Apparently, that's a pretty tall order...

---

### Post by afonic on 2007-10-19
Try Wolvix or maybe Puppy.

They can be installed in a pen drive and with some tweaking should be able to do everything you need.

---

### Post by saulgoode on 2007-10-19
[SLAX]("http://www.slax.org/") might meet your needs.

---

### Post by regomodo on 2007-10-20
[http://www.freenas.org/](http://www.freenas.org/)

I'm surprised nobody has mentioned it yet, i think.

[http://www.smallnetbuilder.com/content/view/30179/75/](http://www.smallnetbuilder.com/content/view/30179/75/)

A very good review

[edit] ****. Just noticed it was your first choice. Anyways, the review is good if you go with Freenas. It appears to have all you want. Don't knock it just because it is BSD based.

---

### Post by Kobalt on 2007-10-22
Have you taken a look at [MediaTomb]("http://www.mediatomb.cc") or [MythTV]("http://www.mythtv.org") ?
Or even [Mythbuntu]("http://mythbuntu.org/") ...

---

### Post by talkingwires on 2007-11-05
> **saulgoode said:**
> [SLAX]("http://www.slax.org/") might meet your needs.I've [mentioned]("http://ubuntuforums.org/showthread.php?p=3197765") Slax before in this thread. So far, it seems to be the best solution. But adding the applications I want, compressing them into an image, and getting it to boot off a USB drive will basically be the same as rolling my own Linux distro. I've already tried it a few times, and couldn't get it to boot. But so far, it seems like the best bet. Let's call it my Alamo.

---

### Post by talkingwires on 2007-11-05
> **regomodo said:**
> [http://www.freenas.org/](http://www.freenas.org/)

I'm surprised nobody has mentioned it yet, i think.

[http://www.smallnetbuilder.com/content/view/30179/75/](http://www.smallnetbuilder.com/content/view/30179/75/)

A very good review

[edit] ****. Just noticed it was your first choice. Anyways, the review is good if you go with Freenas. It appears to have all you want. Don't knock it just because it is BSD based.Oh, I swallowed my pride a while back and gave FreeNAS a spin. It does not boot. The two most recent versions, both running from a CD and two different USB thumbdrives, on two seperate systems. Sixteen different configurations, if you will, and all******* of them complain about not finding the kernel image. FreeNAS' wiki turns up nothing, and neither does Google.

Seriously, if I could get it to run, it would work. Of course, I wouldn't be able to use TwonkyMedia or install my own applications onto the system. But it just won't boot! (Help?)

[SIZE="1"]*******One time, I got my desktop to boot it from a CD-RW disc. Using the installer to copy it to a USB thumbdrive produced another unbootable installation. After trying several other methods, I reburned the image to the CD-RW, only to find it wouldn't boot anymore.[/SIZE]

---

### Post by talkingwires on 2007-11-05
> **Kobalt said:**
> Have you taken a look at [MediaTomb]("http://www.mediatomb.cc") or [MythTV]("http://www.mythtv.org") ?
Or even [Mythbuntu]("http://mythbuntu.org/") ...MythTV and Mythbuntu both have heavy GUIs that I wouldn't be using. Now, MediaTomb looks interesting. Their site doesn't say whether it's compatible with the Xbox 360, but various results from Google implies that it is. I also stumbled across [FUPPES]("http://fuppes.ulrich-voelkel.de/") while searching, it is also seems promising.

Either way, they each entail rolling my own headless distro: perhaps with[ Slax Frodo]("http://www.slax.org/download.php") as the base, I would need to compile the packages and their respective dependencies. Then I'd need to bring in automagical stuff, like hot-plug, udev, and the like. Compile it all into an image file that could be dd'ed to a USB thumbdrive, but have a writable partition/file to save information like shares, network configuration, Last.fm data, plugged in PMP devices, etc.

If this is my only course, it seems like an uphill battle. But certainly a learning experience....

---

