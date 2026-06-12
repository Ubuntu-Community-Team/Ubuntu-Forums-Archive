---
title: "more offense, less defense!"
date: 2007-07-31
forum: Other OS Talk
---

### Post by univremonster on 2007-07-31
I was thinking about all the posts which spring up across the forums which ask "why is Ubuntu/Linux/open source better than Windows?" or vice versa and I realized that the really successful projects have been the ones which are usable within Windows.  Think about it; Firefox got almost a 10% market share within a year of the release of v. 1.0, Thunderbird has been a high flier too (sorry, had to say it).  

We as a community have been struggling to make our operating system more compatible with the programs which come out of Windows - think of all the hours spent on Wine, Cedega, VMWare, and how many programs designed to be Windows-like.  Hell we even make sure that you have solitaire on your desktop, though I must give props because that is one impressive solitaire program.  Why don't we do it the other way and make it so you can emulate Linux on your Windows box?  Wouldn't it be cool if some guy finds this free download and all of a sudden he's running windows with Compiz Fusion and a really sweet Solitaire program, as well as a suite of development tools which he could only dream about having time to download individually in Windows?  Does such a magical program exist without finding a LiveCD?

---

### Post by Bachstelze on 2007-07-31
No. Of course not. I don't think you realize how much different Windows is from other OSes...

---

### Post by LaRoza on 2007-07-31
> **univremonster said:**
> We as a community have been struggling to make our operating system more compatible with the programs which come out of Windows - think of all the hours spent on Wine, Cedega, VMWare, and how many programs designed to be Windows-like.  Hell we even make sure that you have solitaire on your desktop, though I must give props because that is one impressive solitaire program.  Why don't we do it the other way and make it so you can emulate Linux on your Windows box?  Wouldn't it be cool if some guy finds this free download and all of a sudden he's running windows with Compiz Fusion and a really sweet Solitaire program, as well as a suite of development tools which he could only dream about having time to download individually in Windows?  Does such a magical program exist without finding a LiveCD?
There may be such apps, I have hear of a few, but I wouldn't use them for these reasons:

0. It is still Windows
1. It probably doesn't make Windows any more stable, so it may make is *worse*.

There is also the difficulty of altering a close source OS.

---

### Post by univremonster on 2007-07-31
> **HymnToLife said:**
> No. Of course not. I don't think you realize how much different Windows is from other OSes...

If you mean that I don't realize it's proptrietary, I do... but creating an emulator has been done before on windows by non-Microsoft sources, even if it's just stuff like this:

