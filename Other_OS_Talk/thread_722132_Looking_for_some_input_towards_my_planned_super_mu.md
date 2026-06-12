---
title: "Looking for some input towards my planned super multiboot"
date: 2008-03-12
forum: Other OS Talk
---

### Post by Squish on 2008-03-12
Due to the nature of my ubuntu right now, after installing countless alpha's, strange legacy packages, and reinstalls that didnt quite go right, my computer is a bit scrambled... All of course due to my own undertakings, which is fine ol fine (Ever try to install Jahshaka on 7.10?). I have decided that I want to attempt a super-multi-boot, which will have a taste of everything.

I have 5 issues I need advice on first. 

1: What OS's should I get. Preferably, I would like at least 1 Linux derivative from each branch, such as Gentoo, Debian, Slackware, etc... I would also like every notable distribution that I hear so many good things about, such as arch, PCLinuxOs, etc... and I would also like a distribution that specialized in each gui, from gnome, to enlightenment. For fun, I would not mind seeing if I could get some of the classics running, and as well, having some super speed demons on it as well.
I would also like to have at least windows xp, and vista. If possible, even stuff like windows 98... or god forbid... windows ME...
Then I would like to sample from some of the other players, which would be:
OpenSolaris
ReactOS
BSD ~ or whatever it is...
And if possible, even stuff like:
A Mac OS, OS/2, Amiga, and whatever other quacky things are out there.

2: Setting up each operating system to share the same filesystem: I have a 250 gb harddrive, and my idea is to install each os on 50 gb's, and have them all share a 200 gb partition. Basically, what would one suggest partitioning the 200 gb as? I would rather not do a fat, but I am aware it is like far more compatible...

3: Grub or Lilo: One problem I had during setting up multiboots, is that each os would setup its own grub or lilo... so when the first grub would show me a list to choose from, and say I chose opensuse, it would take me to a opensuse lilo... if I have to, I dont mind having a ton of branches... but I would like to show off to my friends, a computer that boots up, and prompts about a dozen operating systems, and it just goes and boots up whichever one I tell it too.

4: Hardware: This is the trickiest part I am assuming, as this is a laptop, and so it has a bit more unique hardware. Here is what I got, with full specs:
[URL="http://system76.com/product_info.php?cPath=28&products_id=51"]http://system76.com/product_info.php?cPath=28&products_id=51
[/URL] With such hardware, I understand that I wont be able to run everything I want, so it doesnt matter if I have to scratch say, Os/2 off the list :)

5: is this possibly the most impractical idea ever?
:lolflag:

Just something to keep me busy for awhile, and something I can say to potential employers: HEY LOOK HOW BIG OF A NERD I AM!!!

---

### Post by mips on 2008-03-12
Virtualbox!

---

### Post by jken146 on 2008-03-12
> **Squish said:**
> 1: What OS's should I get. Preferably, I would like at least 1 Linux derivative from each branch, such as Gentoo, Debian, Slackware, etc... I would also like every notable distribution that I hear so many good things about, such as arch, PCLinuxOs, etc... and I would also like a distribution that specialized in each gui, from gnome, to enlightenment. For fun, I would not mind seeing if I could get some of the classics running, and as well, having some super speed demons on it as well.
I would also like to have at least windows xp, and vista. If possible, even stuff like windows 98... or god forbid... windows ME...
Then I would like to sample from some of the other players, which would be:
OpenSolaris
ReactOS
BSD ~ or whatever it is...
And if possible, even stuff like:
A Mac OS, OS/2, Amiga, and whatever other quacky things are out there.
Go with whatever you feel like trying.  It sounds like you've got the disk space, so keep cramming them in!  Performance -- pretty much every distro will run well on that machine, I expect, with the exception of Windows Vista.  If you miss one out, miss out that one.  DEs/WMs -- you might learn more about what you like in terms of GUIs than in terms of distros, so try them all.  See if you can find a nice theme for OroboROX; I couldn't.

