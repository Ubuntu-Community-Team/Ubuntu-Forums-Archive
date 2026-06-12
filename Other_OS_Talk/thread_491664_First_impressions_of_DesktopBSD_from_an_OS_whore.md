---
title: "First impressions of DesktopBSD from an OS whore"
date: 2007-07-03
forum: Other OS Talk
---

### Post by Scheater5 on 2007-07-03
Well, I've written one of these on Fedora 6, OpenSuSE and Sabayon and all of those were after I had become acquainted with the system.  But now I've installed DesktopBSD, and I decided to write about my impression from very early in my time with the OS, and hopefully share with you guys as some of my issues are resolved.
Well, just getting BSD installed was a challenge.  I tried FreeBSD a year or so ago and couldn't get a working system going.  But I'm quite a bit more experienced in unix-like systems now, and while FreeBSD seemed not worth the effort when I have a working Ubuntu system, PC-BSD seemed worth looking into.
Well, that failed.  I still don't know what that install had against my laptop, but the best I can tell is the entire system locked up when it tried to load X.  [http://ubuntuforums.org/showthread.php?t=490089]("http://ubuntuforums.org/showthread.php?t=490089")

So, I downloaded and installed DesktopBSD.  This time, at least I got a working desktop.  Unfortunatly, it's not all that useful.  No open office.  Didn't recognize my ALPS touchpad.  Didn't recognize my monitor resolution.  Didn't recognize my keyboard properly (the only problem resolved thus far).  But most importantly, didn't recognize my wireless card.  
And ports...wow...and I thought portage on Gentoo (well, Sabayon) was annoying.  At least when you went through the time consuming process of compiling software it worked.  And at least portage handled dependencies.  
I tried installing the firmware for my wireless card - which I found a bit odd, but every forum I searched said that's what other people had done.  Well, first I fired up the GUI for software management, and after having to "ignore" a dependency, it reported sucessful install.  But then I fired up a terminal to load the driver as per instructions found on several forums 
> kldload if_iwi
which failed.  Tried installing the firmware via command line, and that wouldn't even sucessfully install - or get started installing for that matter, spitting out some error message about X.  I couldn't see how X had anything to do with package instalation - especially when I got the same error message from a terminal (as in, not terminal emulator).  
So I thought it might be that I misunderstood how to install the driver, so I tried to install open office, and that hung on a dependency.  On a fresh install, OPEN OFFICE won't install because of unresolvable dependencies??  Wow.

---

### Post by Bachstelze on 2007-07-03
BSD is not for you. Why bother ?

---

### Post by kamaboko on 2007-07-03
I don't get it.  Isn't Linux suppose to be the easiest OS in the world to install?

---

### Post by .aku on 2007-07-03
> **kamaboko said:**
> I don't get it.  Isn't Linux suppose to be the easiest OS in the world to install?

BSD is not Linux.. ;)

//aku

---

### Post by Scheater5 on 2007-07-04
> BSD is not for you. Why bother ?

Well, that may or may not be true.  But this isn't one of those classic "these are the reasons I hate *insert OS here* and you should do things like *my favorite OS* " posts.  I don't know if BSD is for me or not, but I try and make it a policy to familiarize myself with an OS before I decide wether or not I like it.  Thus the phrase "first impression" in my topic.  I'm going to get to know BSD before I decide what to do with that partition (as in leave DesktopBSD or lose it).

BTW, Hymntolife, isn't that a Nightwish quote in your sig?  Very nice.

---

### Post by darkog on 2007-07-04
Different *nix's are suited for different things. The two main BSD's, FreeBSD and OpenBSD, are IMO geared more for network devices, routers, servers,  e.t.c. and not so much as desktops (now this is debatable until we all go blue in the face)

I am not saying that FreeBSD or any of the other BSD's can't be used as a desktop -- they can. But considering that the number of developers working on them is peanuts compared to the sheer number working on Ubuntu, SUSE or Fedora -- you might find that all the new & nifty bells and whistles, especially media related stuff (aka DVD movies making e.t.c., the newest and greatest features of Gnome ), may not be readily available on a BSD. Now, mind you, I have never used DesktopBSD or PC-BSD, but I can't imagine they have a very large developer base.

So I am not that surprised that some of your funky hardware (touchpad) didn't work out of the box so to speak. Having said that. The most secure and solid internet facing device you can have on this planet (short of military grade stuff) is a properly configured and secured OpenBSD box. It's well worth learning it.

all the best.

---

### Post by theonlyrealperson on 2007-07-05
Just as an aside, I never got the iwi-firmware-kmod to work in DesktopBSD 1.6 RC-2. It wouldn't compile, and I wasn't the only one with the problem. It was never acknowledged, and I have no idea if it is/was going to be addressed.

