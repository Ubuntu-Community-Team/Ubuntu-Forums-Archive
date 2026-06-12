---
title: "Rough iso-testing"
date: 2011-08-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-08-02
Man oh man, I haven't played with Ubuntu much lately and I'm just doing Alpha3 iso-testing and I'm going buggy with bugs :lolflag:

Looks like the devs are going to be very busy between now and the first Beta :D

---

### Post by cpatrick08 on 2011-08-02
> **kansasnoob said:**
> Man oh man, I haven't played with Ubuntu much lately and I'm just doing Alpha3 iso-testing and I'm going buggy with bugs :lolflag:

Looks like the devs are going to be very busy between now and the first Beta :D

what kind of bugs did u find

---

### Post by 3rdalbum on 2011-08-02
> **kansasnoob said:**
> Man oh man, I haven't played with Ubuntu much lately and I'm just doing Alpha3 iso-testing and I'm going buggy with bugs :lolflag:

Looks like the devs are going to be very busy between now and the first Beta :D

You'd better get reporting now ;-)

---

### Post by kansasnoob on 2011-08-03
Well, we're waiting for the 4th build now. The devs squashed a lot of bugs between the 1st build and the second build, squashed a few more between the 2nd and the 3rd build, and this is what we're left with ATM:

[http://iso.qa.ubuntu.com/qatracker/test/6157](http://iso.qa.ubuntu.com/qatracker/test/6157)

There are of course other issues but those are the real show stoppers :D

Generally (and sadly) the number of iso-testers tends to taper off badly as the 3rd, 4th, or 5th iso's roll out. I suppose some testers just get tired or busy.

Like I have to go to the hospital for some testing today so I'll be slow testing the new iso when it rolls out :(

---

### Post by jerrylamos on 2011-08-03
> **cpatrick08 said:**
> what kind of bugs did u find

For starters, mouse cursor doesn't move.  That's from zsync today.

3.33 gHz Compaq presario tower with other partitions Lynx, Meerkat, Narwhal running fine.

Jerry

p.s. Just for giggles tried apt-get update, apt-get upgrade and it wanted to change practically every package, this on a Live .iso just zsync'd today, checksum's matching ...... abandon ship, obviously.

---

### Post by kansasnoob on 2011-08-03
I'm sure we'll have a build #5 soon due to this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/820485](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/820485)

I tried to install twice and failed.

I actually tried 3 times but found a new catch to these bugs causing me to abort:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

Fun times at the old rodeo ;)

I'm glad I'm well stocked on DVD's.

---

### Post by kansasnoob on 2011-08-03
Totally OT but I need to share a chuckle.

I recently set up my first home router and I have two computers sharing input/output through a KVM switch. One of the boxes has Win XP w/McAfee security and I swear that it takes longer just for McAfee to allow things to launch or shut down than it takes to completely reboot Ubuntu.

I can't believe I used to use that every day!!!!!!!

---

### Post by kansasnoob on 2011-08-03
#5 just rolled out of the chute :D

---

### Post by jerrylamos on 2011-08-03
Just did a zsync from Daily Build, checksums match, md5sums match:

oneiric-desktop-i386.iso            03-Aug-2011 21:18  712M

No desktop on live boot.  Oneiric says lightdm is running, perhaps on some virtual console somewhere....

Sometimes, frequently actually, the daily build a day or two before an Alpha/Beta/RC is virtually the same as the Alpha/Beta/RC, md5sum and all.
I hope not this time.  

Will try again on next build update....

Jerry

---

### Post by kansasnoob on 2011-08-03
> **jerrylamos said:**
> Just did a zsync from Daily Build, checksums match, md5sums match:

oneiric-desktop-i386.iso            03-Aug-2011 21:18  712M

No desktop on live boot.  Oneiric says lightdm is running, perhaps on some virtual console somewhere....

Sometimes, frequently actually, the daily build a day or two before an Alpha/Beta/RC is virtually the same as the Alpha/Beta/RC, md5sum and all.
I hope not this time.  

Will try again on next build update....

Jerry

Are you using a VM?

I test on actual hardware.

Regardless things only get fixed if you use Launchpad to report bugs, otherwise they just persist ;)

I'm now down to some basic stuff like lacking a restart or logout option on the live CD/DVD and some other minor bugs.

---

### Post by mc4man on 2011-08-03
> **kansasnoob said:**
>  like lacking a restart or logout option on the live CD/DVD and some other minor bugs.
The session indicator on the live session has a log out option and has for some time now
The log in screen has the restart option although it doesn't work on the live session, nor does the shutdown (shutdown does work from the desktop session indicator

---

### Post by kansasnoob on 2011-08-04
> **mc4man said:**
> The session indicator on the live session has a log out option and has for some time now
The log in screen has the restart option although it doesn't work on the live session, nor does the shutdown (shutdown does work from the desktop session indicator

It's odd. There was a reversion in 20110803-i386 where logout was missing again, but in 20110803.1-i386 it was back again.

The restart from login screen was just the opposite. I went through and reverified that this AM.

In total we had five rounds of Ubuntu iso-testing this time and it gets almost mind boggling at times ;)

Add to that a full round of Lubuntu iso-testing and I feel like I just hosted a three day LAN party :lolflag:

---

### Post by jerrylamos on 2011-08-05
> **kansasnoob said:**
> Are you using a VM?

I test on actual hardware.

