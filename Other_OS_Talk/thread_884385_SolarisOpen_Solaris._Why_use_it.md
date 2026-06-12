---
title: "Solaris/Open Solaris. Why use it?"
date: 2008-08-08
forum: Other OS Talk
---

### Post by kaldor on 2008-08-08
I have been trying to learn more and more about unix and unix-like OSes. Could someone tell me what Solaris is used for, why it is used, and if it is worth using as a desktop computer?

---

### Post by zmjjmz on 2008-08-08
Solaris is great for servers and large mainframes, and what's wrong with having another desktop OS?
:)

---

### Post by Yuki_Nagato on 2008-08-08
Sun brought us Java and OpenOffice.  Solaris is a decent product, too.  While not currently using it, I keep it in the back of my mind.  Their greatest strength, (and weakness) is their complete backwards compatibility,

---

### Post by DeadSuperHero on 2008-08-08
Solaris is definitely an interesting one. It has been traditionally used in servers, and for admins. However, OpenSolaris is working on targeting desktop users.

A few good things:
-The ZFS filesystem is excellent. All data can be combined into a large "pool" of data, spanning across hard drives in a way similar to RAID.
-Flash playback is better because Solaris uses one standard set of media libraries.
-The Solaris kernel is excellent, it is the remaining child of the corporate unixes of the 80's and 90's. It is rock solid, and heavily backwards compatible.
-Sun Microsystems created Solaris,Java, and OpenOffice. So, you can expect they're native on here.
-It's now possible to compile and use the latest versions of KDE and Gnome.
-OpenSolaris ships with Gnome and BASH, so many of the functions and commands are familiar to Linux users.
-DTrace is a tweaking system allowing users to get maximum performance out of it.
-Everytime you do a major update, the OS clones an image of itself and allows you to boot it in GRUB. The nice thing about this is if you really mess something up, you can roll back an image, and still have all your bookmarks from whatever version you just messed up.
-A great developer community. Nice people.

Bad points
-IPS package manager needs a lot of improvements. The GUI is really slow and unresponsive for most people.
-Older version of Gnome.
-Not as many packages for it.
-Less hardware support.

That said, I quite like it, and I think it holds a lot of promise.

But, you don't HAVE to use it. There's so many choices, and that's why I love FOSS stuff!

---

### Post by NovaAesa on 2008-08-08
My Uni has Solaris machines in a fair few of their computer labs. It's the really old kind of Solaris though :S

---

### Post by kaldor on 2008-08-08
Is Solaris much like Linux?

---

### Post by namegame on 2008-08-09
> **kaldor said:**
> Is Solaris much like Linux?

Honestly, when I first started my adventure into the world of Linux, I thought Solaris was just another distribution of Linux.

To the untrained eye, they are very similar.

If you are comfortable with Linux, Solaris shouldn't be a problem.

---

### Post by SunnyRabbiera on 2008-08-09
Well I say the best reason to use solaris is if you are developer.
Solaris has a bright future ahead of it once it gets more compatibility and packages.

---

### Post by L815 on 2008-08-09
From my minimal experience with the Live CD, I must say they are heading in the right direction. With a bit better hardware support, and more packages (all the stuff said before), it will creep up!

---

### Post by trickii on 2008-08-15
Solaris 10 This is claimed by many as the most advanced operating system in commercial use today.Free Solid relieable and feels good to use on your desktop.The cons are it is very complex for the less advanced user.The cons are that there is limited hardware support although manafactures are now supporting this sysstem more and more.To test if it would run on your computer there is a tool on the Sun site which will test your hardware for free to see if its suitable. It is currently been developed as a Opensource project called OpenSolaris.The first release of this hybrid Unx/linux OX was made on 05/08.Although impressive it is still work in progress for desktop use.This can be download from the sun site on live CD or you should wait with great excitment for the next edition available in Nov for a more complete solution.

Would suggest as a desktop user you down load a Unix distro based on Opensolaris called Benelix which is a very much complete desktop solution. 

Rob

