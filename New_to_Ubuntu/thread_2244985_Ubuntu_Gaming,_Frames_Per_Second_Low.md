---
title: "Ubuntu Gaming, Frames Per Second Low"
date: 2014-09-20
forum: New to Ubuntu
---

### Post by marino4 on 2014-09-20
Hi,
before ubuntu i was using Windows XP and it was slow as hell and i whanted a change then i started to use Ubuntu! I own a lot of games on steam and most of them are Source Engine based but that dosent matter! The problem is im LOSING A LOT OF FPS on my games and i can run Counter Strike Source barely at 30 FPS if you can give me some advices PLS HELP ME!

Thanks in advance!

---

### Post by grahammechanical on 2014-09-20
What Frames Per Second were you getting with XP. Are you getting less Frames Per Second with Ubuntu? Or is it the same? What video adapter/card do you have in that machine? Does it meet the minimum requirements to run Steam games.

Regards

---

### Post by Rob Sayer on 2014-09-20
It would help if you posted hardware details, but if you're using ubuntu with the Unity desktop you may not realize that it was written for modern hardware.  You really need the same computer power you would to run windows 7 or 8.  If XP was all that slow I don't think Unity will be better.

You often hear about linux being the answer for old hardware, and I don't disagree with that at all.  But what they don't always say is that technically Linux is *just the kernel*.  It doesn't mean the desktop environment ... which isn't integrated in linux like it is in windows, it's just another application program ... will work very well.

On old hardware I'd use Xubuntu or Lubuntu.  Only Lubuntu personally if you have less than 1Gb of memory ... I use xubuntu 14.04 on my 1Gb netbook.

You can install more than one desktop in linux.  I've done it.  But I won't do it any more unless one is Qt based like KDE and the other is GTK like the other ubuntu flavors.  There is just too much of a chance you'll end up with a hard to diagnose fault.  There are lots of people here who will say it's fine but after reading every *really* knowledgeable user saying it's not good I was convinced.

If I were you I'd do a clean reinstall of something like xubuntu, assuming there aren't any other config issues.  If you reinstall try setting up a separate /home partition.

---

### Post by nineteen-73 on 2014-09-20
> **Rob Sayer said:**
>  You often hear about linux being the answer for old hardware, and I don't disagree with that at all.  But what they don't always say is that technically Linux is *just the kernel*.  It doesn't mean the desktop environment ... which isn't integrated in linux like it is in windows, it's just another application program ... will work very well.  Thanks for this bit of info!! The more I browse these forums, the more Linux is becoming clearer.

---

### Post by marino4 on 2014-09-21
Ok dude here are my specs i also have lower framerate on HL2 and other Source games such as Nuclear Dawn and for TF2 OS freezes and dosent even load the map!

My specs are:

CPU - Intel Core Duo 2.4 Ghz
GPU - Nvidia Ge-Force 610 (Low Profile)
RAM - 2 GiB (Minimum for Ubuntu 14.04 32Bit)

Any explanation or fixes? Man if there was only a Direct X Driver for Linux!

---

### Post by olliemonster on 2014-09-21
Just a few things
A) have you installed the closed sourced nvidia driver for you pc 
second as everyone else has said unity is not lightwieght if i were you i would reinstall with either lubuntu or xubuntu

---

### Post by marino4 on 2014-09-22
[ 						 							]("http://ubuntuforums.org/member.php?u=1923775")[**[COLOR=#000000]olliemonster[/COLOR]**]("http://ubuntuforums.org/member.php?u=1923775") tnx for your reply! Well i do gave a driver disc of my GPU but there are no files executable for linux, windows only so do you know from where can i get better drivers?

Thanks in advance!

---

### Post by kira-yamato-2008 on 2014-09-22
> **marino4 said:**
> [                                                      ]("http://ubuntuforums.org/member.php?u=1923775")[**[COLOR=#000000]olliemonster[/COLOR]**]("http://ubuntuforums.org/member.php?u=1923775") tnx for your reply! Well i do gave a driver disc of my GPU but there are no files executable for linux, windows only so do you know from where can i get better drivers?

Thanks in advance!

You can't use windows drivers discs. Go to System, Software & Updates, then Additional Drivers. In there should be your X.Org X Server Nouveau open source driver (Default driver) and at least a few Nvidia binary drivers, generally one current, one current (updates), one legacy, and one legacy (updates).

---

### Post by d4m1r on 2014-09-23
There is your problem right there. It seems you have a very old machine (especially if you still had XP on it) so you have to understand that you are trying to play relatively modern games on ancient hardware....Ofcourse you are going to lag trying to play at any decent settings.

Now, as to why you are seeing lower FPS under Ubuntu than you did under Windows, simply. The *nix based graphics drivers are (not yet) optimized for gaming. Steam is only recently available for *nix so you're gonna have to give the drivers a little time to catch up. However, in the future there is nothing to worry about because *nix has the potential to deliver MORE FPS than Windows....Hopefully sooner rather than later.

---

