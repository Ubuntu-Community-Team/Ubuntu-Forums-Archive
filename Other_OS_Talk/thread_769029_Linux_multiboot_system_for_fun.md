---
title: "Linux multiboot system for fun"
date: 2008-04-26
forum: Other OS Talk
---

### Post by twin_57103 on 2008-04-26
Hi folks,

I have an old P3/500 MHz (not the one in my sig!) laying around that I'm wanting to use for an experiment.  I have a 20 Gb hard drive and I'd like to see how badly I can multiboot the thing (I may be able to scrounge up another, smaller hard drive, possibly adding another 10 Gb or so).  I've got 128 Mb RAM, and I'm working on getting it up to 256.

I've been using Ubuntu for about a year (I'm also a Windows power-user).  I've done some configuration and whatnot, but I'm no expert, and still learning CLI.  This project is to educate myself on some different Linux distros, but not tear out my hair in the process (not sure if I'm up to Arch yet, although I'd be willing to try...).

First, what distros would be good?  I'd like to look at an7y of the major ones that will run on this dinosaur and possibly a few smaller but lightweight options.  I've also been experimenting with live CDs for the heavier ones on my main rig (see sig), but I don't want to install anything more there.

Second, how should I partition it?  So far, I'm thinking 512 Mb /home and 256 Mb swap (may increase this if I can get more RAM), then separate partitions for the different distros.  With each distro, what's a good partition size (enough to comfortably use it, including adding programs, but keeping it small b/c of the limited HDD space)?

Thanks!
twin_57103

---

### Post by cardinals_fan on 2008-04-26
Zenwalk is the best.  FreeBSD is a ton of fun if you're willing to learn.

---

### Post by twin_57103 on 2008-04-26
Yes, they are on my list to try.  I tried to download FreeBSD but couldn't download the image from the web site; not sure what was going on there (tried multiple times, and my network connection is fine).  I got PC-BSD with no problems.  PC-BSD seems like it's just a desktop-customized variant on FreeBSD, so I figured I'd try it instead.  Otherwise, is there an alternate mirror I could use?

---

### Post by cardinals_fan on 2008-04-26
> **twin_57103 said:**
> Yes, they are on my list to try.  I tried to download FreeBSD but couldn't download the image from the web site; not sure what was going on there (tried multiple times, and my network connection is fine).  I got PC-BSD with no problems.  PC-BSD seems like it's just a desktop-customized variant on FreeBSD, so I figured I'd try it instead.  Otherwise, is there an alternate mirror I could use?
PC-BSD and DesktopBSD are both FreeBSD with KDE and GUI installers. [B]EDIT: See post below
[/B]
The FreeBSD images are working fine off the main mirror... [ftp://ftp.freebsd.org/pub/FreeBSD/releases/i386/ISO-IMAGES/7.0/](ftp://ftp.freebsd.org/pub/FreeBSD/releases/i386/ISO-IMAGES/7.0/)

---

### Post by DJiNN on 2008-04-26
I totally agree with cardinals_fan re: Zenwalk. Great distro, good fun to play with, really fast on older equipment & you'll learn a lot from it. 

As for how best to partition your system and what to install on it, the choices are kind of endless.  But i'll give you an example of one of my machines (I have four computers here & i multiboot on ALL of them, with the most OS's being about 5-6 on one machine).

I have a PIII, which i'm on now. It's a 1ghz Coppermine, with a 30 gig hard drive and about 780meg of PC133 RAM (Built it out of spare parts and i love it!) I use it to test loads of different distros & to learn as much as possible about Linux in the process. At the moment i'm heavily into Fluxbox, Conky, panels and a few other things. 

The drive is partitioned into about 6 partitions of varying size (all ext3) and ONE 1gb swap file right at the end, which i use for all the distros that i install. The average size of each partition is between 4-5 gig. I have [antiX]("http://antix.mepis.org/") permanently installed on hda6, but apart from that all the other distros are liable to change frequently. At the moment, the two that have stayed on the longest are antiX & TinyMe.  

Of course it's totally up to you, but (unless you just want to try it & see how it goes) i would stay away from anything too heavy or big on that machine. Stick to the smaller/lighter distros (such as Zenwalk, antiX, TinyMe, TinyFlux, Fluxbuntu, and many more) and maybe even try Xubuntu to see what it's like? But if you start to get too heavy (basically KDE or GNOME) then you'll really notice the difference in performance. Most of them will work, but they will be slow & tedious to use (at least that's what i've found).

When i install any OS, i just install the whole thing onto one partition (including /home) as chances are you'll change them fairly often, and there's no real need to have a separate /home (unless you specifically want one of course).  It also makes the whole thing easier when it comes to allocating a partition for a distro, and means you don't have to remember seperate /home partitions as well..... it can become hard work if you have a seperate / & home for say 4-5 distros. :)

Lastly, one thing i have done (on the advice from bodhi_zazen when i first got into Ubuntu/Linux) is to keep one DATA partition (name it whatever you like) that doesn't carry any distro, only data. Mine's about 6 gig, and i put on it anything that i want to keep when changing/deleting distros etc. Any stuff you may download, source packages, config files, aretwork, avatars etc..... whatever it is, it's all accessible from all the distros, and really can be a life saver.

Oh, and you may want to have a spare Live CD handy that you can use to update your grub files quickly and conveniently when your latest install has written over your MBR. I use the antiX one, because there's a System Config tool on there that just makes it quick & easy, but there are many that you can use.

Anyway, i've waffled for far too long, so hope this helps, have fun (& you will) and i look forward to hearing all about it.  :)

---

### Post by cardinals_fan on 2008-04-26
> **DJiNN said:**
> 
Lastly, one thing i have done (on the advice from bodhi_zazen when i first got into Ubuntu/Linux) is to keep one DATA partition (name it whatever you like) that doesn't carry any distro, only data. Mine's about 6 gig, and i put on it anything that i want to keep when changing/deleting distros etc. Any stuff you may download, source packages, config files, aretwork, avatars etc..... whatever it is, it's all accessible from all the distros, and really can be a life saver.

+1

---

### Post by DJiNN on 2008-04-26
One more thing, re partition size..... to give you an example, most of my installs come in at less than 2gb (Usually around the 1-1.5gb mark) for a light-medium distro, so anywhere between 3-4 gig is ample. That "Should" cope with pretty much most of the installs that you choose to do.

Regarding the Arch thing, give it a go..... it'll be entertaining, but make sure that you put aside FAR more time than you would for installing most other distros. Arch is a great learning curve, but it can be very time consuming for the beginner, especially when there are a few problems to get sorted. LOL!  The Arch forums & the Arch wiki are great places to get answers, and you won't believe the speed of Arch on that machine, especially if you use something like Fluxbox or Openbox..... even XFCE will be fairly snappy.

Oh, and get as much RAM as you can..... it always helps. :)

---

### Post by twin_57103 on 2008-04-27
Cool...thanks to everyone for the ideas.  I "borrowed" some more PC100 from a friend, so I should be able to get the thing up to 256 Mb (crossing my fingers - not sure if it's any good).

I tried Fluxbuntu and Zenwalk, but I think I made a mess of it, so I'll probably reformat the whole thing and start over (starting with Zenwalk this time).  I'm not having any luck sorting it out with Super Grub, either.  Thankfully, there's nothing to lose here, so I can make a mess of it and not mind :)

I also borrowed another hard drive, so I'll probably put that in for data and possibly an OS or two.  I'm not really doing this to use the thing so much as to learn (just built a speed-demon for my main computer).  I will probably give Arch a try after some playing with other distros, so long as I can do it and maintain my sanity.  I'd definitely learn a lot from the attempt.

I still got errors from the free BSD ftp (but thanks for the link!) - maybe it is something on my end (error 45), but other downloads work fine.  I'll just use the PC-BSD image that I've already got.

---

### Post by cardinals_fan on 2008-04-27
I really shouldn't post when I'm lazy and tired.  PC-BSD and DesktopBSD have a few differences that I should have mentioned.  DesktopBSD is essentially FreeBSD with a GUI included, while PC-BSD is a more independent OS.  The FreeBSD ports system probably won't work with PC-BSD (they advise that you stick with their PBI package management system).  DesktopBSD will work with FreeBSD ports using Portsnap.  In short, DesktopBSD provides a more 'pure' FreeBSD system, while PC-BSD is a separate system in most ways.

---

### Post by DJiNN on 2008-04-27
> **twin_57103 said:**
> Cool...thanks to everyone for the ideas.  I "borrowed" some more PC100 from a friend, so I should be able to get the thing up to 256 Mb (crossing my fingers - not sure if it's any good).

More ram makes a lot of difference. :)  256mb is good, more is a bonus! 

> I tried Fluxbuntu and Zenwalk, but I think I made a mess of it, so I'll probably reformat the whole thing and start over (starting with Zenwalk this time).  I'm not having any luck sorting it out with Super Grub, either.  Thankfully, there's nothing to lose here, so I can make a mess of it and not mindLOL.... that's the cool thing about having a machine to just "muck about on". :)  Regarding Zenwalk, it doesn't use grub, it uses lilo instead.  If you would like to use grub (and personally i prefer grub) then the easiest way to install Zenwalk is to just run the installer, then when you get to the part where it's going to install lilo, DON'T install it on the MBR, but put it on the root of the install drive. Then you can either edit your grub file by hand and add the appropriate lines for Zenwalk  to boot (see [here]("http://wiki.zenwalk.org/index.php?title=Installing_Zenwalk_when_you_already_have_another_OS_installed%2C_and_using_GRUB") for an outline) or, better still, make Zenwalk your first install and do the same with lilo, then install your 2nd OS on another partition (making sure it's an OS tha uses grub - most do) and the 2nd OS should pick up the Zenwalk partition and put it in the grub file "automagically".  It's not 100% perfect mind you, and you may still need to go in and edit your menu.lst (/boot/grub/menu.lst) by hand. Obviously this needs to be done as root. 