[http://www.emulator-zone.com/doc.php/nes/nestopia.html](http://www.emulator-zone.com/doc.php/nes/nestopia.html)

The creation of ReactOS shows just how close we are to being able to create such a program.

---

### Post by univremonster on 2007-07-31
> **LaRoza said:**
> There may be such apps, I have hear of a few, but I wouldn't use them for these reasons:

0. It is still Windows
1. It probably doesn't make Windows any more stable, so it may make is *worse*.

There is also the difficulty of altering a close source OS.

I must also mention; while those are both admirable reasons not to use such a program, you are not the target audience.  After all, you're using Ubuntu, so why would you use an Ubuntu emulator?  The idea is to get the average Windows user to actually try Ubuntu without having to worry about something so messy as a dual boot or wiping his/her drive.

---

### Post by LaRoza on 2007-07-31
> **univremonster said:**
> I must also mention; while those are both admirable reasons not to use such a program, you are not the target audience.  After all, you're using Ubuntu, so why would you use an Ubuntu emulator?  The idea is to get the average Windows user to actually try Ubuntu without having to worry about something so messy as a dual boot or wiping his/her drive.

The risk of messing with Windows is more risky than dual-booting.

Although if such a program came out and it was somewhat stable, I would use it, but it is unlikely to happen for many reasons.

LiveCD's and dual-booting are the easiest ways to show Ubuntu, although I don't think your idea was bad, just unrealistic.

---

### Post by Steveway on 2007-07-31
1. Inform yourself better first.
2.Nobody here really wants that our apps run on windows, that would just decimate the Linuxuserbase. (If they can run Compiz on Windows, why would they need Linux?)
3.There is allready Cygwin.

---

### Post by aysiu on 2007-07-31
> **univremonster said:**
> 
The creation of ReactOS shows just how close we are to being able to create such a program. Yes... far off. ReactOS is barely functional for more than ten minutes at a time.

---

### Post by LaRoza on 2007-07-31
> **aysiu said:**
> Yes... far off. ReactOS is barely functional for more than ten minutes at a time.

All I get is the startup screen, on both of my computers.

---

### Post by univremonster on 2007-07-31
> **Steveway said:**
> 1. Inform yourself better first.
2.Nobody here really wants that our apps run on windows, that would just decimate the Linuxuserbase. (If they can run Compiz on Windows, why would they need Linux?)
3.There is allready Cygwin.

1.  I'm confused... what is it I'm supposed to be better informed about?  This is why I'm asking questions on Ubuntu Forums.

2.  Like I said in a previous post, you are not the target audience.  And I disagree thoroughly that it would 'decimate' the user base.  The first time I heard of Linux was because of Firefox.  Creating open source software that is usable by everyone on any platform is paramount.  [www.linux.org](www.linux.org) even boasts "Through the efforts of developers of desktop management systems such as KDE and GNOME, office suite project OpenOffice.org and the Mozilla web browser project, to name only a few, there are now a wide range of applications that run on Linux and it can be used by anyone regardless of his/her knowledge of computers."  

3.  Ahhh finally something useful.

---

### Post by ThinkBuntu on 2007-07-31
> **LaRoza said:**
> There may be such apps, I have hear of a few, but I wouldn't use them for these reasons:

0. It is still Windows
1. It probably doesn't make Windows any more stable, so it may make is *worse*.

There is also the difficulty of altering a close source OS.
Haha. You know you program too much when you start numbered lists with a zero!

---

### Post by igknighted on 2007-07-31
> **univremonster said:**
> I must also mention; while those are both admirable reasons not to use such a program, you are not the target audience.  After all, you're using Ubuntu, so why would you use an Ubuntu emulator?  The idea is to get the average Windows user to actually try Ubuntu without having to worry about something so messy as a dual boot or wiping his/her drive.

I think Wubi has it right.  A windows based installer, no going into Bios or anything, imports bookmarks, mail, etc... and of course the must-include: an uninstaller.  Install and configure Ubuntu from the comfort of windows, reboot and have grub give you the option on which to use (like any normal dual boot), and never have to deal with sloppy, uncomfortable installs.  Then there needs to be an uninstall option in windows.  This would delete grub, restore windows' MBR, erase the Ubuntu partition and re-expand XP's.  Perhaps you could even have the program install the ext file system driver in windows so you can see the drive clearly as well.

I don't think Ubuntu can ever truely run on windows.  You might be able to distribute VMs, but they would be huge downloads and still not super easy to use, and even then theres no 3d support.  Nope, making the install more comfortable and (at least to the average users perception) less risky is the way to go.

> Haha. You know you program too much when you start numbered lists with a zero!
Haha, very true

---

### Post by LaRoza on 2007-07-31
Second nature now, it seems most logical :D, and I object to the words "too much", code == good.

---

### Post by aysiu on 2007-07-31
You don't need to have a messy dual boot or wipe your drive.

The live CD allows you to test out a fully functional Ubuntu without affecting your hard drive, and Wubi allows you to install a dual boot without repartitioning or removing Windows' boot loader. If you have enough RAM, you can also run Ubuntu in VMWare or VirtualBox.

---

### Post by univremonster on 2007-07-31
Then I guess the general consensus is the easiest and quickest way to try Ubuntu from a Windows box is to use the LiveCD?  I have a few friends who are curious to try Ubuntu, which is why I started this post because I didn't want to download 700 Mb and burn DVDs.
edit:  more actually, one friend uses 64 bit, the other 32

---

### Post by aysiu on 2007-07-31
> **univremonster said:**
> Then I guess the general consensus is the easiest and quickest way to try Ubuntu from a Windows box is to use the LiveCD?  I have a few friends who are curious to try Ubuntu, which is why I started this post because I didn't want to download 700 Mb and burn DVDs.
edit:  more actually, one friend uses 64 bit, the other 32
Then order them from ShipIt. You can easily order as many as 10 or 20 free Desktop CDs (with nice packaging to boot). It may take a few months, but you also have the option to purchase DVDs, and those aren't very expensive either (and ship a lot more quickly).

---

### Post by fatfranko on 2007-07-31
i dont know about minnesota, but, here in california, it took less than 2 weeks for me to recieve two 32bit and one 64bit ubuntu cds from shipit.  i don't know if its a freak occurance that i recieved them so soon but its worth a try!

---

### Post by toupeiro on 2007-08-01
How shall I word this...

Firstly, I guess I'll start by saying you CAN run unix and Linux applications in windows.  You have been able to do so for years with the POSIX tools now renamed UNIX tools for Windows.  I first did this in 1997 in Windows NT 4.0.  Now that you know you've had the ability to do this in windows for at least a decade, ask yourself again why its not being done?  Because its HORRIDLY BAD!

Option 2.  A program suite called Hummingbird Exceed does a damn good job a XWindow emulation and GL extensions.  It will even do Kerberos authentication.  Its also over a thousand dollars for the full blown suite, and its a fat pig when it comes to resources.  Its nice on my work machine which is an IBM A-Pro with 2 dual core Opteron procs and 16GB of RAM.  Sadly, my home PC isn't that muscular...

Linux applications are successful cross platform because they are very functional and most of the time extremely lean when it comes to code.  Ask someone who writes installs with Installshield and Wise Package Studio, then if that same person also knows how to compile source on Linux or UNIX, ask him which is easier, Which takes longer, which costs more to do?  Since I can do both, I'll be the first to tell you that I would chose compiling in Linux over trying to follow Microsoft Logo Compliance any day!

Linux distributions should never, ever try to become more like the windows OS.  I just got the chills the other day when I installed a vendor released Linux app at work that was packaged with "Installshield for Linux".  Guess what, it was broken from installation.  I had troubleshot the problem to be the component that was installed by this installshield process (A postgresql database creation)  I did that part manually and it worked beautifully.

For me, that was a small glimpse of Linux trying to adopt a Windows Standard. They should keep right on doing what they do best and be an alternative that follows standards which have been in place in some cases longer than Microsoft has been a corporation.  

The thought of making ubuntu a "windows app" as I've seen described in this thread is totally frightening.  If you are that worried about cutting the Microsoft umbilical cord, then maybe you're just not ready for Linux yet, and that's perfectly ok too.  A virtual Machine is one thing, but don't kill the innovation of an OS like ubuntu by proposing to make it an app...

my .02

---

### Post by univremonster on 2007-08-06
> **toupeiro said:**
> 
The thought of making ubuntu a "windows app" as I've seen described in this thread is totally frightening.  If you are that worried about cutting the Microsoft umbilical cord, then maybe you're just not ready for Linux yet, and that's perfectly ok too.  A virtual Machine is one thing, but don't kill the innovation of an OS like ubuntu by proposing to make it an app...

my .02

When I started reading this post, I thought it was right on, but towards the end I became less sure that you understand what I am talking about... this has nothing to do with an umbilical cord, I've been Windows-free for long enough I hardly remember how to navigate Windows.  The idea is to create an emulator which could let people use open source software like is being done with Firefox, Thunderbird, Pidgin and Open Office, except rather than individual applications run gnome or KDE.  From the sounds of it though that is only a daydream...

---

### Post by LaRoza on 2007-08-06
> **univremonster said:**
> When I started reading this post, I thought it was right on, but towards the end I became less sure that you understand what I am talking about... this has nothing to do with an umbilical cord, I've been Windows-free for long enough I hardly remember how to navigate Windows.  The idea is to create an emulator which could let people use open source software like is being done with Firefox, Thunderbird, Pidgin and Open Office, except rather than individual applications run gnome or KDE.  From the sounds of it though that is only a daydream...

The easiest and safest way to test drive, is to use a live cd. Altough I understand the question, it is not very feasible, especially in light of better solutions.

---

