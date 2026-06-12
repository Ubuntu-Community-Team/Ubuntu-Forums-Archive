---
title: "Should i use Gentoo?"
date: 2007-10-26
forum: Other OS Talk
---

### Post by rekahsoft on 2007-10-26
Hi all, i am thinking of installing gentoo...what would be the advantages of doing so? how is the install process? i have heard that gentoo buildes everything from source so it takes a long long time to get the system up and running and that the install process is not very nice...i am a coder so i do not mind building the system from sources...i was just wondering what the OS has to offer...besides of course the awesome learning experiance :P

---

### Post by LaRoza on 2007-10-26
> **rekahsoft said:**
> Hi all, i am thinking of installing gentoo...what would be the advantages of doing so? how is the install process? i have heard that gentoo buildes everything from source so it takes a long long time to get the system up and running and that the install process is not very nice...i am a coder so i do not mind building the system from sources...i was just wondering what the OS has to offer...besides of course the awesome learning experiance :P

Then install it, nothing is hurt by trying

The home page of Gentoo is quite informative, just read and follow along.

I would ask Gentoo users, they seem to love it.

Building from source isn't as hard as some believe it to be, so don't worry about that.

---

### Post by rekahsoft on 2007-10-26
well..the building from source is np for me..lol..i hack up my ubuntu install all the time..i am really thinking about installing gentoo tho...

---

### Post by cotcot on 2007-10-27
I am using gentoo as well.

I installed gentoo almost 2 years ago because I could not get some apps in ubuntu (and other OS fedora, suse). If they were available I anded up in dependancy problems. The apps were hugin, autopano-sift, opera, epson printer driver.
After the well known learning curve I got them installed in gentoo. I recently checked the apps with Gutsy and they are ok now.

Reasons for gentoo are the speed (is clearly faster than ubuntu but the difference is not that big that is should be the only reason to switch to gentoo; the difference is less visible the more powerful your computer is); good documentation, recent software versions available.
Forums are excellent as well (small but specialized people actively responding)

---

### Post by fwojciec on 2007-10-27
If you hack up Ubuntu all the time then go ahead and install Gentoo.  It might be a learning curve at first (nothing too bad though - and Gentoo has excellent documentation) but you will like it better than Ubuntu in the end, I think.  

Ubuntu excels at providing a good default that just works for a lot of people, if you have that urge to customize everything about Ubuntu, however, you might just as well learn how to build a Linux system from ground up the way you like it - and Gentoo will let you do that.  It's much more fun that way, IMO, but it does take a certain kind of personality and attitude towards computers to enjoy it.

---

### Post by rekahsoft on 2007-10-27
ok..i have decided i am going to install gentoo...i have read through the install handbook...i am going to go with a partitioning scheme like so:

/boot as ext2 size:100mb
swap size 2gb
/ as reiserfs size 15gb
/home as reiserfs size:the rest available

i am going to turn on DMA...does anybody have any eperiance with this? and do you see any issues with my partitioning scheme?...do u think that 15gb is too big for /...and is 2gb too big of a swap?..i have always had it at 2gb but i don't think that much has ever been used..any tips before i start?

---

### Post by LaRoza on 2007-10-27
> **rekahsoft said:**
> 
i am going to turn on DMA...does anybody have any eperiance with this? and do you see any issues with my partitioning scheme?...do u think that 15gb is too big for /...and is 2gb too big of a swap?..i have always had it at 2gb but i don't think that much has ever been used..any tips before i start?

Do you hibernate? Fi not, then yes, 2 GB is a waste. People have tried getting the swap smaller, and found 128 MB often worked. If you have the room, I would use 512 MB.

---

### Post by fwojciec on 2007-10-27
> **rekahsoft said:**
> ok..i have decided i am going to install gentoo...i have read through the install handbook...i am going to go with a partitioning scheme like so:

/boot as ext2 size:100mb
swap size 2gb
/ as reiserfs size 15gb
/home as reiserfs size:the rest available

i am going to turn on DMA...does anybody have any eperiance with this? and do you see any issues with my partitioning scheme?...do u think that 15gb is too big for /...and is 2gb too big of a swap?..i have always had it at 2gb but i don't think that much has ever been used..any tips before i start?

Ask this question on Gentoo forums, you're likely to get better answers.  I would consider using something like 20GB partition for root.  Portage tree, from what I've read, can take up quite a bit of space, and some programs (like Openoffice for example) require considerable amount of disk space during compilation.

---

### Post by rekahsoft on 2007-10-27
well i decided i am not going to install gentoo today...reason being cause i have school work to do and i need a stable system for school...i am buying a new desktop and laptop for university in the near future so then i will set up a system with gentoo :D

---

### Post by cotcot on 2007-10-28
15 GB for / is more than enough. 10 GB will do as well. If the 10 GB is full it is better to clean up (old distfiles etc).
Please check the meaning of use flags. I have a limited amount in my make.conf and the rest per package (in package.use). If you put all use flags in make.conf you miss one of the advantages of gentoo. Goal is to have only those use flags in make.conf that are often use and the rest per package. You can check the use-flags with emerge -pv ebuild-you-want-to-install.
Success !

---

### Post by meborc on 2007-10-28
on a different note, but still on topic of gentoo... has anyone ever done a speed comparison of arch and gentoo? i am facinated with the ideas behind arch and pacman :) but my laptop is really slow :( so i would need every ns of speedgain i can get... is gentoo faster then arch?

---

### Post by fwojciec on 2007-10-28
This is what [Arch wiki]("http://wiki.archlinux.org/index.php/Arch_vs_Others#Arch_vs_Gentoo") says on the topic of comparison between Gentoo and Arch:
> Because the Arch installation is binary, it is much less time-consuming than a source-based Gentoo installation. Gentoo has more packages and lets you choose the exact version of a package you want to install. Both Gentoo and Arch allow binary and source-based packaging; however, Gentoo is mainly source-based while Arch is mainly binary-based. Both are rolling-release systems. Arch PKGBUILDs are easier to create than ebuilds. Gentoo is more portable out of the box as packages will get compiled to your specific architecture, whereas Arch is optimized for i686 and x86-64 only (although an i586 user-based spin-off project is underway). There is no documented proof that Gentoo is any faster than Arch or vice-versa. The Arch design approach is more focused on simplicity.
If you're interested in the differences between Gentoo and Arch you can also have a look at these threads on [Gentoo]("http://forums.gentoo.org/viewtopic-t-577784-postdays-0-postorder-asc-start-0.html") and [Arch]("http://bbs.archlinux.org/viewtopic.php?id=36649") forums.

Bottom line: speed should not be the main criterion for choosing between Gentoo or Arch - other differences are much more significant.

---

### Post by happysmileman on 2007-10-29
Advantages would be great speed increases... Compiz-fusion works fine for me on my 512MB RAM comp with 64Mb graphics, on *buntu it's horribly slow...

Took me about 3 days to get a base KDE install working, had to leave KDE to build overnight... Soem advice I'd give is read the gentoo websites instructions for KDE/GNOME or anything big like that, I accidentally installed dozens of KDE packages I didn't want first time around.

I also like knowing that I don't have a bunch of apps I'll never use run in the background

---

### Post by rekahsoft on 2007-10-29
well i went for the install and buchered it...i did not know that the intaller does not format the disks after i set what thier mount points are to be...so after failing multiple times i booted to ubuntu to see it totaly screwed up :S...all my users were deleted, my sound conf was messed...and a ton more...i managed to log in after deleting the encrypted password of root from the shadow file..but everything was broken bad...so i reinstalled...anyways i am now in a nice functioning kubuntu system :D...although when i buy a desktop i am going to install gentoo for sure :D

---