Also remember that everytime you install another OS, there's a good chance that it's going to install it's own grub, which will then become the default, and so on and so on. You can (with most distros although not all) put grub on the root of the install drive of each partition that you install, and then just use one main menu.lst & alter it by hand..... the choice is yours. It takes a bit of getting used to, and with the addition of UUID's now, that can really stuff up your multi installs.  I usually wipe the UUID's from the fstab and replace them with the relevant /dev line of the drive in question. 

It sounds more confusing than it is, and once you've done it a few times & got the hang, you'll be fine. :)

---

### Post by twin_57103 on 2008-04-27
> **DJiNN said:**
> 
Regarding Zenwalk, it doesn't use grub, it uses lilo instead.  If you would like to use grub (and personally i prefer grub) then the easiest way to install Zenwalk is to just run the installer, then when you get to the part where it's going to install lilo, DON'T install it on the MBR, but put it on the root of the install drive. Then you can either edit your grub file by hand and add the appropriate lines for Zenwalk  to boot (see [here]("http://wiki.zenwalk.org/index.php?title=Installing_Zenwalk_when_you_already_have_another_OS_installed%2C_and_using_GRUB") for an outline) or, better still, make Zenwalk your first install and do the same with lilo, then install your 2nd OS on another partition (making sure it's an OS tha uses grub - most do) and the 2nd OS should pick up the Zenwalk partition and put it in the grub file "automagically".  It's not 100% perfect mind you, and you may still need to go in and edit your menu.lst (/boot/grub/menu.lst) by hand. Obviously this needs to be done as root. 

Also remember that everytime you install another OS, there's a good chance that it's going to install it's own grub, which will then become the default, and so on and so on. You can (with most distros although not all) put grub on the root of the install drive of each partition that you install, and then just use one main menu.lst & alter it by hand..... the choice is yours. It takes a bit of getting used to, and with the addition of UUID's now, that can really stuff up your multi installs.  I usually wipe the UUID's from the fstab and replace them with the relevant /dev line of the drive in question. 

Clear as mud...but I'll play around with it.  I'm going to wipe the drive, then try Zenwalk first and see how that goes.  Thanks for the ideas!

---

### Post by twin_57103 on 2008-04-28
I got Zenwalk going, but only after installing Xubuntu.  Xubuntu got Grub installed and configured (I wasn't able to get it going with only Zenwalk installed - probably Grub & Lilo baggage left over from previous attempts).  I got three entries in the Grub menu for Zenwalk - not sure why it did that!  I'll keep going for more distros later.

I got it up to 320 Mb RAM and got a spare 20 Gb hard drive from a friend, so now I've got more space to work with :)

---

### Post by DJiNN on 2008-04-28
> **twin_57103 said:**
> I got Zenwalk going, but only after installing Xubuntu.  Xubuntu got Grub installed and configured (I wasn't able to get it going with only Zenwalk installed - probably Grub & Lilo baggage left over from previous attempts).  I got three entries in the Grub menu for Zenwalk - not sure why it did that!  I'll keep going for more distros later.

Yay!! Good stuff! :) 

Possibly it was baggage, or maybe because you either didn't have a working grub installed on the mbr?.... Or, maybe it was because you formatted the Zenwalk partition as xfs rather than ext3?  Whatever the reason, it's great that it's now up & running & you can start to play around with it.  Zenwalk (Slack) is so different to the Buntu's/Debian etc..... you'll have loads of fun! :)

> I got it up to 320 Mb RAM and got a spare 20 Gb hard drive from a friend, so now I've got more space to work with :)Great!! The more ram the better, and i think what you said earlier about having the "Data" drive on the 2nd partition is a good idea. Remember also (Just in case you don't already know) that you can only have up to 4 Primary partitions on any physical drive, and the "Extended" partition (Where you'll put the "Logical" drives) will take up one of those primary slots, so that leaves 3.  You can have the swap in an extended partition as well though, so that can help.

Have fun, and keep posting what you're up to. :)

---

### Post by twin_57103 on 2008-04-28
I'm still guessing baggage; I deleted the partitions when I started over, but didn't do anything to sort out the MBR.  I'm pretty sure I did ext3 for all the partitions (did it from GParted).  I got the main drive partitioned into 3 Gb chunks using extended partitions - that's something that's pretty new for me, too.  I've usually never done more than 2 partitions per drive.

I still want to see how many separate distros I can get going simultaneously, so I might see about using the second drive for 3 or 4 more...it's silly, but why not?!?  I'd like to try Fedora and openSuse, even though they will be heavy on this machine (because I'd like to see installed versions of them).  It does meet the minimum requirements (not by much!!).

Some day, if I get really ambitious, I'll do this with some of the heavier distros on a spare hard drive on my quad-core (pull the main drive so it doesn't interfere with my system)....... don't know if I'll ever get around to it, but it would be cool.

I have a few errands to run tonight, but I'm hoping to work on Knoppix and/or PC-BSD next.

---

### Post by DJiNN on 2008-04-29
> **twin_57103 said:**
> I'm still guessing baggage; I deleted the partitions when I started over, but didn't do anything to sort out the MBR.  I'm pretty sure I did ext3 for all the partitions (did it from GParted).

It could be, although Zenwalk (IIRC) defaults to xfs on the root drive. But whatever, it's great that you got it going. :)

>   I got the main drive partitioned into 3 Gb chunks using extended partitions - that's something that's pretty new for me, too.  I've usually never done more than 2 partitions per drive.

LOL!! It's great fun, but can get very confusing if you start using /home partitions as well. That's why, if you're just using it as a testing rig, it's better to just install each distro to just one partition. You could at some point get into sharing one home partition. It can be done, and the easiest way to do it would be to have different usernames for each distro. 

[/quote]I still want to see how many separate distros I can get going simultaneously, so I might see about using the second drive for 3 or 4 more...it's silly, but why not?!?  I'd like to try Fedora and openSuse, even though they will be heavy on this machine (because I'd like to see installed versions of them).  It does meet the minimum requirements (not by much!!).

Some day, if I get really ambitious, I'll do this with some of the heavier distros on a spare hard drive on my quad-core (pull the main drive so it doesn't interfere with my system)....... don't know if I'll ever get around to it, but it would be cool.

I have a few errands to run tonight, but I'm hoping to work on Knoppix and/or PC-BSD next.[/QUOTE]

I think it's great to try all those distros..... some will work, some will be great, some will be awful, but the whole thing will be great fun & a great learning curve. (Quite frustrating at times also though) LOL!

With regards to how many partitions, you can pretty much have as many as you want, as long as you observe the Primary rule of no more than 4. On my laptop at the moment, i have the following....

XP (Use it for music production etc) along with a 50gb FAT partition for storing stuff, then i also have (As logical partitions) 5x 4gb partitions and one 8gb partition, plus a 2gb swap. At the moment they're loaded with antiX, Sidux, Pud, Linux Mint, and the others are waiting to be loaded with whatever distro(s) i choose next..... But (apart from antiX) they all change regularly. Sometimes the whole Grub thing can get a bit scary, but it's a great way to learn. :)

On the P3 machine i also have (on 4gb partitions) TinyMe, Sidux, antiX and Xubuntu Hardy (Which is just about to be replaced by Arch with KDEmod because Xubuntu (Although a great distro) is just too bloated and slow). And of course i also have my data partition. :)

So go for it, and have as many as you feel comfortable with.... just watch out for those UUID's..... when you start changing stuff too much, especially the physical drive sizes (like re-sizing partitions & such) the distros that use UUID's will refuse to boot because the UUID's no longer match the drive(s) that they point too. Best to replace the UUID with /dev/sda?? etc, in the grub file.

Sounds like your having a blast though, which is cool! :guitar:

---

### Post by DJiNN on 2008-04-29
> **twin_57103 said:**
> I'm still guessing baggage; I deleted the partitions when I started over, but didn't do anything to sort out the MBR.  I'm pretty sure I did ext3 for all the partitions (did it from GParted).

It could be, although Zenwalk (IIRC) defaults to xfs on the root drive. But whatever, it's great that you got it going. :)

>   I got the main drive partitioned into 3 Gb chunks using extended partitions - that's something that's pretty new for me, too.  I've usually never done more than 2 partitions per drive.