> 2: Setting up each operating system to share the same filesystem: I have a 250 gb harddrive, and my idea is to install each os on 50 gb's, and have them all share a 200 gb partition. Basically, what would one suggest partitioning the 200 gb as? I would rather not do a fat, but I am aware it is like far more compatible...
I would recommend ext3, because it has never given me any problems.  Windows XP can read & write to ext3 with [this]("http://fs-driver.org") driver.  FAT is awful: avoid it!  NTFS may be your only option though, if you use Windows Vista.  I *think* that Linux can read/write Mac file systems, but I'm not sure.  It can read & write NTFS.

I think that 50 GB for each distro is too much.  If you try out a lightwieght Linux distro like Puppy, you certainly won't need more than a gig or two, after if you install tons of packaged software.  I would say no more than 10 GB for each Linux distro, with the exception of Sabayon, which complains if you give it less than 15 GB.  Distros that you install yourself from the ground up, like Arch, Gentoo or even a minimal Ubuntu install, will take up a lot less space than the 'usual' ~2-4 GB desktop linux install.  You also don't have enough  disk space to have a 200 GB partition and more than one 50 GB partition on that laptop.

Don't forget a swap partition -- no more than 1 GB.

> 3: Grub or Lilo: One problem I had during setting up multiboots, is that each os would setup its own grub or lilo... so when the first grub would show me a list to choose from, and say I chose opensuse, it would take me to a opensuse lilo... if I have to, I dont mind having a ton of branches... but I would like to show off to my friends, a computer that boots up, and prompts about a dozen operating systems, and it just goes and boots up whichever one I tell it too.
Use GRUB, rather than LILO.  You could get each distro to install GRUB on its own / partition, then get one final distro to detect them all (installing GRUB on the MBR).  This could lead to a lot of promps to use, though.  A better solution might be to manually edit the menu.lst of the last GRUB installed, copying the relevant sections from each distro's menu.lst.  It's a good idea to have individual installations of GRUB for each distro, as this gives you a bit of a fallback.

> 4: Hardware: This is the trickiest part I am assuming, as this is a laptop, and so it has a bit more unique hardware. Here is what I got, with full specs:
[URL="http://system76.com/product_info.php?cPath=28&products_id=51"]http://system76.com/product_info.php?cPath=28&products_id=51
[/URL] With such hardware, I understand that I wont be able to run everything I want, so it doesnt matter if I have to scratch say, Os/2 off the list :)
This is probably a case of trying and seeing.

> 5: is this possibly the most impractical idea ever?
:lolflag:
No, not at all.  I've done similar things and it isn't really that hard.

> Just something to keep me busy for awhile, and something I can say to potential employers: HEY LOOK HOW BIG OF A NERD I AM!!!
I'm not sure that potential employers will care to be honest.

Have fun!

---

### Post by Squish on 2008-03-12
> Go with whatever you feel like trying.  It sounds like you've got the disk space, so keep cramming them in!  Performance -- pretty much every distro will run well on that machine, I expect, with the exception of Windows Vista.  If you miss one out, miss out that one.  DEs/WMs -- you might learn more about what you like in terms of GUIs than in terms of distros, so try them all.  See if you can find a nice theme for OroboROX; I couldn't.
 ha, I better not try vista until I have at least 8 gigs of ram, and a dual quad core setup, with 6 cores directly set to running aeroglass...
Well, I was thinking that I would like to see if I could get mac installed, because I might have to use some of its software for video editing. I had come across a x86 version (you know, when everything was still PowerPC), and I was thinking it might be a bit more versatile than getting a regular macosx... considering the harsh proprietary nature, and refusal of flexibility philosophy they adopt. So in short, what would you reccomend for mac - the altered x86 version, or just a reg mac os?


