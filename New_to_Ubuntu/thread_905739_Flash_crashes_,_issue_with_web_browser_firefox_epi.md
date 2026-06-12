---
title: "Flash crashes , issue with web browser firefox epiphany galeon"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by fuwkej on 2008-08-30
Is ubuntu ever going to come out with a fix for flash that crashes web browsers? The bug report was filed almost immediately when Hardy came out, but there is still no fix. It can be very annoying when you are typing something in one tab and flash from another crashes the browser, and you lose all your data. It's almost a switch back to Windows issue. (Though I do like Ubuntu overall, it is much better than Windows)

The bug is:

-Flash crashes any type of web browser at random when first initializing
-Flash crashes any type of web browser always on certain sites

---

### Post by alienexplorers on 2008-08-30
I found that disabling Ubuntu Firefox Modifications in addons and the flash crashes were minimized in firefox.

---

### Post by kellemes on 2008-08-30
> **laverabe said:**
> Is ubuntu ever going to come out with a fix for flash that crashes web browsers? The bug report was filed almost immediately when Hardy came out, but there is still no fix. It can be very annoying when you are typing something in one tab and flash from another crashes the browser, and you lose all your data. It's almost a switch back to Windows issue. (Though I do like Ubuntu overall, it is much better than Windows)

The bug is:

-Flash crashes any type of web browser at random when first initializing
-Flash crashes any type of web browser always on certain sites

What Flashplayer do you have installed? I recently got the latest from the Adobe website and have not seen any crash till now.

---

### Post by fuwkej on 2008-08-30
Unfortunately, I had no luck with disabling the modifications in addons, it still crashes. I don't think it is a firefox problem, since it does it in the other two browsers I tried.

It may be a flash problem, but I had tried upgrading to the newer flash, and it still crashes. My flash version is 9.0 r124 as listed under the Plugins section.

---

### Post by lovinglinux on 2008-08-30
Try running Memtest to check if you memory sticks are ok. I had the same problem under Windows and was going nuts when decided to install Ubuntu. The Live CD has Memtest, so I did a few tests and found that one memory card was faulty.

Since I replaced that memory card Firefox is not crashing as it used to, like 3 times per minute. It crashes now when I try to switch tabs while a flash web site is loading on another tab, but nothing compared with the nightmare before the memory replacement.

BTW, I have deleted Windows and I'm a happy Ubuntu user for about two weeks.

---

### Post by fuwkej on 2008-09-01
I only have a single RAM card, and it's 1ghz, so I don't think I need to upgrade that. This system was prebuilt with Ubuntu, since I liked how Ubuntu worked on my last comp, I bought a prebuilt one from Dell. I've never had any problems with flash with Fiesty or Gutsy, but Heron is giving me problems. It is not severe, and only occurs when first opening the flash window. Once the video starts it's no problem, and I am usually able to get any flash to work after 1 or 2 tries; it is more an annoyance. There is only one site that I can't view the flash, it's comedy central (the daily show) website; doesn't work for some reason.

Can't wait for the next distro, I**** I****, because HH was a COMPLETE nightmare compared to FF and GG (I had other problems, most of which are resolved, though the side panels do freeze from time to time)

---