LOL!! It's great fun, but can get very confusing if you start using /home partitions as well. That's why, if you're just using it as a testing rig, it's better to just install each distro to just one partition. You could at some point get into sharing one home partition. It can be done, and the easiest way to do it would be to have different usernames for each distro. 

> I still want to see how many separate distros I can get going simultaneously, so I might see about using the second drive for 3 or 4 more...it's silly, but why not?!?  I'd like to try Fedora and openSuse, even though they will be heavy on this machine (because I'd like to see installed versions of them).  It does meet the minimum requirements (not by much!!).

Some day, if I get really ambitious, I'll do this with some of the heavier distros on a spare hard drive on my quad-core (pull the main drive so it doesn't interfere with my system)....... don't know if I'll ever get around to it, but it would be cool.

I have a few errands to run tonight, but I'm hoping to work on Knoppix and/or PC-BSD next.

Haven't tried Knoppix for ages, but its a good distro. Watch out for BSD though, because it may wipe out your logical drives if you install it to a logical drive. So best to install onto an actual physical partition if poss. I went to install PC-BSD the othet night & decided not to do it (Mainly because it didn't seem to offer anything new or exciting) so i ended up installing Sidux instead..... Sidux is really nice.... complicated, because of all the things you have to do to get a dist-upgrade working, but well worth the effort, and it's REALLY FAST!! Possibly the fastest debiansystem (That uses KDE) i've ever tried so far. I didn't think i'd ever get a usable KDE working on this old P3, but Sidux has proved me sooo wrong! 

I think it's great to try all those distros though ..... some will work, some will be great, some will be awful, but the whole thing will be great fun & a great learning curve. (Quite frustrating at times also though) LOL!

With regards to how many partitions, you can pretty much have as many as you want, as long as you observe the Primary rule of no more than 4. On my laptop at the moment, i have the following....

XP (Use it for music production etc) along with a 50gb FAT partition for storing stuff, then i also have (As logical partitions) 5x 4gb partitions and one 8gb partition, plus a 2gb swap. At the moment they're loaded with antiX, Sidux, Pud, Linux Mint, and the others are waiting to be loaded with whatever distro(s) i choose next..... But (apart from antiX) they all change regularly. Sometimes the whole Grub thing can get a bit scary, but it's a great way to learn. :)

On the P3 machine i also have (on 4gb partitions) TinyMe, Sidux, antiX and Xubuntu Hardy (Which is just about to be replaced by Arch with KDEmod because Xubuntu (Although a great distro) is just too bloated and slow). And of course i also have my data partition. :)

So go for it, and have as many as you feel comfortable with.... just watch out for those UUID's..... when you start changing stuff too much, especially the physical drive sizes (like re-sizing partitions & such) the distros that use UUID's will refuse to boot because the UUID's no longer match the drive(s) that they point too. Best to replace the UUID with /dev/sda?? etc, in the grub file.

Sounds like your having a blast though, which is cool! :guitar:

Apologies for the length of the post.... i got a bit carried away! :-)

---

### Post by twin_57103 on 2008-04-29
I tried PC-BSD and Knoppix last night (got around to it after all).  Knoppix installed, but I may yet wipe it.  It installed its own, separate Grub file (got the original restored with Super Grub) and somehow I ended up with a password problem so that I couldn't even get into the thing!  A typo, I'm sure, but I'll probably leave that one as a live CD for now.  That's why I'm doing this :)

PC-BSD kept giving me errors about getty repeating too fast and never installed.  I eventually gave up.  I didn't even get to the point of picking an installation location.

I managed to download the entire stinking Fedora install DVD - started it yesterday when I got home and it finished sometime during the night.  3 Gb - yikes!  I'm glad this old clunker has a DVD-ROM!

---

### Post by DJiNN on 2008-04-29
> **twin_57103 said:**
> I tried PC-BSD and Knoppix last night (got around to it after all).  Knoppix installed, but I may yet wipe it.  It installed its own, separate Grub file (got the original restored with Super Grub) and somehow I ended up with a password problem so that I couldn't even get into the thing!  A typo, I'm sure, but I'll probably leave that one as a live CD for now.  That's why I'm doing this :) 

Heehee...... i had a similar problem with knoppix a while back.... i got it sussed eventually but can't remember how i did it! :)

> PC-BSD kept giving me errors about getty repeating too fast and never installed.  I eventually gave up.  I didn't even get to the point of picking an installation location.

Good choice. Maybe it's worth trying one of the other BSD's that's out there instead. Desktop-BSD is supposed to be quite good. 

> I managed to download the entire stinking Fedora install DVD - started it yesterday when I got home and it finished sometime during the night.  3 Gb - yikes!  I'm glad this old clunker has a DVD-ROM!

Heehee..... That's a pretty long install time eh?  I tried Fedora a few weeks ago, but wasn't that impressed with it. It was slick alright, and looked great, but looked like most other Gnome packages that i've seen. It ran well though, and is well put together.

I'm just playing with Sidux on this old P3, and i'm mightily impressed. It's incredibly fast! :)

---

### Post by twin_57103 on 2008-04-29
> **DJiNN said:**
> 
Heehee..... That's a pretty long install time eh?  I tried Fedora a few weeks ago, but wasn't that impressed with it. It was slick alright, and looked great, but looked like most other Gnome packages that i've seen. It ran well though, and is well put together.

That's just the *download*!!!  I haven't tried installing it yet - hopefully tonight.  Thankfully, this thing has a DVD-ROM - I don't have to mess with a multi-CD install.

> **DJiNN said:**
> 
I'm just playing with Sidux on this old P3, and i'm mightily impressed. It's incredibly fast! 
I'll download it and give it a try.

---

### Post by cardinals_fan on 2008-04-29
> **DJiNN said:**
> 
Good choice. Maybe it's worth trying one of the other BSD's that's out there instead. Desktop-BSD is supposed to be quite good. 
DesktopBSD is much better than PC-BSD (IMHO).  It stays closer to its FreeBSD roots.

---