> I would recommend ext3, because it has never given me any problems.  Windows XP can read & write to ext3 with [this]("http://fs-driver.org") driver.  FAT is awful: avoid it!  NTFS may be your only option though, if you use Windows Vista.  I *think* that Linux can read/write Mac file systems, but I'm not sure.  It can read & write NTFS.Fat is awful... hopefully ext3 will be able to work with all em crowds... 
> 
I think that 50 GB for each distro is too much.  If you try out a lightwieght Linux distro like Puppy, you certainly won't need more than a gig or two, after if you install tons of packaged software.  I would say no more than 10 GB for each Linux distro, with the exception of Sabayon, which complains if you give it less than 15 GB.  Distros that you install yourself from the ground up, like Arch, Gentoo or even a minimal Ubuntu install, will take up a lot less space than the 'usual' ~2-4 GB desktop linux install.  You also don't have enough  disk space to have a 200 GB partition and more than one 50 GB partition on that laptop. Pardon me, I meant taking the 50 gigs, and splitting them up into say, a dozen smaller partitions, of which each I will install a new os.
> 
Don't forget a swap partition -- no more than 1 GB.Absolutely, its sorta a given. Although I am not sure if I will be able to use more than the 4 gigs I already have:guitar:

> Use GRUB, rather than LILO.  You could get each distro to install GRUB on its own / partition, then get one final distro to detect them all (installing GRUB on the MBR).  This could lead to a lot of promps to use, though.  A better solution might be to manually edit the menu.lst of the last GRUB installed, copying the relevant sections from each distro's menu.lst.  It's a good idea to have individual installations of GRUB for each distro, as this gives you a bit of a fallback.
 The manual edits will require a bit of education, however its probably worth the learning exercise. I hear vista is freaking gay when it comes to installing multi's.... I better do that first.
> 
This is probably a case of trying and seeing. Definitely... I look forward to reactos


> No, not at all.  I've done similar things and it isn't really that hard.Good good, then it is doable:KS


> I'm not sure that potential employers will care to be honest. Well, it sorta worked with me getting a job with HP. They asked me if I knew anything bout computer, and I just went on about all the nerd projects I did on my computer, just trying to talk as advanced and technical as I could. It was rather humorous, but they stopped me in the middle and said something like: ok ok, we get the point~
> 
Have fun!Thanks

---

### Post by Shazaam on 2008-03-12
+1 for virtualization. Some distro's can be problematic. I once had 8 distros loaded into a massive multi-boot vm. If something went haywire on an install it wasn't a problem. Unfortunatly I set the vm disks up as expanding instead of static and they outgrew the room I had set aside for them. Time for a new one!

---

### Post by wolfen69 on 2008-03-12
just remember to install ubuntu last, as it does a wonderful job at recognizing other OS's and getting grub right.

---

### Post by Squish on 2008-03-13
Yah the ubuntu does do it nicely, however, it is a fairly raw grub screen. For a purely aesthetic reason, what would you suggest gives the nicest grub...

Hmmm, actually, I should see if I could get a pretty ubuntu grub, as it only makes sense seeing I have a "Powered by Ubuntu" sticker on mine...

Edit:
> +1 for virtualization. Some distro's can be problematic. I once had 8 distros loaded into a massive multi-boot vm. If something went haywire on an install it wasn't a problem. Unfortunatly I set the vm disks up as expanding instead of static and they outgrew the room I had set aside for them. Time for a new one!
Hmmm, I had forgotten to consider that.
In essence, VM's are operating systems in themselves. Is there any distrobutions that specialize in such a thing... cause I drool at the prospect of a compiz fusion VM session, with 3 differant desktops all running at the same time...
hmmm, if only I had quad core...

Oh, what would you suggest for VM's in the area of free? I have tried VMware, as well as XEN...?

---

### Post by mips on 2008-03-13
> **Squish said:**
> Yah the ubuntu does do it nicely, however, it is a fairly raw grub screen. For a purely aesthetic reason, what would you suggest gives the nicest grub...

Hmmm, actually, I should see if I could get a pretty ubuntu grub, as it only makes sense seeing I have a "Powered by Ubuntu" sticker on mine...

Edit:

Hmmm, I had forgotten to consider that.
In essence, VM's are operating systems in themselves. Is there any distrobutions that specialize in such a thing... cause I drool at the prospect of a compiz fusion VM session, with 3 differant desktops all running at the same time...
hmmm, if only I had quad core...

Oh, what would you suggest for VM's in the area of free? I have tried VMware, as well as XEN...?

I like Virtualbox.

---

### Post by Squish on 2008-03-25
Super Multiboot Update

*Linux*

      Debian
      + Ubuntu
      + Damn Small Linux (Based off knoppix, which is based of debian)

      Gentoo
      + Sabayon

      (RPM Based)
      Fedora 8
      Opensuse 10.3
      Mandriva
      PCLinuxOS

      (Others)
      Slackware
      Deli
      Arch


*Windows*

      98
      XP
      Vista
      OS/2
      Reactos

*Unix*

      Darwin
      iATKOS (Mac for PC) (just assume that I am an apple dev)
      Minix
      Plan9
      Solaris
      FreeBSD


And finally,
Aros (Amiga for the x86)

From this list, I will trim and decide where to go from here. First I need to make known the complications:

1> The goal is to fit all these operating systems on 50 gigabytes worth of hard drive (on a 250 gigabyte harddrive, leaving 200 gigs for universal storage shared between all operating systems). To make this easier, I am willing to cut certain operating systems based on if they provide a redundant experience, and do not bring something unique to the table. I will also have to figure out how much space I should allocate for each os in accordance to how much space it needs, and how much space software will fill up. Given that it is likely that my operating systems of choice will likely be one from each platform (xp or vista + Ubuntu, Slackware, Opensuse, Arch, Gentoo, or Sabayon + iATKOS), for whichever ones I choose, I will need to allocate additional space for the programs I will want to run.
At current, I do not use more than 6 gigabytes on my ubuntu for installed junk. Windows can run programs off the 200 gig universal storage partitioned as ext3 (Right?), and I am not entirely sure how mac works. The thing about mac is that I want to get Final Cut Studio, and that is a 50 gig program alone. So I need to find out how much space it will take when I install it, and whether it has to be installed on the same partition the mac comes in?

2> The order of installations:
I will most likely be installing the linux last, as they are best at dealing with custom partitions, and play nice with other operating systems. The ones I want to get out of the way are the Mac, Vista, XP, 98, OS/2, and Aros.
OS/2 is a fickle beast, and I have my suspicions that I will have to drop it. I downloaded the OS, but it came in like 15 floppy images... and I do not have a floppy drive, nor do I want to deal with it.
So what should go on first? Mac? Vista? XP?
I was thinking it might be a good idea to make some of the partitions ahead of time, so they can go exactly where I tell em too.

3> What should I choose for my os's of choice in regards to Linux.
Personally I am an ubuntu guy, however i have never used anything Slackware, Gentoo always peaked my interest, especially how advanced sabayon is, Opensuse I quite enjoyed as my first os, and Arch for some reason always gets recommended. My preference is gnome, however I liked opensuse's variant of kde. I wasnt a huge fan of kde4, partly because I missed the icey feel, konquerer, and that the icon system was a fair bit strange. Compiz Fusion is a must, so what will work best with that is pretty essential too.

---

### Post by Lord Illidan on 2008-03-25
Regarding your problem, personally, I'd do it in Virtualbox, it saves you a lot of hassle, plus, you can run 2 or more distros (depends how much RAM you have) at the same time, which is pretty freaking cool in my opinion. For instance, XP running with Linux.

---

### Post by Squish on 2008-03-25
Although that is an option that I am keeping open, I would rather be able to do multiboots, as virtual machines will not run the games I want at the speeds I want. That is indeed another project though, setting up something similar. I might want to get a stronger processor for that though.

---

### Post by Lord Illidan on 2008-03-25
Perhaps an option would be a dualboot of 1 Linux distro, and Windows (thus giving you games), and the rest virtualised on Linux, or whatever you prefer.

---