[http://www.belenix.org/index.php](http://www.belenix.org/index.php)

---

### Post by Twitch6000 on 2008-08-15
> **Mr. Psychopath said:**
> Solaris is definitely an interesting one. It has been traditionally used in servers, and for admins. However, OpenSolaris is working on targeting desktop users.

A few good things:
-The ZFS filesystem is excellent. All data can be combined into a large "pool" of data, spanning across hard drives in a way similar to RAID.
-Flash playback is better because Solaris uses one standard set of media libraries.
-The Solaris kernel is excellent, it is the remaining child of the corporate unixes of the 80's and 90's. It is rock solid, and heavily backwards compatible.
-Sun Microsystems created Solaris,Java, and OpenOffice. So, you can expect they're native on here.
-It's now possible to compile and use the latest versions of KDE and Gnome.
-OpenSolaris ships with Gnome and BASH, so many of the functions and commands are familiar to Linux users.
-DTrace is a tweaking system allowing users to get maximum performance out of it.
-Everytime you do a major update, the OS clones an image of itself and allows you to boot it in GRUB. The nice thing about this is if you really mess something up, you can roll back an image, and still have all your bookmarks from whatever version you just messed up.
-A great developer community. Nice people.

Bad points
-IPS package manager needs a lot of improvements. The GUI is really slow and unresponsive for most people.
-Older version of Gnome.
-Not as many packages for it.
-Less hardware support.

That said, I quite like it, and I think it holds a lot of promise.

But, you don't HAVE to use it. There's so many choices, and that's why I love FOSS stuff!

That makes me wanna try OpenSolaris <.<.

---

### Post by Dremora on 2008-08-16
> **Twitch6000 said:**
> That makes me wanna try OpenSolaris <.<.

Better run a level 3 DTrace on the warp engines! :lolflag:

---

### Post by DeadSuperHero on 2008-08-17
> **Twitch6000 said:**
> That makes me wanna try OpenSolaris <.<.

Well, the best place to start is on their site. 

I must warn you, though. There definitely is a learning curve. Things that I currently don't like about it:

-I'm stuck with Rythmbox on it until I can be bothered to compile Mono and Banshee. It's an alright player, but I happen to just adore Banshee. There's always Amarok, though.
-The package manager got so incredibly unusable for me.
-Using BlastWave.org's repos is a little tricky, as you have to implement the "pkg-get" command into BASH. Not too hard, but you'll need to know that you'll sometimes have to move your downloaded BlastWave packages to /usr/lib or /usr/bin
-I couldn't get Wine to work, was probably my fault though.
-My Microsoft Keyboard didn't work all the way. This was a minor surprise because it works great with everything else. I was enjoying a good play through Full Throttle when I realized that F5 didn't work, and I couldn't save.

---

### Post by cardinals_fan on 2008-08-17
> **Mr. Psychopath said:**
> 
-The package manager got so incredibly unusable for me.
-Using BlastWave.org's repos is a little tricky, as you have to implement the "pkg-get" command into BASH. Not too hard, but you'll need to know that you'll sometimes have to move your downloaded BlastWave packages to /usr/lib or /usr/bin

The package management is temporarily a disaster, but it should improve with time.

It's not BlastWave anymore - read [this]("http://www.cuddletech.com/blog/pivot/entry.php?id=960").  The new site is [here]("http://www.opencsw.org/").

---

### Post by Twitch6000 on 2008-08-17
> **Mr. Psychopath said:**
> Well, the best place to start is on their site. 

I must warn you, though. There definitely is a learning curve. Things that I currently don't like about it:

-I'm stuck with Rythmbox on it until I can be bothered to compile Mono and Banshee. It's an alright player, but I happen to just adore Banshee. There's always Amarok, though.
-The package manager got so incredibly unusable for me.
-Using BlastWave.org's repos is a little tricky, as you have to implement the "pkg-get" command into BASH. Not too hard, but you'll need to know that you'll sometimes have to move your downloaded BlastWave packages to /usr/lib or /usr/bin
-I couldn't get Wine to work, was probably my fault though.
-My Microsoft Keyboard didn't work all the way. This was a minor surprise because it works great with everything else. I was enjoying a good play through Full Throttle when I realized that F5 didn't work, and I couldn't save.

I like Rythmbox and I toke the learning curve of Linux didn't I? :p.
Really though I hope it likes my laptop :(.

---

### Post by DeadSuperHero on 2008-08-17
It should work fine. If you need help, I can scour some of the OpenSolaris boards looking for any fixes you need.

If you want 3D working out of the box, I just hope your laptop either has an Intel or an Nvidia card in it. ATI is currently incompatible.

---

### Post by Dremora on 2008-08-18
Things keeping me from using Solaris:

1. IPS is a POS. (Packaging system)

2. Lots of drivers are missing, and are difficult or impossible to install.

3. Branded Zone with a copy of CentOS to run Linux software, instead of something nice like FreeBSD's Linuxulator.

---

### Post by DeadSuperHero on 2008-08-18
Dremora:

1. Should be alot better by 2008.11 release.

2. There's some actually pretty good documentation on how to install existing drivers, such as Nvidia or Marvell ones.

3. Most Linux software can be recompiled and re-packaged for Solaris.

---

### Post by Twitch6000 on 2008-08-18
> **Mr. Psychopath said:**
> It should work fine. If you need help, I can scour some of the OpenSolaris boards looking for any fixes you need.

If you want 3D working out of the box, I just hope your laptop either has an Intel or an Nvidia card in it. ATI is currently incompatible.

Basically everything in this laptop is Intel <.<.
Anyways I am download open solaris now and just one question,does it have a live cd mode,Or would I want to try it on a Virtual machine first?

---

### Post by smartboyathome on 2008-08-18
> **Twitch6000 said:**
> Basically everything in this laptop is Intel <.<.
Anyways I am download open solaris now and just one question,does it have a live cd mode,Or would I want to try it on a Virtual machine first?

It has a live CD mode, but imo it is a PITA to get it to work in Virtualbox. :(

---

### Post by Twitch6000 on 2008-08-18
> **smartboyathome said:**
> It has a live CD mode, but imo it is a PITA to get it to work in Virtualbox. :(

Well if it has a LiveCd mode that's all I need :).
Because after wine hits 1.2.0 I am almost 100% sure I can go full Linux.Then have Open Solaris as a dual boot >.>.
Unless ofcourse I get my new laptop before hand >.>.

Edit: 
Well just got through giving it a try and at first I was like is this ubuntu LOL.

Then I started to fool around with it alot and figured out how different they were.
All and all I can say when I don't need windows anymore open solaris will be my dual boot :).Until then I have it to fool around with and learn on.

---

### Post by Sorivenul on 2008-08-18
> **Twitch6000 said:**
> All and all I can say when I don't need windows anymore open solaris will be my dual boot :).Until then I have it to fool around with and learn on.
Feel free to learn on the LiveCD, but a HD install is the best.  And as far as anything I've tried, the stability of virtualization in OpenSolaris is awesome - That's where I have MY Windows installed.  Good luck!

---