### Post by cardinals_fan on 2008-04-29
> **twin_57103 said:**
> That's just the *download*!!!  I haven't tried installing it yet - hopefully tonight.  Thankfully, this thing has a DVD-ROM - I don't have to mess with a multi-CD install.
Uh, is there a reason you're using the DVD?  They have regular size CD iso's available... [http://fedoraproject.org/en/get-fedora](http://fedoraproject.org/en/get-fedora)

---

### Post by twin_57103 on 2008-04-29
I know you can install Fedora from the CD versions, but I figured I'd go for the regular installer.  I just left it running overnight - not a big deal, just slow.

I ended up with PC-BSD when I couldn't get the download to work for freeBSD - still haven't gotten anywhere with that.  I think I found a link that led me to it, and that's why I tried it.

I actually managed to borrow another computer from a friend - a 1.8 GHz something-or-other (I think it's a P4??), so I'll continue the "exploring Linux" saga there with some of the heavier distros that won't run on the P3.

I'll update when I manage to get somewhere with all of this!  Thanks for still reading!

---

### Post by twin_57103 on 2008-05-03
> **cardinals_fan said:**
> Uh, is there a reason you're using the DVD?  They have regular size CD iso's available... [http://fedoraproject.org/en/get-fedora](http://fedoraproject.org/en/get-fedora)

You were right, it was a bad idea.  I discovered that while this thing may have a DVD-ROM (the only optical drive), it won't boot from a DVD, only a CD.  I installed from the live CD (although later wiped it, see below).

I got so much going on that I couldn't sort out heads or tails (Xubuntu would only start after fsck errors, couldn't get at several of the installed distros, even with Super Grub, etc., at least one didn't see the network connection), so I started over.  I used DBAN (Darik's Boot & Nuke) to wipe both drives to get rid of the MBR baggage, then started with DesktopBSD (first time I've actually gotten it to boot, even though I installed it twice before :)).

I'll update once I get a little further - we'll see if I can make something that works this time!  Thanks for still reading!

---

### Post by cardinals_fan on 2008-05-03
> **twin_57103 said:**
>  then started with DesktopBSD (first time I've actually gotten it to boot, even though I installed it twice before :)).
Good luck, DesktopBSD is fun.

---

### Post by DJiNN on 2008-05-04
> **twin_57103 said:**
> 
I got so much going on that I couldn't sort out heads or tails (Xubuntu would only start after fsck errors, couldn't get at several of the installed distros, even with Super Grub, etc., at least one didn't see the network connection), so I started over. 

LOL!! That happens a lot when you're installing multiple distros with their own idea of how they should be set up etc. I used to get a lot of problems with fsck etc until i stopped using UUID's in the fstab of whatever distro i had just installed. I'm not saying that it's the reason for it, but it certainly helps to remove any reference to UUID & replace with the relevant /dev/sd? etc.

> I used DBAN (Darik's Boot & Nuke) to wipe both drives to get rid of the MBR baggage, then started with DesktopBSD (first time I've actually gotten it to boot, even though I installed it twice before :)).

I haven't tried DBAN yet, but i've just had a small laptop HD that won't boot anymore (Grub errors) and i think it's just MBR garbage, so i may give that a try and see what happens. Good news about your BSD install..... how are you finding it? 

> I'll update once I get a little further - we'll see if I can make something that works this time!  Thanks for still reading!

Thanks for still posting. :)  It's good to hear how you're doing.

---

### Post by twin_57103 on 2008-05-04
DBAN did a nice (if slow) job of getting rid of the MBR baggage.  
When I repartitioned it, I made sure no partition was the same size - it seems to make it easier to know which partition is which (based on drive size as well as sdx notation).

DesktopBSD is quite heavy on this machine (it only just meets the minimum specs) and it seems that the FreeBSD servers simply don't like me, because it just won't update or add packages (I had trouble downloading FreeBSD before - couldn't connect then, either).  That could be a real functionality-breaker - I'll have to stay with what's there by default unless the server starts working for me.

I might have to play with the UUID/fstab thing - right now I'm doing OK (got Xubuntu's GRUB edited to have the right entries), but once I get more on there it might get hairy again.  Planning to add Fedora (KDE) today and possibly a couple more; I'd like to try openSuse (KDE).  Beyond those, I'll go back to the lighter distros.

Thanks for reading and for the ideas!

---

### Post by DJiNN on 2008-05-04
> **twin_57103 said:**
> DBAN did a nice (if slow) job of getting rid of the MBR baggage.  
When I repartitioned it, I made sure no partition was the same size - it seems to make it easier to know which partition is which (based on drive size as well as sdx notation).

I was impressed with DBAN - slow but thorough, although ultimately the drive was trashed anyway and when i started to create some more partitions after i ran DBAN, it was slow & wouldn't create everything i asked for.... so i threw the drive!  :(  LOL!!

> DesktopBSD is quite heavy on this machine (it only just meets the minimum specs) and it seems that the FreeBSD servers simply don't like me, because it just won't update or add packages (I had trouble downloading FreeBSD before - couldn't connect then, either).  That could be a real functionality-breaker - I'll have to stay with what's there by default unless the server starts working for me.

Maybe there's just a problem with some of the servers?  But the good thing is at least you can go back & try again at a later date?  I'm still not sure what the attraction is for BSD (over Linux i mean) and that's the main drive for me to experience some BSD distros.  I just seem to find too many Linux distros that i'd rather install & try, so never seem to get around to putting BSD on any machine properly. :)

> I might have to play with the UUID/fstab thing - right now I'm doing OK (got Xubuntu's GRUB edited to have the right entries), but once I get more on there it might get hairy again.  Planning to add Fedora (KDE) today and possibly a couple more; I'd like to try openSuse (KDE).  Beyond those, I'll go back to the lighter distros.

Thanks for reading and for the ideas!

No probs..... i enjoy hearing how it's going & learn much in the process. :)  Nice one with the Xubuntu Grub. Xubuntu's one of my fave distros of them all.... just a shame that it's getting so heavy & bloated. Still an excellent distro though. 

OpenSuse is REALLY nice (In an eyecandy kinda way - & green is my favourite colour) but a bit heavy on this old P3. I downloaded the beta about a week ago but couldn't get it installed.... otherwise i would have tried that myself. I'll probably wait for a later release & try again. Let me know how you get on with it if you get a chance and a few screenshots would be real cool if you can. 

Oh, and you might want to have a look at Foresight Linux if you want to see a slick Gnome distro..... it's really nice.

---

### Post by cardinals_fan on 2008-05-04
> **twin_57103 said:**
> 
DesktopBSD is quite heavy on this machine (it only just meets the minimum specs) and it seems that the FreeBSD servers simply don't like me, because it just won't update or add packages (I had trouble downloading FreeBSD before - couldn't connect then, either).  That could be a real functionality-breaker - I'll have to stay with what's there by default unless the server starts working for me.
That's because it uses KDE by default.  I don't understand your server problems, because mine work fine.  Oh well.

> **twin_57103 said:**
> 
I might have to play with the UUID/fstab thing - right now I'm doing OK (got Xubuntu's GRUB edited to have the right entries), but once I get more on there it might get hairy again.  Planning to add Fedora (KDE) today and possibly a couple more; I'd like to try openSuse (KDE).  Beyond those, I'll go back to the lighter distros.

Fedora is a good distro.  One that you might be interested in is Draco Linux: [http://www.dracolinux.org/](http://www.dracolinux.org/).  It uses the Pkgsrc package/source system from NetBSD (which I currently use on DragonFlyBSD), and it offers both a preconfigured version with Xfce and Fluxbox and a 'pure' version with no GUI preinstalled.  This distro is currently #1 on my list of stuff to try, so let me know if you test it.

---

### Post by twin_57103 on 2008-05-04
Cardinals_fan, I wish I knew what was going on with the BSD servers, too -  I just can't connect!  Maybe it's something to do with my network hardware or ISP - who knows?

After installing Fedora, Xubuntu again gave me fsck errors.  I read somewhere that UUID's change after formatting a partition - so the errors make sense.  I removed the UUID's from fstab (uncommented the /media/sdx notation) and that has fixed the error.

I didn't let Fedora install its own GRUB, but now I'm having trouble adding it to Xubuntu's GRUB (with update-grub or by adding it manually).  I've tried to get it to boot in Super Grub without much luck.  I'll probably have to try the Fedora live CD and see if I can reinstall its GRUB (either that, or completely reinstall Fedora, including GRUB), but I haven't gotten that far - maybe later today.

---

### Post by cardinals_fan on 2008-05-04
Any reason you're keeping Xubuntu?

---

### Post by twin_57103 on 2008-05-04
> **cardinals_fan said:**
> Any reason you're keeping Xubuntu?

Familiarity, I guess (and the fact that I didn't care for Fluxbuntu).  My original goal was to get multiple distros going simultaneously, and it is nice to have something that I know a little better to use as a base.  I've still got plenty of partitions that are unoccupied, so it's not like I'm keeping it at the expense of something else.  It runs smoothly, other than the video resolution, which is still at 800x600 - I haven't yet taken time to fix it (other distros are running at 1280x1024, so it's just configuration).

Once I get to the point where I'm out of hard drive space for more distros, I'll probably consider canning Xubuntu, but for now, it's nice to have around.

There's no logical reason that I need Xubuntu's GRUB file - it's just where I started.  I thought I'd be able to add Fedora into it without too much hassle (it worked for DesktopBSD), but it seems I was wrong on that one!

---

### Post by twin_57103 on 2008-05-04
I reinstalled Fedora from the live CD, including allowing it to install GRUB.  I get the Fedora Grub entry by default, but it doesn't boot, just pauses after loading the kernel.

```
  Booting 'Fedora (2.6.23.1-42.fc8)'

root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.23.1-42.fc8 ro root=LABEL=/12 rhgb quiet
  [Linux=bzImage, setup=0x2c00, size=0x1e0320]
initrd /boot/initrd=2.6.23.1-42.fc8.img
  [Linux-initrd @ 0x2d16000, 0x2d73b8 bytes]
boot
Uncompressing Linux... Ok, booting the kernel.
Red Hat nash version 6.0.19 starting
```

From here, nothing happens.  I can access the partition from other OS's, but not boot it.  I got it pasted into Xubuntu's grub menu.lst - now I can get the same freeze-up from either grub :P (not especially helpful, but it means I don't need to swap files with Super Grub).  Any ideas?

---

### Post by cardinals_fan on 2008-05-04
You're just unlucky.  Nothing seems to work right for you.  Regardless, you can try reinstalling Fedora and see if it works then.

---

### Post by DJiNN on 2008-05-05
> **twin_57103 said:**
> I reinstalled Fedora from the live CD, including allowing it to install GRUB.  I get the Fedora Grub entry by default, but it doesn't boot, just pauses after loading the kernel.

```
  Booting 'Fedora (2.6.23.1-42.fc8)'

root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.23.1-42.fc8 ro root=LABEL=/12 rhgb quiet
  [Linux=bzImage, setup=0x2c00, size=0x1e0320]
initrd /boot/initrd=2.6.23.1-42.fc8.img
  [Linux-initrd @ 0x2d16000, 0x2d73b8 bytes]
boot
Uncompressing Linux... Ok, booting the kernel.
Red Hat nash version 6.0.19 starting
```From here, nothing happens.  I can access the partition from other OS's, but not boot it.  I got it pasted into Xubuntu's grub menu.lst - now I can get the same freeze-up from either grub :P (not especially helpful, but it means I don't need to swap files with Super Grub).  Any ideas?

Just a though, & i could be wrong, but it looks like Fedora is using the newer version of Grub (Grub 2). If that's the case, they're not cross compatible, and the settings that you would put into a normal grub install won't work in Grub 2.  This is only what i have found out from when i installed Foresight Linux, and it asked me if i wanted to use Grub (old style) or Grub 2. It may be worth checking. 

You can still get your grub back (from Xubuntu) anyway, by booting with the Xubuntu Live CD & either running grub in a terminal (Can't remember the exact commands offhand, but do a search on the Ubuntu forums & that should get what you need) or you can go [here]("http://users.bigpond.net.au/hermanzone/p15.htm") and have a look at Hermans Grub page. It's full of info about Grub and what to do in various situations. It's saved me a few times. :)  Not sure if it covers Grub 2 yet, but that doesn't really matter as you can use the normal grub to boot Fedora, and if you re-install Grub with the Live CD or what have you, it should pick up the Fedora install anyway.

Hope this helps.

---

### Post by twin_57103 on 2008-05-05
DNiNN,

Thanks for the constructive advice.  I don't care which file I end up using, but the installation doesn't boot either way (so far, I've gotten the same response whether I use Fedora's information pasted into Xubuntu's grub or whether I use Fedora's own file).  I can also switch between the files using Super Grub.  I'll try installing it to a different location (so far, I've tried reinstalling on the same partition) when I have time in case that helps.  I've seen Herman's page - thanks for the reminder.

---

### Post by DJiNN on 2008-05-05
> **twin_57103 said:**
> DNiNN,

Thanks for the constructive advice.  I don't care which file I end up using, but the installation doesn't boot either way (so far, I've gotten the same response whether I use Fedora's information pasted into Xubuntu's grub or whether I use Fedora's own file).  I can also switch between the files using Super Grub.  I'll try installing it to a different location (so far, I've tried reinstalling on the same partition) when I have time in case that helps.  I've seen Herman's page - thanks for the reminder.

I'm not 100% sure if i've got this correct, so please forgive me if i'm mistaken..... :)   copying & pasting from the Fedora Grub (if that's what you mean?) into the Xubuntu grub file, won't work at all, because Xubuntu uses the old (normal) style grub, and so needs the information formatted (written?) in the normal way. You'll have to write it yourself using the normal format.  So it'll be something like......

```

**[FONT=courier new,courier,monospace][COLOR=#0000ff]title Fedora (2.6.23.1-49.fc8)[/COLOR][/FONT]**[INDENT][COLOR=#0000ff]**[FONT=courier new,courier,monospace]        root (hd0,1)[/FONT]**
**[FONT=courier new,courier,monospace]        kernel /vmlinuz-2.6.23.1-49.fc8 ro root=/dev/main/root rhgb quiet[/FONT]**
**[FONT=courier new,courier,monospace]        initrd /initrd-2.6.23.1-49.fc8.img[/FONT]**[/COLOR][/INDENT][COLOR=#0000ff]**[FONT=courier new,courier,monospace]title Fedora (2.6.23.1-42.fc8)[/FONT]**[/COLOR]
[INDENT][COLOR=#0000ff]**[FONT=courier new,courier,monospace]        root (hd0,1)[/FONT]**
**[FONT=courier new,courier,monospace]        kernel /vmlinuz-2.6.23.1-42.fc8 ro root=/dev/main/root rhgb quiet[/FONT]**
**[FONT=courier new,courier,monospace]        initrd /initrd-2.6.23.1-42.fc8.img[/FONT]**[/COLOR][/INDENT]
```



Obviously changing the root=/  to whatever drive it's on, and also changing the kernel images to whatever you're currently using. Oh, and the grub - root (hd0,1) to whatever device/partition you're using as well. It's worth a try if you've not already done so. :)

---

### Post by DJiNN on 2008-05-05
> **cardinals_fan said:**
> 
Fedora is a good distro.  One that you might be interested in is Draco Linux: [http://www.dracolinux.org/](http://www.dracolinux.org/).  It uses the Pkgsrc package/source system from NetBSD (which I currently use on DragonFlyBSD), and it offers both a preconfigured version with Xfce and Fluxbox and a 'pure' version with no GUI preinstalled.  This distro is currently #1 on my list of stuff to try, so let me know if you test it.

Draco sounds interesting, i think i'll give that a try soon.  I've noticed from your sig, that you're using Dragonfly BSD.  Any chance of a screenshot or two? And what do you think of it overall?   It's quite a small distro isn't it? Does it come with any DE or is it purely Non GUI?  I was thinking that it may be worth trying out.

Any info would be great. :)

Thanks....

DJiNN

---

### Post by twin_57103 on 2008-05-05
I think I may need to give up on Fedora, at least on this machine.  I reinstalled it a couple times, trying both hard drives and leaving the bootloader configurations at default.  Oh, well - on to something else.  I think I'll try openSuse next.

---

### Post by DJiNN on 2008-05-05
> **twin_57103 said:**
> I think I may need to give up on Fedora, at least on this machine.  I reinstalled it a couple times, trying both hard drives and leaving the bootloader configurations at default.  Oh, well - on to something else.  I think I'll try openSuse next.

Sorry to hear about your Fedora probs..... but i think you'll like Suse. :) One day i'm going to install a minimal SUse (well, as minimal as i can get) along with Flux/Openbox, just to see what it runs like. :)

---

### Post by cardinals_fan on 2008-05-05
> **DJiNN said:**
> Draco sounds interesting, i think i'll give that a try soon.  I've noticed from your sig, that you're using Dragonfly BSD.  Any chance of a screenshot or two? And what do you think of it overall?   It's quite a small distro isn't it? Does it come with any DE or is it purely Non GUI?  I was thinking that it may be worth trying out.

Any info would be great. :)

