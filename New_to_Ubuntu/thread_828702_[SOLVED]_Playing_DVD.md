---
title: "[SOLVED] Playing DVD"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2008-06-14
I started to try to play DVDs with Hardy.  Totem cam up and suggested I installed a GStreamer plugin.  I did this.  However Totem then said it could not read from the source (the whole point of the plugin I thought!)  So I followed other advice and installed vlc.  Getting that as the default player was the source of another thread I started.   I followed all the steps given by kind advisers, copying and pasting all commands to ensure accuracy. It is now possible to have vlc as default but it refuses to play DVDs - it just opens and then immediately disappears. The advice of that thread has now dried up and I am still left with the latest Ubuntu OS unable to play a DVD back - in fact returning to Totem freezes the machine.
Any one any ideas?

---

### Post by bumanie on 2008-06-14
As long as you have the codecs installed, to play a dvd in vlc click file --> open disc It should play. To install multi-media codecs? 
> sudo apt-get install restricted-extras
Also go to the medibuntu site and follow the instructions there for more multi-media codecs.

---

### Post by llama320 on 2008-06-14
while you may have already done this, it may be worth mentioning in case you haven't

first you need to install libdvdread3:

```
 sudo apt-get install libdvdread3 
```

Then go into run install-css.sh in the libdvdread3 folder:

```
 cd /usr/share/doc/libdvdread3
sh install-css.sh 
```

That made it work for me

Good Luck

---

### Post by cheesypoof on 2008-06-14
You may have to install libdvdcss2 over and above the restricted-extras.

---

### Post by Dumpy Dumpster on 2008-06-14
First of all thanks for the replies.  I installed libdvdread3, but the second command,llama320, didn't work for some reason.  The restricted-extras that bumanie suggested came up 'could not be found'!   Then I installed as per cheesypoof's suggestion and it now working.  I do not know which one of you had the secret; it was perhaps the combination that did it.  So thanks again and I leave you wih the question - why does it seem so difficult to get the dvd player working in a brand new OS?  More than likely it is just my luck!!

---

### Post by Martje_001 on 2008-06-14
It's```
sudo apt-get install ubuntu-restricted-extras
```
good luck :)

---

### Post by cariboo on 2008-06-14
The reason it takes a little bit of work, is dvd's are encrypted and in some countries it is illegal to decrypt the dvd and play them (USA).

If I remember correctly to **legally** play dvd's in windows you have to buy a codec to play them.

If you have documented what you did to get all your media files to work, the next time you need to do it, it will be a snap.

Jim

---

### Post by fred_miller on 2008-06-16
OK then the terminal shows 

dvdcss-P10131/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to [www.dtek.chalmers.se|129.16.30.198|:80](www.dtek.chalmers.se|129.16.30.198|:80).


then it timeouts and repeats over and over.  Dead link?  Can't watch dvd and that sucks.  As to buying the codecs, I have purchased Windows 98, 98se, me, 2000, xp, and even vista, which is why i am switching to linux.  I also have purchased the codecs in power DVD and win dvd, so I HAVE PAID FOR THEM OVER AND OVER!

---

### Post by mc4man on 2008-06-16
You really don't need the libdvdread.sh thing. either go here  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)  and add the medibuntu repo for the ver. of unbuntu your using and then install libdvdcss2 ( sudo apt-get install libdvdcss2  or if your on hardy run thru these commands and you'll be ok for all players
[http://ubuntuforums.org/showthread.php?t=828342](http://ubuntuforums.org/showthread.php?t=828342)

---

### Post by jwkite on 2008-06-18
> **llama320 said:**
> while you may have already done this, it may be worth mentioning in case you haven't

first you need to install libdvdread3:

```
 sudo apt-get install libdvdread3 
```

Then go into run install-css.sh in the libdvdread3 folder:

```
 cd /usr/share/doc/libdvdread3
sh install-css.sh 
```

That made it work for me

Good Luck

I've spent the last couple of weeks using this method, but I had to re-run the install script after every reboot.  This morning I looked at the script and found that it ultimately changes to a temporary directory and runs dpkg.  So I did the following, and it looks like the changes are permanent:
```

sudo -s
cd /tmp
cd dvdreadcss (or appropriate)
dpkg -i libdvdcss2<version>.deb

```
Unfortunately the dvdreadcss directory has been removed from /tmp, so I can't be exactly sure of the filenames, but hopefully my point is clear.  I hope this helps someone, as I've spent hours trying to figure out this problem.

---

### Post by Tom--d on 2008-06-18
download this:

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)

It enabled dvd playback.

In Windows, it comes built in as you pay for it. Paying for Windows also pays for the licensing!

---

### Post by ash4ever on 2008-06-18
> **Tom--d said:**
> download this:

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)

It enabled dvd playback.

In Windows, it comes built in as you pay for it. Paying for Windows also pays for the licensing!

Thanks Tom--d

That worked great for me

Ash

---

### Post by fred_miller on 2008-06-19
> **Tom--d said:**
> download this:

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)

It enabled dvd playback.

In Windows, it comes built in as you pay for it. Paying for Windows also pays for the licensing!

Ah, an easy fix that works.  I owe you one! :popcorn::popcorn::popcorn:

---

### Post by KEE on 2008-06-19
Ok after trying that link  [http://download.videolan.org/pub/lib...2.9-1_i386.deb](http://download.videolan.org/pub/lib...2.9-1_i386.deb) it stops with an error... so what do you do if you get an error message saying

 "Only one software management tool is allowed to run at the same time  please close the other application e.g update manager, aptitude or synaptic first"

i mean neither synaptic nor is update manager are not running at all as far as i can tell so =/ :confused:

---

### Post by KEE on 2008-06-19
> **Martje_001 said:**
> It's```
sudo apt-get install ubuntu-restricted-extras
```
good luck :)

OK how do you  reverse that cause now  that i installed it i cant update nor download any to with 7.10 gutsy =/

i keep getting  dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
 
:mad:

---

### Post by KEE on 2008-06-19
> **KEE said:**
> OK how do you  reverse that cause now  that i installed it i cant update nor download any to with 7.10 gutsy =/

i keep getting  dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
 
:mad:
nevermind i got it figured =) wow i never thought it would work so well Thank you for that info on dvd codecs =)

---

### Post by Eric Qel-Droma on 2008-06-25
> **Tom--d said:**
> download this:

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)

It enabled dvd playback.

In Windows, it comes built in as you pay for it. Paying for Windows also pays for the licensing!

Total Ubuntu newbie here:  Do I need to reboot after installing that?  I'm trying to run from a VIDEO_TS folder on my HD, and while Totem can play the VOB file, it can't run the IFO file, so I have no chapters.  Plus, Totem can't tell where I am in the file (I can't skip to a particular part).

With all of that said, here's an extra bonus question:  How does one convert video in 8.04/Linux-in-general?  Thanks!

Eric

---

### Post by Martje_001 on 2008-06-25
> **Eric Qel-Droma said:**
> Total Ubuntu newbie here:  Do I need to reboot after installing that?
No

> and while Totem can play the VOB file, it can't run the IFO file, so I have no chapters. Plus, Totem can't tell where I am in the file (I can't skip to a particular part).
Try VLC, it supports chapters.

> With all of that said, here's an extra bonus question: How does one convert video in 8.04/Linux-in-general? Thanks!

Usually with 'ffmpeg' in the commandline. But there are some front-ends. Search google or this forum!

---