### Post by kansasnoob on 2008-09-01
[http://ubuntuforums.org/showthread.php?t=906896](http://ubuntuforums.org/showthread.php?t=906896)

It's working great!

---

### Post by fuwkej on 2008-09-01
Well, no joy. I tried the new flash plugin, downloaded, extracted, and installed (no small feat for me!), and it said it installed perfectly. This was after I removed the old flash. But no flash appeared in mozilla. I reinstalled the nonfree flash from the repositories and it appears to returned to the way it was before.

Seems like everytime I try to fix 1 thing, 2 things break. Unfortunately now when the firefox crashes when flash freezes it, it no longer recovers the pages that were last viewed in it. Oy! :(

Linux is great, but it's confusing as all hell!

---

### Post by ctswhole on 2008-09-01
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

This solved all my flash problems

---

### Post by lazyart on 2008-09-01
I use a FF plugin that i believe is called flashblocker.  Simply put, it won't start flash animations until you click on them.  Flash is particularly annoying in 64 bit as it just eats up resources like mad.  If you've had a menu drop down BEHIND a flash animation you'll instantly appreciate flashblocker.

---

### Post by lovinglinux on 2008-09-02
> **lazyart said:**
> I use a FF plugin that i believe is called flashblocker.  Simply put, it won't start flash animations until you click on them.  Flash is particularly annoying in 64 bit as it just eats up resources like mad.  If you've had a menu drop down BEHIND a flash animation you'll instantly appreciate flashblocker.

You can also use NoScript extension for Firefox, which blocks Flash and Java. Besides the flash issues, NoScript is an extra layer of protection. For example, other day I received an e-mail from Veoh. I was pissed about this service, because they simply blocked several countries (mine included) from accessing the videos, due to commercial interests (or lack of it). Anyways, in a moment of rage I clicked the link to see what kind of advertisement they were sending, to someone that is not even allowed to browse their site. Obviously the e-mail and the link were bogus and a script appeared filling the entire screen. NoScript blocked it and I don't want to know what it was :)

---

### Post by fuwkej on 2008-09-02
> **kansasnoob said:**
> [http://ubuntuforums.org/showthread.php?t=906896](http://ubuntuforums.org/showthread.php?t=906896)

It's working great!

Now flash is completely broken. I followed the steps for i386, and everything seemed to be working; I rebooted, and opened a flash page and it displayed the flash icon and said I needed to install flash. I tried to undo everything by reinstalling the nonfree library like before, but it's already installed. Things always get worse when I try to fix them. Ironically though, immediately after rebooting the first time, the daily show video played for about 2 seconds, but then never worked again. (Nor any other flash).

---

### Post by kansasnoob on 2008-09-02
> **laverabe said:**
> Now flash is completely broken. I followed the steps for i386, and everything seemed to be working; I rebooted, and opened a flash page and it displayed the flash icon and said I needed to install flash. I tried to undo everything by reinstalling the nonfree library like before, but it's already installed. Things always get worse when I try to fix them. Ironically though, immediately after rebooting the first time, the daily show video played for about 2 seconds, but then never worked again. (Nor any other flash).

OK, let's start here:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Now, you'll notice at the beginning there are some specific instructions for 64bit users. I assume you're not using 64bit:confused:

Just go with all the i386 instructions! I'm goona try to stay with you. No guarantee ......... I'm tired!

---

### Post by kansasnoob on 2008-09-02
> **kansasnoob said:**
> OK, let's start here:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Now, you'll notice at the beginning there are some specific instructions for 64bit users. I assume you're not using 64bit:confused:

Just go with all the i386 instructions! I'm goona try to stay with you. No guarantee ......... I'm tired!

Or if you're sure you did that all correctly we could skip ahead to:

```
cd ~/.mozilla
```

```
rm flashplayer.xpt libflashplayer.so
```

Wait until it's done.

```
sudo apt-get remove --purge flashplugin-nonfree
```

Then DL this:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

It's a .deb! No hassle! Just let it install!

---

### Post by fuwkej on 2008-09-03
Every step I make everything gets worse.

I start off with flashing working most of the time.
Then flash doesn't work
and now..
flash doesn't work and all my bookmarks, settings, addons, and everything in firefox was erased. (Thank god for foxmarks)



I do appreciate the help though.

While I'm at it, know of a good backup program? I know if I try to fix this, I will end up having to fix Ubuntu from a terminal screen because Ubuntu will not start up. (I have done this twice before..)

I see why so few switch from Windows/Mac to Linux; you have to be a programmer to have a fully functioning operating system.

---

### Post by fuwkej on 2008-09-03
I forgot to mention what I did to make it worse.


I removed the files, and the apt-get remove nonfreeflash command, and downloaded the .deb file. It seemed to install fine, and I rebooted firefox and it was as if I started firefox on a fresh operating system install (everything default). And unfortunately flash still does not work.

---

### Post by fuwkej on 2008-09-06
I was able to get video working by uninstalling everything related to flash under Synaptic package manager, and reinstalling the flash driver from their website.

Unfortunately, now the sound does not work, any suggestions?

---

### Post by Kaneda187 on 2008-09-06
hey just breezed through your post... any success with stoping flash vids crashing firefox?? its so annoying!!:(

---

### Post by fuwkej on 2008-09-06
For your crash problem, I would remove all installations in synaptic package manager dealing with flash (except libflashsupport) and in terminal type:

[HTML]
sudo apt-get install flashplugin-nonfree[/HTML]


For my issue, flash video and sound now works again. Unfortunately, though, firefox no longer remembers what page you were on if it crashes.

For the audio, I had to reinstall libflashsupport in Synaptic package manager.

---

