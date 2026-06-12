---
title: "Solaris"
date: 2007-04-12
forum: Other OS Talk
---

### Post by jazzman83 on 2007-04-12
This is just an information post.  I am have been intrigued about using Solaris for a while now but I know very little about it.  I was wondering if I could have some feedback on using Solaris.

I use my computer for both work and home purposes.  I use a variety of programs such as Matlab, Pro/E, Latex, various graphic programs and program with C++.  I was wondering if it made any sense at all someone like me trying out Solaris or any other OS for that matter.  I do most of my work now on Ubuntu - except for the Windows programs of Pro/E and Matlab.

Any info on Solaris in general would also be welcome. Thanks

---

### Post by igknighted on 2007-04-12
> **jazzman83 said:**
> This is just an information post.  I am have been intrigued about using Solaris for a while now but I know very little about it.  I was wondering if I could have some feedback on using Solaris.

I use my computer for both work and home purposes.  I use a variety of programs such as Matlab, Pro/E, Latex, various graphic programs and program with C++.  I was wondering if it made any sense at all someone like me trying out Solaris or any other OS for that matter.  I do most of my work now on Ubuntu - except for the Windows programs of Pro/E and Matlab.

Any info on Solaris in general would also be welcome. Thanks

MatLab has a linux native version, any reason you don't use that in linux?

As for Solaris, for programming work it is good.  Sun offers a very nice development suite (although I think it is mainly targeted at Java).  For most of the other stuff, it might be a struggle.  You could check out Nexenta, it is basically Ubuntu, but built around the solaris kernel.  It is only in an alpha state though.  Belenix is also nice (another open-solaris distro).  Overall, it never hurts to try out new OS's.  If you aren't going to try sun's official solaris 10, I might try BSD first.  The open-solaris projects are just too young.

---

### Post by jazzman83 on 2007-04-12
> **igknighted said:**
> MatLab has a linux native version, any reason you don't use that in linux?

Thanks for the reply igknighted.  I know Matlab has a linux version but I only have a regular Windows version CD.  I have tried using Crossover Office to install it but never managed to get it working.

Thanks for the info on the other OS'es.  Is Solaris mainly used from a server/client perspective then if it wouldn't suit my purposes properly? I have looked quickly at FreeBSD but it never really seemed to catch my eye.

---

### Post by igknighted on 2007-04-12
> **jazzman83 said:**
> Thanks for the reply igknighted.  I know Matlab has a linux version but I only have a regular Windows version CD.  I have tried using Crossover Office to install it but never managed to get it working.

Thanks for the info on the other OS'es.  Is Solaris mainly used from a server/client perspective then if it wouldn't suit my purposes properly? I have looked quickly at FreeBSD but it never really seemed to catch my eye.

Honestly, at this point solaris just isnt much used.  It is growing as the kernel was just opened up, but until recently if you weren't running sparq architecture then you probably didn't use Solaris.  Now, solaris is a very solid kernel and once great distro's are built around it then it will be a great OS.  If you were a java developer I would recommend Solaris, because Sun is its major backer and there are great java developer tools.  However, you would have to look closer on the sun site to see if those do C++ as well, I couldn't tell you.

Sorry to ramble, but the quick answer to your question is avialability of apps.  It has long been great for servers, but is just really starting to blossom on the desktop, and java development is its strong point thanks to being a Sun product.

---

### Post by handy on 2007-04-13
I've just installed [***_Nexenta_***]("http://www.gnusolaris.org/gswiki/Nexenta_OS"), it looks like Ubuntu, even brown! :) 