Regardless things only get fixed if you use Launchpad to report bugs, otherwise they just persist ;)


Yes, I use actual hardware, Compaq Presario 3.33 gHz, ati radion xpress 200.

Launchpad ubuntu-bug is useless because you have to have desktop and browser running and in this case the desktop doesn't run.  That's the problem.

I did notice Alpha 3 live apt sources.list only had 4 lines in it.  So from command line copied in a sources.list from Alpha 2, much much longer.

Installed lightdm from that, and voila the desktop came up.

Mouse wouldn't budge, can't report anything to Launchpad unless everything is running.

Let me see if there's anything in Oneiric forum on how to get mouse to move.

Plan is to boot on actual hardware, 
get to the failure, 
use ubuntu-bug, 
get to the point where it asks to start browser, 
then go off and do copy Alpha 2 sources.list, 
install lightdm, 
get mouse running, 
get the browser running, 
then finish the ubuntu-bug report.  

Fat chance but I'm trying.

Jerry

---

### Post by kansasnoob on 2011-08-05
> **jerrylamos said:**
> Yes, I use actual hardware, Compaq Presario 3.33 gHz, ati radion xpress 200.

Launchpad ubuntu-bug is useless because you have to have desktop and browser running and in this case the desktop doesn't run.  That's the problem.

I did notice Alpha 3 live apt sources.list only had 4 lines in it.  So from command line copied in a sources.list from Alpha 2, much much longer.

Installed lightdm from that, and voila the desktop came up.

Mouse wouldn't budge, can't report anything to Launchpad unless everything is running.

Let me see if there's anything in Oneiric forum on how to get mouse to move.

Plan is to boot on actual hardware, 
get to the failure, 
use ubuntu-bug, 
get to the point where it asks to start browser, 
then go off and do copy Alpha 2 sources.list, 
install lightdm, 
get mouse running, 
get the browser running, 
then finish the ubuntu-bug report.  

Fat chance but I'm trying.

Jerry

Sorry, I somehow thought you were using VM's.

Aside from Unity I think many bugs are related to lightdm, although you'll notice I say "related to" :)

Throughout this round of testing it seems like casper needs to be tweaked to fit lightdm so which is to blame?

It's sort of like a wedding gown not fitting. Who's to blame ...... the bride or the seamstress :lolflag:

---

### Post by ranch hand on 2011-08-05
Write the Launchpad address down.  Boot to recovery and login.
```

sudo apt-get install elinks

```
and;
```

elinks

```
Go to Lanuchpad and report bug.

I put elinks and mc (terminal file browser) packages on all my installs just in case.

---

### Post by jerrylamos on 2011-08-05
> **ranch hand said:**
> Write the Launchpad address down.  Boot to recovery and login.
```

sudo apt-get install elinks

```
and;
```

elinks

```
Go to Lanuchpad and report bug.

I put elinks and mc (terminal file browser) packages on all my installs just in case.

Thanks, ranch hand, I'm going to have to learn how to use elinks with ubuntu-bug.  A bit late tonight.

Jerry

---

### Post by ronacc on 2011-08-05
thanks for the tip on elinks , I've been using MC for a long time but hadn't found elinks .

---

### Post by jerrylamos on 2011-08-07
> **ranch hand said:**
> Write the Launchpad address down.  Boot to recovery and login.
```

sudo apt-get install elinks

```
and;
```

elinks

```
Go to Lanuchpad and report bug.

I put elinks and mc (terminal file browser) packages on all my installs just in case.

Well, on Oneiric Live, 
sudo apt-get install elinks
can't find it.  Note, can't find lightdm either.

So I copy in apt/sources.list from Alpha2 and sure enough, elinks installs.

Then do 
ubuntu-bug lightdm
it says 1 to start browser, I reply 1 and elinks starts.
Page asks for username and password.
I use tab to get to username, the field is highlighted white, no matter what key I push nothing appears on screen.

Now I can tab to password and enter that, but what good is that if I can't enter userid?

Any thoughts?

Jerry

---

### Post by jerrylamos on 2011-08-08
> **jerrylamos said:**
> Just did a zsync from Daily Build, checksums match, md5sums match:

oneiric-desktop-i386.iso            03-Aug-2011 21:18  712M

No desktop on live boot.  Oneiric says lightdm is running, perhaps on some virtual console somewhere....

Sometimes, frequently actually, the daily build a day or two before an Alpha/Beta/RC is virtually the same as the Alpha/Beta/RC, md5sum and all.
I hope not this time.  

Will try again on next build update....

Jerry
Found the problem.

Bios boots on the IDE drive which Narwhal thinks is /dev/sda.

This is a tower, there is a second drive, a SATA.  Narwhal thinks it is /dev/sdb.

The rub is Grub2 thinks the non-boot SATA is /dev/sda and the IDE is /dev/sdb.  Just reversed from what the bios and Narwhal think.

Now booting Live Oneiric Ocelot, Install thinks the second non-boot drive is /dev/sda and the boot hard drive is /dev/sdb.

This being a test pc, there are Ubuntu images on both hard drives, so I just have to fish around to see what Oneiric did this time.

Right now, 
booting on the IDE, Narwhal thinks it is /dev/sda.
Booting on the IDE again, Ocelot A3 thinks it is /dev/sdb.

Any way to get Ocelot to get it's head screwed on right, the boot drive is /dev/sda like Narwhal knows?

Thanks, Jerry

---