### Post by Squish on 2008-03-25
The thing about the virtual machine that is sort of throwing me off, is that I would like to set up the machine in a way that running other operating systems looks like such an easy process, as many other users use the machine. Its allot easier to say to someone to just reboot the machine and choose from the list, versus open up a terminal and run such and such command. Part of the excersize is to show how easy using linux is along side other programs, and I shy away from having to show em intense terminal sessions.

buuut, i have never used virtual box... is there a nice frront end that makes all these things easy as pie, and look easy as well?

---

### Post by mips on 2008-03-25
> **Squish said:**
> The thing about the virtual machine that is sort of throwing me off, is that I would like to set up the machine in a way that running other operating systems looks like such an easy process, as many other users use the machine. Its allot easier to say to someone to just reboot the machine and choose from the list, versus open up a terminal and run such and such command. Part of the excersize is to show how easy using linux is along side other programs, and I shy away from having to show em intense terminal sessions.

buuut, i have never used virtual box... is there a nice frront end that makes all these things easy as pie, and look easy as well?

It's all GUI based and you have your list of operating systems which you simply select with a mouse click. Depending on cpu & ram you could run a few at the same time. Usim VM will be much easier and simpler than doing a multiboot.

---

### Post by Dr. C on 2008-03-25
You may wish to check this out. 145 operating systems on one machine.

137 GNU / Linux
5 Windows
3 DOS