Thanks....

DJiNN
DragonFly is a lot of fun to play with, and I recommend it... but not for use as a real desktop.  It includes no GUI by default.  In most ways, DragonFly was good (great installer), but their package management is messed up.  They use NetBSD's pkgsrc (which is also great), but their repos are a bit odd.  They don't have all the Xorg packages that they should, and some other things are missing compared to the NetBSD repos.  In all, DragonFly has a lot of potential, but I'll stick with NetBSD until they fix a few things.  No screenshots because I never made it to X.  The aforementioned Xorg packages didn't work, and if I can get Xfree86 by default from NetBSD, why should I use DragonFly?

BTW, like the new sig? :)  I've finally found a 'home' with NetBSD.  This is one to try.

For twin_57103: I recommend downloading a small Puppy iso.  The Puppy GRUB installer is great, and it'll fix your GRUB if anything will. Note that you don't need to install Puppy; just use the GRUB app.

---

### Post by DJiNN on 2008-05-06
> **cardinals_fan said:**
> DragonFly is a lot of fun to play with, and I recommend it... but not for use as a real desktop.  It includes no GUI by default.  In most ways, DragonFly was good (great installer), but their package management is messed up.  They use NetBSD's pkgsrc (which is also great), but their repos are a bit odd.  They don't have all the Xorg packages that they should, and some other things are missing compared to the NetBSD repos.  In all, DragonFly has a lot of potential, but I'll stick with NetBSD until they fix a few things.  No screenshots because I never made it to X.  The aforementioned Xorg packages didn't work, and if I can get Xfree86 by default from NetBSD, why should I use DragonFly?

Hmmm, that's a shame. 

I agree though, if it's not 100% or somewhere near, then better to find something else that is. I was under the impression that NetBSD was quite a difficult system to get going as well. (Mainly from most of the reviews that i've read). Is it as friendly as DesktopBSD or PC-BSD do you think?  

> BTW, like the new sig? :)  I've finally found a 'home' with NetBSD.  This is one to try.

Heehee...... but for how long? :)  You've peaked my interest though, so i'm gonna have to give NetBSD a look.  Maybe after i've given the new Solaris a try.... it does look interesting, and even more so because of Ian Murdock's involvement. :)

> For twin_57103: I recommend downloading a small Puppy iso.  The Puppy GRUB installer is great, and it'll fix your GRUB if anything will. Note that you don't need to install Puppy; just use the GRUB app.


+1 for Puppy. Just downloaded the latest (v4) and it's the best yet by far. It's a great disk to have around because it does so much..... some of the tools are fantastic. :guitar:

---

### Post by cardinals_fan on 2008-05-06
> **DJiNN said:**
> Hmmm, that's a shame. 

I agree though, if it's not 100% or somewhere near, then better to find something else that is. I was under the impression that NetBSD was quite a difficult system to get going as well. (Mainly from most of the reviews that i've read). Is it as friendly as DesktopBSD or PC-BSD do you think?  
NetBSD isn't that hard (easier than DragonFly, for instance).  You should be prepared to spend some time on it though, as with any minimal OS.  PC- and DesktopBSD are obviously easier to set up, because they include a graphical environment by default.  With NetBSD you have to set that up yourself (it includes some Xfree86 libraries which you choose whether to install - I'm going to try using these instead of downloading Xorg to see how well they work).  If you prefer to use Xorg, there are good packages in the NetBSD repos.  The NetBSD Guide is **excellent**.

> **DJiNN said:**
> 
Heehee...... but for how long? :)  You've peaked my interest though, so i'm gonna have to give NetBSD a look.  Maybe after i've given the new Solaris a try.... it does look interesting, and even more so because of Ian Murdock's involvement. :)

I wonder if this is 'the one'.  I really like how things are working on NetBSD, but we'll see how everything comes out...

---

### Post by twin_57103 on 2008-05-06
> **cardinals_fan said:**
> For twin_57103: I recommend downloading a small Puppy iso.  The Puppy GRUB installer is great, and it'll fix your GRUB if anything will. Note that you don't need to install Puppy; just use the GRUB app.