It installed easily on an old Asus A7N266-VM motherboard (which the FreeBSD's have terrible trouble with by the way!)

My broadband worked straight away too.

It is different than Linux, so there is the learning thing, which I'm at the very beginning of.

The next release = alpha 7, which will have [***_ZFS_***]("http://www.opensolaris.org/os/community/zfs/") support, which will be really very very interesting.

There are currently 12,207 packages in the [***_Nexenta apt repository_***]("http://www.gnusolaris.org/archive/elatte-unstable/newpkg_main")!!!  That number is growing by the hour too...

I think that the [***_ZFS_***]("http://www.opensolaris.org/os/community/zfs/") in particular makes [***_Nexenta_***]("http://www.gnusolaris.org/gswiki/Nexenta_OS") one to keep an eye on.

---

### Post by jazzman83 on 2007-04-13
> **handy said:**
> I've just installed [***_Nexenta_***]("http://www.gnusolaris.org/gswiki/Nexenta_OS"), it looks like Ubuntu, even brown! :)

Yeah, I looked at it earlier and was surprised at the similarity with Ubuntu.  It looks to me as a direct port of Ubuntu on a Unix OS.  

I have been looking around a bit more and am now thinking on giving Arch Linux a try.  I like the idea of being able to completely customize my system and it also seems to have much greater 64-bit usability than Ubuntu does.

---

### Post by handy on 2007-04-13
> **jazzman83 said:**
> Yeah, I looked at it earlier and was surprised at the similarity with Ubuntu.  It looks to me as a direct port of Ubuntu on a Unix OS.  

I have been looking around a bit more and am now thinking on giving Arch Linux a try.  I like the idea of being able to completely customize my system and it also seems to have much greater 64-bit usability than Ubuntu does.

Yep, they state on the Nexenta web site:

***We use Debian/Ubuntu - one of the best existing software distribution/packaging mechanisms - to glue the numerous pieces together.***

Good luck with all the customizing, I couldn't really be bothered anymore... :)

---

### Post by mips on 2007-04-13
> **handy said:**
> 

I think that the [***_ZFS_***]("http://www.opensolaris.org/os/community/zfs/") in particular makes [***_Nexenta_***]("http://www.gnusolaris.org/gswiki/Nexenta_OS") one to keep an eye on.


I just wish they would release ZFS under the GPL or BSD license. Many people have hangups about the current CDDL license.

---

### Post by handy on 2007-04-13
> **mips said:**
> I just wish they would release ZFS under the GPL or BSD license. Many people have hangups about the current CDDL license.

Can you expand on that please Mips?

---

### Post by handy on 2007-04-16
I just installed Solaris, (it finally arrived :D )

I've only had a brief look at it at this stage, it certainly presents very professionally.

My internet doesn't work, so I will have to do some research on that one.  Unless anyone knows the tricks? :)

---

### Post by igknighted on 2007-04-16
> **handy said:**
> I just installed Solaris, (it finally arrived :D )

I've only had a brief look at it at this stage, it certainly presents very professionally.

My internet doesn't work, so I will have to do some research on that one.  Unless anyone knows the tricks? :)

I never got mine working with the official Solaris10.  However opensolaris, in the form of Belenix and Nexenta (think Ubuntu with the solaris kernel instead of linux... human theme and all).  It's the official one that I want though, cause of the java tools... grr.

---

### Post by handy on 2007-04-16
> **igknighted said:**
> I never got mine working with the official Solaris10.  However opensolaris, in the form of Belenix and Nexenta (think Ubuntu with the solaris kernel instead of linux... human theme and all).  It's the official one that I want though, cause of the java tools... grr.

You had hardware support issues I guess?

---

### Post by dca on 2007-04-17
Hmmm, same thing a while ago.  Nexenta installed fine on my laptop but when I got those freebie CDs from Sun (containing Solaris10) hardly anything worked.  The pain was even the integrated network card (Broadcom) required a separate driver.  
 
Solaris is still mainly a server platform known for stability.  I don't see them making any head-way in the desktop market anytime soon.
 
They also did a good job on the virualization end by their use of containers, but according to this article they're going to incorporate Xen into the mix -- - -http://searchdatacenter.techtarget.com/originalContent/0,289142,sid80_gci1196868,00.html

---

### Post by aamukahvi on 2007-04-18
I just got my OpenSolaris DVD in mail (for free). Haven't tried it yet.

---

### Post by handy on 2007-04-25
Solaris is just a bit too *sterile* for me...

I guess I like the life of the Ubuntu community more than a corporate laboratory. :guitar:

---

### Post by Pobega on 2007-04-25
I just got my Solaris CD, I'm going to install it later tonight, I'll report back later tonight.

---

### Post by cantormath on 2007-04-25
> **jazzman83 said:**
> This is just an information post.  I am have been intrigued about using Solaris for a while now but I know very little about it.  I was wondering if I could have some feedback on using Solaris.

I use my computer for both work and home purposes.  I use a variety of programs such as Matlab, Pro/E, Latex, various graphic programs and program with C++.  I was wondering if it made any sense at all someone like me trying out Solaris or any other OS for that matter.  I do most of my work now on Ubuntu - except for the Windows programs of Pro/E and Matlab.

Any info on Solaris in general would also be welcome. Thanks

Solaris 10 rocks

---

### Post by H264 on 2007-04-25
> **handy said:**
> Can you expand on that please Mips?

ZFS would be the Only reason I would want to use Solaris.

ZFS is a new file system made largely by Sun Microsystems... for more info visit:
[http://en.wikipedia.org/wiki/ZFS](http://en.wikipedia.org/wiki/ZFS)
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

As you can see, it is basically the best out there. Now as the other person was saying that basically the licenses prevent Linux devs from including ZFS support in the kernel.
However there is a FUSE port that is being worked on, which sorda side steps the license junk.
[http://zfs-on-fuse.blogspot.com/](http://zfs-on-fuse.blogspot.com/) has more in detail.
[https://developer.berlios.de/project/showfiles.php?group_id=6836](https://developer.berlios.de/project/showfiles.php?group_id=6836) is the actual project.

Now from what I understand a FUSE based file system implementation is going to be slower in general, but I have no idea how much, if at all.

ZFS would be nice to have :D

---

### Post by mips on 2007-04-25
> **H264 said:**
> ZFS would be the Only reason I would want to use Solaris.

ZFS is a new file system made largely by Sun Microsystems... for more info visit:
[http://en.wikipedia.org/wiki/ZFS](http://en.wikipedia.org/wiki/ZFS)
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

As you can see, it is basically the best out there. Now as the other person was saying that basically the licenses prevent Linux devs from including ZFS support in the kernel.
However there is a FUSE port that is being worked on, which sorda side steps the license junk.
[http://zfs-on-fuse.blogspot.com/](http://zfs-on-fuse.blogspot.com/) has more in detail.
[https://developer.berlios.de/project/showfiles.php?group_id=6836](https://developer.berlios.de/project/showfiles.php?group_id=6836) is the actual project.

Now from what I understand a FUSE based file system implementation is going to be slower in general, but I have no idea how much, if at all.

ZFS would be nice to have :D

Thing I don't understand is that FreeBSD is incorporating ZFS. How does that work as the BSD license is more strict than the GPL

---

### Post by Hex_Mandos on 2007-04-25
No, the BSD license is MUCH looser than the GPL. They can incorporate proprietary bits without any problem.

---

### Post by H264 on 2007-04-25
> **Hex_Mandos said:**
> No, the BSD license is MUCH looser than the GPL. They can incorporate proprietary bits without any problem.

Yeah, [http://zfs-on-fuse.blogspot.com/](http://zfs-on-fuse.blogspot.com/) covers the topic briefly.

---

### Post by jinx099 on 2007-04-25
I really hope Sun releases ZFS upder GPL also.  I tried ZFS-FUSE and it was terribly slow.

---

### Post by handy on 2007-04-25
Hopefully the Haiku OS will make it to a pleasing reality.  It's new filesystem sounds amazing too.  I only know about it from what the dev's said in [***_the video..._***]("http://video.google.com/videoplay?docid=236331448076587879")

---

### Post by mrfelker on 2007-04-26
In fact my Internet connection didn't work - EXCEPT in VMware - where I'll use openSUSE 10 Dev Edition.  It's FDISK utility basically sucks.  Wanted to install to an extended partition with RAID volume-  nonono Soalris.  I will tryi FreeBSD (Desktop BSD isn't quite ready).

---

### Post by H264 on 2007-04-27
> **jinx099 said:**
> I really hope Sun releases ZFS upder GPL also.

I hope so too!

I don't think it would be too far off for them to do so as well... esp. after releasing the source code for Java.

---

### Post by RAV TUX on 2007-04-27
> **handy said:**
> Hopefully the Haiku OS will make it to a pleasing reality.  It's new filesystem sounds amazing too.  I only know about it from what the dev's said in [***_the video..._***]("http://video.google.com/videoplay?docid=236331448076587879")

still waiting for an iso, from Haiku....I look forward to having Haiku as an option over Linux and BSD.

on the Solaris side I tried an install of Nexenta....install was fine but could not get it to boot.

---

### Post by handy on 2007-04-27
> **RAV TUX said:**
> still waiting for an iso, from Haiku....I look forward to having Haiku as an option over Linux and BSD.

on the Solaris side I tried an install of Nexenta....install was fine but could not get it to boot.

Yep, I'm with you all the way re. Haiku.

Nexenta booted on my old Asus-A7N266-VM, it was interesting. At Alpha-6, it has a long way to go, seems to be moving fast though.  I don't know how much support is coming directly from Sun?  I'm also not quite sure what I think about Sun either?  I tend to prefer the ocean to have lots of little fish...

I find DreamLinux to be very interesting... :)

---

### Post by RAV TUX on 2007-04-28
> **handy said:**
> Yep, I'm with you all the way re. Haiku.

Nexenta booted on my old Asus-A7N266-VM, it was interesting. At Alpha-6, it has a long way to go, seems to be moving fast though.  I don't know how much support is coming directly from Sun?  I'm also not quite sure what I think about Sun either?  I tend to prefer the ocean to have lots of little fish...

I find DreamLinux to be very interesting... :)Dreamlinux is nice, as far as Debian based derivatives I am most impressed with NepaLinux and elive.

I have used Solaris and I find it not very exciting as it is stable,....I do like that Opera works beautifully in Solaris.

---

### Post by handy on 2007-04-28
> **RAV TUX said:**
> Dreamlinux is nice, as far as Debian based derivatives I am most impressed with NepaLinux and elive.

I have used Solaris and I find it not very exciting as it is stable,....I do like that Opera works beautifully in Solaris.

I may have a language problem with NapaLinux I think... :)  

Great that it has been created though.

---

### Post by 3rdalbum on 2007-04-28
Nexenta and Sabayon were the only two Linux/Unixes that didn't work properly on my hardware. Nexenta was extremely slow.

However, I did try Belenix, and I must say that it's quite a nice distro. If I had a clue what I was doing in Solaris, I'd possibly install it.

---