[http://www.justlinux.com/forum/showthread.php?p=861282#post861282]("http://www.justlinux.com/forum/showthread.php?p=861282#post861282")

---

### Post by Squish on 2008-03-25
That thread is awsome, exactly something I could use!

oh so btw, from the list of os's, would there be any that anyone would trim for the purpose that it does not offer anything unique to the table... such as mandriva, pclinuxos, suse, or fedora?

---

### Post by maybeway36 on 2008-03-26
I don't think you can fit all thouse Windows and BSD variants on one hard drive, becasue you can only have 3 primary partitions and 1 extended partition. Linux can boot from a logical partition inside an extended partition, so the more the better.
Add Puppy Linux too; it can install on the same partition as another OS, and it's only 100MB.

---

### Post by markharding557 on 2008-03-26
i really can't see the purpose in having so many linux o/s installations,they all have much the same softwares just configured in different ways and with different themes

---

### Post by cardinals_fan on 2008-03-26
Definitely try Zenwalk.  Also include vanilla Slackware.

---

### Post by Squish on 2008-03-27
> 
Hard disk considerations

Most MS systems are designed to reside in a primary partition and there can be a maximum of four of 4 primaries in each hard disk. To get more partition a user “must” give up one primary to turn it into an extended partition. In Linux a Pata (or IDE) disk can have 63 partitions maximum and the limit of a Sata or SCSI disk is 15.

The number of partition plus the whole disk itself make up 64 and 16 devices repeactively.


So does this mean I can have 16 boots?

If that is the case, then 3 primaries go towards microsoft, and I will have 13 os's on the others...

Does that make sense?

Which means, if I can only have 13...

Scratch:
Debian
Mandriva
OS/2
Darwin
Deli
DSL

Sabayon or Gentoo?


Leaving me

1 Windows 98
2 Windows XP
3 Windows Vista
4 Mac
5 Aros
6 Solaris
7 Plan 9
8 Minix
9 FreeBSD
10 Arch
11 Fedora
12 Opensuse
13 Gentoo or Sabayon
14 PCLinuxOS
15 Slackware
16 Ubuntu

Did I get that right?
Oh and seriously, gentoo or sabayon?

---

### Post by maybeway36 on 2008-03-27
1. To the best of my knowlegde, FreeBSD cannot install to an extended partition, only a primary one. You might need to scrap that too.
2. Keep DSL! It can share a partition with another OS (this is the beauty of the frugal install.)

---

### Post by mips on 2008-03-27
> **maybeway36 said:**
> 1. To the best of my knowlegde, FreeBSD cannot install to an extended partition, only a primary one. You might need to scrap that too.


As far as I know that goes for all BSDs...or Unixes.

---

### Post by Squish on 2008-03-28
Yarg, that makes for some difficult decisions...


I hear you can do windows on extended however[http://www.goodells.net/multiboot/]("http://www.goodells.net/multiboot/")... so if possible, I could have the 4 primary as:
Mac
Free BSD
Solaris
Plan9
Minix

Im sure one of those could do an extended

---

### Post by mips on 2008-03-28
> **Squish said:**
> ... I could have the 4 primary as:
Mac


What do you mean by Mac?

---

### Post by maybeway36 on 2008-03-28
You can only have 3 primary and one extended, actually, so that makes it difficult. :(
Luckily, you can have as much Linux as you can fit on the hard drive. Yay for logical partitioning!

---

### Post by Squish on 2008-03-29
I thought I posted it... but it must have been deleted. Mentioning it I suppose is taboo.

The mac-holes told me so as well, but I had no bad intentions... 
Stuck up operating system...

---

### Post by hhhhhx on 2008-03-29
if you can get a hackintosh on there that would be cool :)

---

### Post by Squish on 2008-03-30
Shhhh, havnt you heard that mac is spying, and calling the isp's of people to shutdown hackers who dare tread among the mac~

Not a big fan of the mac philosophy... im gonna be honest.

---

### Post by maybeway36 on 2008-03-30
You're not going to get much community support for installing it either, considering it normally comes pre-installed.

---

### Post by hhhhhx on 2008-03-30
> **maybeway36 said:**
> You're not going to get much community support for installing it either, considering it normally comes pre-installed.
ORLY:
[http://www.hackint0sh.org/forum/indexpage.php](http://www.hackint0sh.org/forum/indexpage.php)

---

### Post by Squish on 2008-04-06
Alright, I have a partition scheme needing approval:

Primary - 10gb - Vista
Primary - 10gb - XP
Extended
Logical - 55 gb - iATKOS
Logical - 0.5 gb - Aros
Logical - 0.5 gb - Plan 9
Logical - 0.5 gb - Reactos
Logical - 1 gb - Arch Linux
Logical - 4 gb - Fedora 8
Logical - 4 gb - Gentoo
Logical - 4 gb - Opensuse 10.3
Logical - 4 gb - PCLinuxOS
Logical - 4 gb - Slackware 12.0
Logical - 6 gb - Ubuntu 8.04
Primary - 125 gb - EXT3 for free space
Swap - 4gb


I setup iATKOS, and then ubuntu, but the ubuntu grub didnt detect it... why?

Essentially my plan thus far is to setup beforehand the partitions in gparted, Then go forth and install xp, then vista, then mac, and then the rest, ending with ubuntu

---

### Post by Squish on 2008-04-12
So I have been at it for a quite a few hours today.

What I have discovered is that XP is impossible... well probably is, but I am not keen enough to go for it, and vista will do. Essentially XP cant detect my harddrive, so shucks to that..

Right now I am trying to get mac on to my comp, and work from there. I have tried tirelessly to get IATKOS on, however I cant get it to boot up, so I am going to try Kalyway instead.

If I can get mac, vista, and ubuntu on, then I will be happy. From there I will go and add reactos, minix, plan9, and a slew of Linux

huh.... damn you mac!

---

### Post by Squish on 2008-04-13
Update:

12 hours of trying to get this thing to work... and not to any avail yet...
Right now my os is a live ubuntu cd, and I am currently downloading the next version of Kalyway, a mac osx86 version, in which I will burn to a cd.... Which sounds funny because I am running a live cd!
No worries, I have a plan for that...

---

### Post by sizzoid on 2008-04-14
Hello squish.
Remember, XP creates a vfat partition for it's own restore business. So it's stealing one of your primary partitions.

---

### Post by Squish on 2008-04-16
no kidding... 
Well it looks like im skipping xp anyways...

but thanks for the knowledege. I almost have the new kalyway downloaded!

---