In vanilla FreeBSD 6.2, it works well, with only a memory allocation issue.

---

### Post by weblordpepe on 2007-07-05
The next Ubuntu is supposed to be able to get certain wifi firmwares automatically for ya. Should be cool! It was a right mess getting my Broadcom chipset working and it still doesnt do WPA

---

### Post by wilberfan on 2007-07-06
I tried DesktopBSD--twice--in the past week (once on my 64-bit dual-core AMD, once on my 32-bit Pentium 4 DELL) and found that neither would properly recognize my respective video cards--and that was during the *install* process!

Bleah.

I guess I've been spoiled by 'buntu and OpenSuSE and Sabayon...

---

### Post by amoore on 2007-07-06
I tired PC-BSD about 2 weeks ago. It was a nice, fast, and dependable OS.  The deal breaker was I could never get my Atheros wifi card to work in it. Back to Ubuntu!!!

---

### Post by ThinkBuntu on 2007-07-06
> **wilberfan said:**
> I tried DesktopBSD--twice--in the past week (once on my 64-bit dual-core AMD, once on my 32-bit Pentium 4 DELL) and found that neither would properly recognize my respective video cards--and that was during the *install* process!

Bleah.

I guess I've been spoiled by 'buntu and OpenSuSE and Sabayon...
Some just don't work right. OpenSuse Alpha 5 (10.3) and Gentoo 2007.0 both screw up when trying to launch X, but all the others work fine for me.

---

### Post by a12ctic on 2007-07-06
No distribution picks up my video card for some weird reason, I always have to do the install with 640x480@16bit colors, and I dont have a specifically uncommon video card either, 6600GT. I don't mind thoguh, once I get the nvidia drivers working everythign works fine.

---

### Post by wilberfan on 2007-07-06
> **a12ctic said:**
> No distribution picks up my video card for some weird reason, I always have to do the install with 640x480@16bit colors, and I dont have a specifically uncommon video card either, 6600GT. I don't mind thoguh, once I get the nvidia drivers working everythign works fine.

I have an GeForce 6600 (2 years old now?) and I think OpenSuSE and Sabayon were the ONLY two distros that properly recognized it?   I started down the Linux path last August with Dapper--and NO release of Ubuntu has been able to give me my 1280 x 1024 @ 60 that I want for my HP f1905e LCD monitor.   

DesktopBSD was the first distro where the LiveCD / Install would not give my ANY kind of usable display!  :o

---

### Post by Scheater5 on 2007-07-07
Well, it's been several days now, and I've made no headway.  Still no joy on compiling anything.  Thinking about trying, as someone else put it "vanilla" FreeBSD soon, and I've got the Desktop 1.6RC2 downloaded as well.  Dunno what the problem is.  I would mess with it more except for two things:
I have yet to have even a hint of malicious software on my Ubuntu install, and one of the reasons I wanted to try BSD was security since I'm on a university network.
And two, it doesn't seem particularly responsive or fast, which was another reason I thought I might like it.  I was hoping to be able to set it up where I could easily browse the web and do word processing - in other words, school work.  But, for now, the partition merely sits there taking up space.  For now, DesktopBSD is still installed on it.  And should I run out of projects, I may give it another go.  Now, I'm off to read more about SSH.

---

### Post by hanzomon4 on 2007-07-08
Well I've tried PC-BSD and I like it, v1.4 comes with beryl by default!! Only problem is sound, I can't get my supported m-audio delta 66(snd_envy24) sound card to work. With 1.3 I got sound but couldn't control the volume. The ports system seems a bit dated compared to some parts of gentoo's portage system, like emerge. I got high hopes for the BSDs however, being that everything, other than sound, worked. It also screws up my clock in Ubuntu but I have this problem with every dual, I eventuality fix it but always forget how.....

---

### Post by mips on 2007-07-08
> **hanzomon4 said:**
> It also screws up my clock in Ubuntu but I have this problem with every dual, I eventuality fix it but always forget how.....

Is that not because of the UTC selection for the bios clock when you install ? So what happens is the OS assumes the bios clock is set to UTC and then it automatically adjusts it according to your timezone.

I get the same problem with a windows dual boot. One way to do it is to set your bios clock and tell the system not to use UTC.

---

### Post by Shakkaa on 2007-07-09
I completely agree with darkog on this thread.   BSD doesn't have nowhere near the support that linux has, yet if you're looking for server software FreeBSD and specially OpenBSD are the ones to look at.  The reason why they're not as responsive is because the BSD kernel isn't as memory aggressive as the linux kernel.  They're meant for different things.  Personally I think that if BSD taps the desktop community, they have a long way to go, because their kernel is currently not developed for a desktop.  IT IS an incredible piece of software.  OpenBSD was once banned from DefCon for being unhackeable O.o

---