Good to know.  I've got a copy of Puppy (probably an older one - I'll download the newest), just haven't gotten to it on this machine.  I'll have to give it a try.  I'd tried to use it before for some file recovery, but ended using Knoppix instead.

I've also been impressed by openSuse's bootloader and configuration utility.  It handles the other OS's grub menus as submenus of its own and there's a GUI for configuring the whole mess.  I'm working on putting it all together in one - haven't gotten everything to work yet.  I can get everything save Fedora to boot, just not in one menu.

---

### Post by cardinals_fan on 2008-05-06
> **twin_57103 said:**
> Good to know.  I've got a copy of Puppy (probably an older one - I'll download the newest), just haven't gotten to it on this machine.  I'll have to give it a try.  I'd tried to use it before for some file recovery, but ended using Knoppix instead.

The old ones work well - I'm still using 2.6.1 :)

---

### Post by JawsThemeSwimming428 on 2008-05-06
Not sure if it was mentioned yet or not but I would try antiX for sure. It is amazingly fast and functional. I recently tried out Arch and although I think I like Debian based distros more Arch was amazing ( I think my decision about Arch vs. Debian is biased because I have only ever really liked Debian base distros, till Arch).

---

### Post by twin_57103 on 2008-05-06
I've got a CD burned for AntiX, but I haven't tried it yet.  I did put Tiny Me on it before I wiped the whole thing.  I'll try AntiX as soon as I have a chance.  Arch is also on my list of things to try.  Thanks for the ideas!

---

### Post by gnumd on 2008-05-06
This is a cool thread!

I have a lot to learn myself and am quite a noob.
I love my 8g eeePC because "theoretically" I should be able to install GNU/LINUX distros on multiple 8gig SDHCs and just pop-in the I want to play with, reboot and select to boot off the SDHC and have no problems.  So much for that theory.  

I am having an assortment of issues.
So far I was only able for a brief time to run WinXP off an SDHC (not recommended b/c it's slow) that does still work however, but the cool part was I could eject that SDHC and put in another one - I had a working SDHC running Ubuntu 7.10 (had to be tweaked a bit for internet access and display issues - would still be a work in progress but I bricked my ability to boot into it by trying out gnewsense on an external USB HDD).

My internal SSD (8gig) has a /home partition (for ubuntu and this has many files & settings that I don't want to lose), it also has a 128mb boot partition (probably way too big).

I tried reinstalling Ubuntu with the /home on the SSD and the boot and root on the SDHC but no joy.
Wondering if I can just install everything including home on the SDHC and somehow successfully link that install to the existing /home that is on the SSD??  I imagine it is possible. 

So my more general questions for those experienced with multibooting:
Should the SSD have a /boot partition that is shared with all the distro's where I'll install a GRUB that I'll tweak somehow (ie. after every additional install)?  I was hoping to just bypass using grub altogether and boot right off each SDHC but that doesn't seem to work for some reason.

Should I be putting my /home on my SSD for any of the distros? (I'd like to learn how to copy or image the /home to prevent too much loss of information when I inevitably mess up and get stuck) for now I'm a little glad it is separate, because I don't trust my terminal command abilities for moving it, copying it and back-up/restore.

When you make that data partition mentioned earlier- do you flag it as anything or just format a large partion as ext3 and leave it alone?

Sorry for the rather basic and noob questions, hopefully they are useful to everyone.  I'm stuck and frustrated and timid to mess around with GRUB editing - do you recommend a place to read on how to sort out all these sda, sdb, sdc, numbers and the hd0 etc formats that are used.  I think if I get through this tough spot I'll get much more fun out of the eeePC and start trying more distros (and tweaks for getting the hardware to work).

RE: Puppy Linux/Grub/SuperGrub... I was wondering if there was a way to make a liveCD with a small linux that can permit fixing the GRUB and getting to the internet (ie. like the Ubuntu Live CD but with my needed eeePC tweaks?).

Thanks.

~gnumd~

---

### Post by twin_57103 on 2008-05-07
Welcome!

> **gnumd said:**
> I have a lot to learn myself and am quite a noob.

So do I!  I've been using Linux for about a year now, and this old computer was an excuse to get further in depth with it.

> **gnumd said:**
> I love my 8g eeePC because "theoretically" I should be able to install GNU/LINUX distros on multiple 8gig SDHCs and just pop-in the I want to play with, reboot and select to boot off the SDHC and have no problems.  So much for that theory.  

I am having an assortment of issues.
So far I was only able for a brief time to run WinXP off an SDHC (not recommended b/c it's slow) that does still work however, but the cool part was I could eject that SDHC and put in another one - I had a working SDHC running Ubuntu 7.10 (had to be tweaked a bit for internet access and display issues - would still be a work in progress but I bricked my ability to boot into it by trying out gnewsense on an external USB HDD).

My internal SSD (8gig) has a /home partition (for ubuntu and this has many files & settings that I don't want to lose), it also has a 128mb boot partition (probably way too big).

I tried reinstalling Ubuntu with the /home on the SSD and the boot and root on the SDHC but no joy.
Wondering if I can just install everything including home on the SDHC and somehow successfully link that install to the existing /home that is on the SSD??  I imagine it is possible. 

I've seen mention of this (using a separate /home partition) on internet, so I know it can be done, but I don't remember where to find it...:(
> **gnumd said:**
> 
So my more general questions for those experienced with multibooting:
Should the SSD have a /boot partition that is shared with all the distro's where I'll install a GRUB that I'll tweak somehow (ie. after every additional install)?  I was hoping to just bypass using grub altogether and boot right off each SDHC but that doesn't seem to work for some reason.

That's a bummer - I'd figure that you'd be able to boot each separate card just like swapping a hard drive.

> **gnumd said:**
> 
Should I be putting my /home on my SSD for any of the distros? (I'd like to learn how to copy or image the /home to prevent too much loss of information when I inevitably mess up and get stuck) for now I'm a little glad it is separate, because I don't trust my terminal command abilities for moving it, copying it and back-up/restore.

When you make that data partition mentioned earlier- do you flag it as anything or just format a large partion as ext3 and leave it alone?

Sorry for the rather basic and noob questions, hopefully they are useful to everyone.  I'm stuck and frustrated and timid to mess around with GRUB editing - do you recommend a place to read on how to sort out all these sda, sdb, sdc, numbers and the hd0 etc formats that are used.  I think if I get through this tough spot I'll get much more fun out of the eeePC and start trying more distros (and tweaks for getting the hardware to work).

I don't have enough experience to tackle most of this - I'm hoping other readers of this thread can help.  It sounds like you ought to be able to keep each system independent on its own drive/data card, but that these aren't booting like they ought.

The data partition I'm using is just a separate ext3 partition (right now, I have several empty ext3 partitions, planning on putting more distros in them).  The /home folder contains some configuration and whatnot, but if you're after a place to store files, any partition/drive should do.  I'm following the advice I've gotten on this thread - keep /home within the distro rather than on a separate partition.  You can always backup/copy your /home folder through nautilus or other file manager if you'd rather not use the command line.

I don't know any web sites to help with the hard drive notation, but here's the nutshell version: (hd0,x) refers to the first hard drive - the numbering starts from 0, like many things in computing.  x is the partition number, again starting from 0.  (hd0,0) is the first partition on the first drive; hd(0,2) is the third partition on the first drive, and (hd1,1) is the second partition on the second drive.  sdx and hdx are a different/parallel way of referring to the drives (and more common).  sdx is for SCSI/SATA drives and hdx is for standard IDE drives.  x can be a, b, c, etc. for each drive.  hda1 is the first partition on the first drive, hdb2 is the second partition on the second drive, etc.

> **gnumd said:**
> RE: Puppy Linux/Grub/SuperGrub... I was wondering if there was a way to make a liveCD with a small linux that can permit fixing the GRUB and getting to the internet (ie. like the Ubuntu Live CD but with my needed eeePC tweaks?).
I know you can do this on a flash drive - [persistent desktop]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").  The SDHC cards should be comparable - they're both bootable, removable media, but again, that's back to an installation, rather than configuring a live CD.

Sorry I can't be of much help - hopefully some of the other posters on this thread can chime in.

---

### Post by DJiNN on 2008-05-07
> **cardinals_fan said:**
> NetBSD isn't that hard (easier than DragonFly, for instance).  You should be prepared to spend some time on it though, as with any minimal OS.  PC- and DesktopBSD are obviously easier to set up, because they include a graphical environment by default.  With NetBSD you have to set that up yourself (it includes some Xfree86 libraries which you choose whether to install - I'm going to try using these instead of downloading Xorg to see how well they work).  If you prefer to use Xorg, there are good packages in the NetBSD repos.  The NetBSD Guide is **excellent**.


I wonder if this is 'the one'.  I really like how things are working on NetBSD, but we'll see how everything comes out...

That sounds really interesting. I like minimal install OS's and i would guess that something like fluxbox or openbox would work quite well on NetBSD?  As long as the guide is good (which you say it is) then it shouldn't be too much of a problem getting Xorg working etc. 

Thanks for the info...... i'll D/L & give it a go today. :)

---

### Post by DJiNN on 2008-05-07
> **gnumd said:**
> 
RE: Puppy Linux/Grub/SuperGrub... I was wondering if there was a way to make a liveCD with a small linux that can permit fixing the GRUB and getting to the internet (ie. like the Ubuntu Live CD but with my needed eeePC tweaks?).

Thanks.

~gnumd~

Hi gnumd. 

I don't know much about the eeePC (Although i'm working towards getting one asap) but there are quite a few things that you could use to do what you're after. A very straightfoward way to do it would be to download the [antiX]("http://www.antix.mepis.org") Live CD and boot with that. It already has a Grub repair utility built into it, as part of the system admin. (See screenshot below)

[[IMG]http://img180.imageshack.us/img180/4651/200805071440x900lj0.th.jpg[/IMG]]("http://img180.imageshack.us/my.php?image=200805071440x900lj0.jpg")
antiX Grub repair utility.

You can also "Make your own" really easily, by installing something like [TinyMe]("http://www.tinyme.mypclinuxos.com") then changing the installed system to do what you'd like (by adding or removing whatever apps you require) then "remastering" your install into your very own "Live CD". Works a treat!!

There are of course many other tiny Live CD's that you can either just use as they are, or customise & create your own, but it doesn't get any easier than the antiX way. :)  Oh, and not forgetting of course, the fabulous ZenLive CD which also has the ability to make a Custom Live CD.

Too many choices! :lolflag:

---

### Post by DJiNN on 2008-05-07
> **gnumd said:**
> This is a cool thread!

I have a lot to learn myself and am quite a noob.
I love my 8g eeePC because "theoretically" I should be able to install GNU/LINUX distros on multiple 8gig SDHCs and just pop-in the I want to play with, reboot and select to boot off the SDHC and have no problems.  So much for that theory.  

I was just thinking about the different questions that you're asking, and a couple of things came to mind that are worth checking out. These are only guesses at what could help in resolving your problems and may or may not work. :)

WIth regards to booting from different SDHC's, can't see any reason why that wouldn't work, as long as each distros fstab points to the correct devices/dirs etc. May be worth checking each fstab of your distros just to see what they're saying. 

With regards to the booting getting screwed after you'd tried gnewsense on a USB portable, i can't see why this should cause problems, apart from maybe something changing in the BIOS that points to what the default boot device is.  For instance, on one of my machines here, if i plug in a USB stick and re-boot, it comes up with a message saying the "default boot device" has changed & what would i like to do.  Have you checked the BIOS to see if anything's changed at all? 

> 
Wondering if I can just install everything including home on the SDHC and somehow successfully link that install to the existing /home that is on the SSD??  I imagine it is possible.

Why not just install whatever distro you choose, onto the SDHC, then just mount the /home on the SSD manually to wherever you want it? Once you have it working you can then add the relevant line to fstab to do it automatically when you boot?

> So my more general questions for those experienced with multibooting:
Should the SSD have a /boot partition that is shared with all the distro's where I'll install a GRUB that I'll tweak somehow (ie. after every additional install)?  I was hoping to just bypass using grub altogether and boot right off each SDHC but that doesn't seem to work for some reason.  

Hmmm, that last one would be what i would have chosen.... just install the whole thing to a formatted (EXT3) SDHC and boot into it whenever you want. I'm surprised that it doesn't work, but then i don't know how the eeePC works with regards to the devices that it reads from (ie: internal SSD & extrenal SDHC's etc)    Once again, i find myself thinking that there may be something that you can set/change in the BIOS with regards to booting from an external device. 

> Should I be putting my /home on my SSD for any of the distros? (I'd like to learn how to copy or image the /home to prevent too much loss of information when I inevitably mess up and get stuck) for now I'm a little glad it is separate, because I don't trust my terminal command abilities for moving it, copying it and back-up/restore.

You can pretty much put your home wherever you like, as long as the device names are the same whenever you boot with the distro that relates to your /home partition. Remember, although you can share your /home "Partition" if you like, you have to have different usernames for each distro if you do. Otherwise, whenever you install/boot another distro with the same /home and/or username, it'll all start to go screwy & probably won't boot properly, if at all.  It's not a good idea to share the /home dir at all unless you know what you're doing.  

If it were me doing it, i'd get a distro working on the internall SSD first, then try and install another on an external SDHC and go from there. 

> When you make that data partition mentioned earlier- do you flag it as anything or just format a large partion as ext3 and leave it alone?

You format as ext3 (or whatever you choose) then add it to the fstab of each distro that you boot from. 

> Sorry for the rather basic and noob questions, hopefully they are useful to everyone.  I'm stuck and frustrated and timid to mess around with GRUB editing - do you recommend a place to read on how to sort out all these sda, sdb, sdc, numbers and the hd0 etc formats that are used.  I think if I get through this tough spot I'll get much more fun out of the eeePC and start trying more distros (and tweaks for getting the hardware to work).

We all have to start somewhere, and there's really no end to what people learn as it's kind of "Ever changing", so in a way we're all beginners! :)  As for learning more about Grub etc, try the [HermanZone]("http://users.bigpond.net.au/hermanzone/p15.htm"), and also [here]("http://www.dedoimedo.com/computers/grub.html") is a really good tutorial on Grub (With some other really useful tips).  Whatever you want to read about, do a Google search or search in these forums & you're bound to get some good stuff. To get you started [Here's a guide]("http://linuxplanet.com/linuxplanet/tutorials/4232/1/") on how hard drives are named/designated etc in Linux. Have a read and then go from there. :)

---

### Post by gnumd on 2008-05-07
Thanks guys!

I'll read up about the hard drive handling in GNU/LINUX.  I reinstalled Ubuntu to the SDHC a couple times now - experimenting.

So far I've gotten GRUB errors such as 71 or was it 17, 15 and 21.  I am bad about remembering and should have written things down - I was always thinking it was going to work and didn't.

The last install I was sure would work.  I think I know what is happening now and it may be related to the last step in the Ubuntu installer - where one can click advanced.  A dialogue appears that offers the option to uncheck installing the boot loader (grub apparently) and also has by default the (hd0,0).  So I had the USB HDD connected and I believe that is getting called (or was called at that time anyway) hd0.  So I took my eeePC with me to work today thinking it was going to work - that is when I encountered the grub 21 error (I may be mistaken about the code though).  I didn't have the external drive because I expected to not need it because I didn't realize that the Grub may have been put onto it instead of the internal SSD which I thought was usually the HD0,0.  When I got home I rebooted with the external USB attached and the install on the SDHC worked.  So I think it put Grub on that device instead of on the boot partition on my internal SSD.  IF it had put it on the internal SSD then the SDHC should have booted.  Similarly the same thing must have occurred when I thought I was putting the boot onto the SDHC.  SO if I can figure out what the SDHC is called and what code to put in this advanced option then the install should all go to the card and the card should work whenever I tell the eeePC to boot from it.

Interesting...  When I installed the entire Ubuntu onto the SDHC I wonder if that setting was wrong, because grub wouldn't work at that time either - I think that was an error 71 or 15, I can't remember sorry.

I'm going to read up about these names and fstab and figure out what code to put into that advanced setting and reinstall to the SDHC - hopefully it will really put the boot on that card and then it will work every time regardless of other installations - if it actually reads that card first and not somewhere else!

I'll keep you posted.  This situation is slowly teaching me a lot about booting.  Like I said before, figuring out booting will permit a lot of further experimentation.  

I do like the idea of putting an installation on the internal SSD - and I may turn to that as a solution as well.  Initially I was concerned about space but really the space would then become unlimited by using external SDHC cards as data sticks for storage of any data versus code that would be stored on the SSD.  I'd like to not have to carry around the external HDD for space and primarily use that device at home when necessary for system back-ups.

Infact if I can figure out how to reliably copy the present /home partition to a CDROM or DVD then I'll just erase and install Ubuntu on the SSD tonight and use the SDHCs for other distros that I may experiment with.

This is long sorry.  But in failure one finds small breakthroughs.:)

~gnumd~

---

### Post by twin_57103 on 2008-05-07
> **gnumd said:**
> Thanks guys!I'll keep you posted.  This situation is slowly teaching me a lot about booting.  Like I said before, figuring out booting will permit a lot of further experimentation.  
Glad to hear it - that's much of what I'm doing with this old P3, too.

> **gnumd said:**
> Infact if I can figure out how to reliably copy the present /home partition to a CDROM or DVD then I'll just erase and install Ubuntu on the SSD tonight and use the SDHCs for other distros that I may experiment with.

If nothing else, you can always boot a live CD and use Brasero (or other CD-burning software) to burn to a CD.  You could also copy to the USB drive using Nautilius (or other file manager).

I'd recommend completely wiping the drive - I did this when I started over and it helped to remove some of the MBR baggage.  [Darik's boot & nuke]("http://dban.sourceforge.net/") should work for this - just be very sure you've backed up everything you need first!  (I'm not 100% sure if it's compatible with solid-state drives/cards - can someone else confirm this?)  That way, when you start over, you won't have anything in the MBR to confuse the new install.

I don't think there's any need for a separate /boot partition.  After a thorough wipe, you may be able to stick with the original plan of using the SDHC cards in lieu of a hard drive and using the internal SSD as a data area.  If so, don't let them install any bootloader to the internal SSD - keep it on the individual cards.

In any case, let us know how it works out!

---

### Post by cardinals_fan on 2008-05-07
> **DJiNN said:**
> That sounds really interesting. I like minimal install OS's and i would guess that something like fluxbox or openbox would work quite well on NetBSD?  As long as the guide is good (which you say it is) then it shouldn't be too much of a problem getting Xorg working etc. 

Thanks for the info...... i'll D/L & give it a go today. :)
I use Openbox, and it worked well on my former NetBSD install with Xorg.  It'll be really interesting to check out XFree86 though, so I'll let you know how it comes out (could be two weeks or so, since I'm thinking about waiting till the end of school).

You'll want to check out the wiki page on getting Xorg working at [http://wiki.netbsd.se/How_to_install_modular_Xorg](http://wiki.netbsd.se/How_to_install_modular_Xorg).  Also look at the wondrous NetBSD Guide at [http://www.netbsd.org/docs/guide/en/index.html](http://www.netbsd.org/docs/guide/en/index.html).

---

### Post by DJiNN on 2008-05-07
> **cardinals_fan said:**
> I use Openbox, and it worked well on my former NetBSD install with Xorg.  

Great stuff, if it works with Openbox then it'll almost certainly work with Fluxbox as well (I love both, but i'm far more at home with Flux.) :)

> It'll be really interesting to check out XFree86 though, so I'll let you know how it comes out (could be two weeks or so, since I'm thinking about waiting till the end of school).

Hmmm, i used Xfree86 a few weeks ago on an Arch install. It worked well there so i can't see any reason why it shouldn't work on NetBSD?  It's a lot smaller & more straightforward than Xorg isn't it?

> You'll want to check out the wiki page on getting Xorg working at [http://wiki.netbsd.se/How_to_install_modular_Xorg](http://wiki.netbsd.se/How_to_install_modular_Xorg).  Also look at the wondrous NetBSD Guide at [http://www.netbsd.org/docs/guide/en/index.html](http://www.netbsd.org/docs/guide/en/index.html).

OK, that's great..... thanks for the links. I'll give that a go in the next few days & see how it performs. Should be interesting to say the least. LOL!  Thanks for the info.

---

### Post by cardinals_fan on 2008-05-07
> **DJiNN said:**
> 
Hmmm, i used Xfree86 a few weeks ago on an Arch install. It worked well there so i can't see any reason why it shouldn't work on NetBSD?  It's a lot smaller & more straightforward than Xorg isn't it?

NetBSD actually includes some [optional] XFree86 packages on the install disk, so it'll be really easy to set up NetBSD boxes from now on if this works.

---

### Post by twin_57103 on 2008-05-11
Well, the download difficulties are definitely related to something in my network connection.  I'm visiting family this weekend and downloaded freeBSD without glitches - and lightning speed (they've got cable internet, I have DSL).  I don't think I'll bother installing it since I've already got DesktopBSD running, but it's nice to know where the problems are coming from.

I have a friend who wants to get something running on a 200 MHz laptop with no CD-ROM.  It doesn't need to be fast, but it does need to be reasonably user-friendly for the end-user.  My first idea (before he mentioned the lack of a CD-ROM) was Zenwalk - I've really liked it.  My ideas were a network install or putting the hard drive in a different computer and installing, then moving it back to the intended machine.  Any ideas?  I can always post it as a separate thread, but I thought I'd mention it here first.

---

### Post by DJiNN on 2008-05-11
> **twin_57103 said:**
> 
I have a friend who wants to get something running on a 200 MHz laptop with no CD-ROM.  It doesn't need to be fast, but it does need to be reasonably user-friendly for the end-user.  My first idea (before he mentioned the lack of a CD-ROM) was Zenwalk - I've really liked it.  My ideas were a network install or putting the hard drive in a different computer and installing, then moving it back to the intended machine.  Any ideas?  I can always post it as a separate thread, but I thought I'd mention it here first.


Good to hear it's all going well :)

As for the laptop, 200mhz is quite slow & it also depends on how much ram. If it's quite an old laptop i'd try something like Puppy first. (New version is out & it's great).  Zenwalk's good, but it does have its limits, especially on really old machines with limited ram. You can also (fairly quickly) install Puppy onto a usb stick (if the laptop has usb that is?) and then boot from the stick and install from there?

---

### Post by twin_57103 on 2008-05-11
> **DJiNN said:**
> Good to hear it's all going well :)

As for the laptop, 200mhz is quite slow & it also depends on how much ram. If it's quite an old laptop i'd try something like Puppy first. (New version is out & it's great).  Zenwalk's good, but it does have its limits, especially on really old machines with limited ram. You can also (fairly quickly) install Puppy onto a usb stick (if the laptop has usb that is?) and then boot from the stick and install from there?

Wow - that was a fast reply!  This laptop doesn't have to be fast - it can be clunky & slow as long as it runs (going overseas for missions).  Usability is a bigger priority than speed.  I've been thinking about Zenwalk because it's a little more polished, but Puppy is definitely plan B.

I don't think the laptp has USB, and even if it did,  I don't think the BIOS would support booting from USB.  I know Puppy can run as an image off a hard drive - that's always an option.  I've got a USB adapter for any hard drive (2.5"/3.5" IDE or SATA) - lovely tool.  Do you know if there's a network install for Zenwalk or any of the other ultra-light distros?

I can always copy data to the drive using a different computer.  I'll play with it when I get back.  Thanks for the thoughts!

---

### Post by cardinals_fan on 2008-05-11
> **twin_57103 said:**
> Wow - that was a fast reply!  This laptop doesn't have to be fast - it can be clunky & slow as long as it runs (going overseas for missions).  Usability is a bigger priority than speed.  I've been thinking about Zenwalk because it's a little more polished, but Puppy is definitely plan B.

I don't think the laptp has USB, and even if it did,  I don't think the BIOS would support booting from USB.  I know Puppy can run as an image off a hard drive - that's always an option.  I've got a USB adapter for any hard drive (2.5"/3.5" IDE or SATA) - lovely tool.  Do you know if there's a network install for Zenwalk or any of the other ultra-light distros?

I can always copy data to the drive using a different computer.  I'll play with it when I get back.  Thanks for the thoughts!
Zenwalk is a better distro, but Puppy is probably the best choice for a really old machine.  You could do a Zenwalk Core install and then just add a light WM, skipping Xfce.  I've done that on an ancient Dell and it FLIES.

---

### Post by anticapitalista on 2008-05-11
twin... have you given antiX a try yet?

---

### Post by twin_57103 on 2008-05-11
> **cardinals_fan said:**
> Zenwalk is a better distro, but Puppy is probably the best choice for a really old machine.  You could do a Zenwalk Core install and then just add a light WM, skipping Xfce.  I've done that on an ancient Dell and it FLIES.

Cool - thanks for the thoughts.  I'll have to get my hands on it to see exactly what's there.  Do you know if Zenwalk has a network installation?  I looked (briefly) but didn't find it.

---

### Post by twin_57103 on 2008-05-12
> **anticapitalista said:**
> twin... have you given antiX a try yet?

It's on my list of distros to install; several posters have recommended it.  I've got the images downloaded (base and full), but haven't gotten around to installing it yet.

I'm hoping that the laptop my friend is working on is a P2, but he told me that it's 200 MHz, which means it's probably a P1 (no idea how much RAM).  From what I saw on the antiX wiki, that won't meet the minimum requirements.  Do you know if anyone has tried it on a P1?  I'd like to get as much functionality as I can from it, but I'm guessing I'll need to stick with Puppy or DSL.

---

### Post by cardinals_fan on 2008-05-12
> **twin_57103 said:**
> 
I'm hoping that the laptop my friend is working on is a P2, but he told me that it's 200 MHz, which means it's probably a P1 (no idea how much RAM).  From what I saw on the antiX wiki, that won't meet the minimum requirements.  Do you know if anyone has tried it on a P1?  I'd like to get as much functionality as I can from it, but I'm guessing I'll need to stick with Puppy or DSL.
Yikes.  With that laptop, you might want to stick with a CLI only system.

---

### Post by twin_57103 on 2008-05-12
> **cardinals_fan said:**
> Yikes.  With that laptop, you might want to stick with a CLI only system.

I know.

Unfortunately, a CLI-only system isn't an option for the end-user. We're trying to see if we can get something graphical going, but if we can't, we'll junk it.  I'll need to get my hands on it before I know exact specs, but I'm hoping to give Puppy a try (or possibly DSL).  If that won't run, we will probably need to give up.

---

### Post by DJiNN on 2008-05-12
twin - although with that laptop i would go with something like DSL, Puppy, SLitaz or austrami etc, you could give antiX a try although i'm not sure if the latest version (7.2) will work well, if at all, on such a machine. I think that version 6.5 is still available and that's almost certain to work on a P1 or somesuch. (Assuming you have at least a reasonable amount of Ram of course.) :)

---

