---
title: "OpenSolaris is a huge disappointment"
date: 2008-06-07
forum: Other OS Talk
---

### Post by init1 on 2008-06-07
I tried out the OpenSolaris live CD today, and found it to be completely useless on my laptop. 
First Boot
The first thing I did was open Firefox. After half an hour, it still had not completely loaded. I then forced it off with the power button.

Second Boot
The second time, I went straight to the installer. My only free partition was  in an extended partition, which the installer doesn't support. I then had to reboot and repartition.

Third Boot
I tried the installer again. After an hour it was still installing. So I came back a few hours later and found that the installation had failed. 

The only thing that the installer did was mess up grub and change the partition type of one of my partitions to solaris.

---

### Post by LaRoza on 2008-06-07
Running a live cd on a laptop is usually prone to errors.

If you have suitable, it works very, very well as a live disk.

---

### Post by SunnyRabbiera on 2008-06-07
well solaris is coming into its own though, once it has better intel support it will be much better.

---

### Post by kk0sse54 on 2008-06-07
OpenSolaris I find has horrible hardware support but if you can get it running it's quite good.

---

### Post by izanbardprince on 2008-06-08
I tried the OpenSolaris 2008/5 disc, both on my new Gateway GM5446E and my old Compaq Presario v2608wm (circa 2005), and it would not work right out of the box on any of them, and just was not possible to fix, so the moral of the story is what the OP said, stay away from it.

It also is quite slow compared to Linux, this is especially true on uniprocessor systems with 1 GB of RAM or less, where Ubuntu does well considering, I mentioned this to a dev and he said "Solaris scales up, not down", even though allowing you to use something other than ZFS (CPU hog) for the filesystem would fix a lot of that.

Solaris developers are arrogant, even by Unix hacker standards, and I highly doubt Slowlaris will be any kind of a threat to Linux if they can't do any better than this with all of Sun's resources behind them.

---

### Post by zmjjmz on 2008-06-08
No Open Source OS is a threat to any other Open Source OS.
I've tried BeleniX (based on OpenSolaris) on some computers...
well thanks for royally screwing up my USB flash drive. (It's fine now)
The USB installer wouldn't work, on any computer, and eventually I gave up and figured I'll just buy a SPARC box and put it on there :P
It's still in the early stages of development though (they had their first stable release only recently), so there's no way of telling how far it'll get in 15 years.

---

### Post by perlluver on 2008-06-08
I tried it and all I got out of the deal was a dead CD-Burner, after about an hour I found it had killed my CD-Burner at 38 percent.  Needles to say I haven't tried it again.

---

### Post by pastormick on 2008-06-08
OpenSolaris worked like a champ an my T61 - and it even worked on an old eMachines m5113. The only thing I didn't take into account is that when putting it on a test partition, it has to be the LAST partition because it will nuke everything after it! Oh well; I wanted to do a fresh install and test my backups anyway...

If OpenSolaris runs like a dog for you, why not give [Nexenta]("http://www.nexenta.org/os") a shot?

---

### Post by digger95 on 2008-06-08
> **perlluver said:**
> I tried it and all I got out of the deal was a dead CD-Burner, after about an hour I found it had killed my CD-Burner at 38 percent.  Needles to say I haven't tried it again.
I can sympathize.  It didn't kill my burner, but it made noises I've *never* heard before out of a cd drive.  At the very least that OpenSolaris cd put some major wear and tear on my drive.  I regret even trying it.

---

### Post by LaRoza on 2008-06-08
Well, I used it as a live cd for several hours, and had flash and all hardware working very easily.

---

### Post by Midwest-Linux on 2008-06-08
Thanks for the warning. You saved me a couple of hours of whatever time I have for these projects from the downloading the distro, attempting installation, trying to make it work, and ending it up wiping it from my hard drive. Nothing more I hate is spending hours or days in trying to get something to work only to have to wipe it from the hard drive.

---

### Post by 3rdalbum on 2008-06-08
I got my CD a little while ago. It wouldn't boot up on my primary computer and I didn't know what kernel options to give it for greater compatibility (the usual Linux ones weren't recognised). So I tried my slightly-older Compaq. Solaris recognised everything except the disused Winmodem. Actually, it recognised my printer, but didn't have a driver. The Java-based printer setup program scared me, and I didn't check out CUPS.

There's really not very much preinstalled on the disc. I mean, it's a whole CD. No Openoffice.org, which is a huge surprise considering Sun is the biggest sponsor of OOo.

The package manager also didn't seem to work. It took a long time to start up, and a long time to pretend to install MP3 codecs, and then wouldn't start again. I was running from the live CD; maybe OpenSolaris doesn't have any sort of UnionFS or anything like that, so no writable filesystem?

I did end off feeling like "What's the point?".

---

### Post by karellen on 2008-06-08
why get through the pain of trying something else, waste time and patience, when your Linux install just works?

---

### Post by LaRoza on 2008-06-08
> **karellen said:**
> why get through the pain of trying something else, waste time and patience, when your Linux install just works?

...because it just works.

---

### Post by Sef on 2008-06-08
It worked fine on my desktop.   The only thing I have to figure out is how to stream music.

---

### Post by Istonian on 2008-06-09
OpenSolaris does not like my hardware at all. I can't get to the live cd at all. It gives me an error message.

---

### Post by ibutho on 2008-06-09
I tried it a few weeks ago and it worked fine on my laptop and desktop except for the fact that it did not support any of my network interface cards (which work out of the box with Linux, FreeBSD and NetBSD). It seems like at the moment hardware support is not very good.

---

### Post by n8ek on 2008-06-10
I just installed it on my packard bell h5535 notebook and wireless worked out of the box but surfing the web is like being on dial up and getting the package manager to run is a no go it just wont play ball, 1 thing i cant find is how to re-start the only option i have is to shut down, what ashame the install was idiot proof it looks good,runs good, just cant update or re-start  and wireless is at a crawl, 
maybe a new install to see if it is the OS or a bad install due to a faulty burn/disk will help iron out the above probs?

---

### Post by Octagonal on 2008-06-10
Tried it.  OpenSolaris didn't recognize my audio device.  I used a pretty standard PC--a Dell Optiplex 745.  Also, I couldn't get conky to work as it's not supported with solaris which was the deal breaker for me ;)

---

### Post by init1 on 2008-06-10
Glad to see I'm not the only one who can't run it.

---

### Post by diskotek on 2008-06-17
very strange for my computer but it worked GREAT for my box. actually i could never run ubuntu live cd with my ati radeon x200 but opensolaris 2008.5 works really great. hardware support is great also. 

but, it just look like ubuntu fork :) i couldn't see any difference.

when i can success to screw up my ubuntu hardy heron, i'll install it.. but it seem impossible for now :D

but again great work!

---

### Post by Lupgaru on 2008-06-19
I agree fully with the disappointment. I have tried the Live CD 3 times on different(recent computers) First with XP on a dual boot, wiped out XP, did not find my wireless or dialup nor other hardware. Same with Vista on a brand new Desktop. The Ubuntu install did dual boot but still very little hardware recognition. And again no Internet connection.
    Installation all 3 times was painfully slow with several failures. I just gave it up and tried out a few other Operating Systems with no problems. Still run Ubuntu primarily, mostly for the hardware recognition over several others.

---

### Post by babylon2233 on 2008-06-20
> **diskotek said:**
> . 

but, it just look like ubuntu fork



Well, it not even a Linux distro.

---

### Post by ibutho on 2008-06-20
> **babylon2233 said:**
> Well, it not even a Linux distro.

Its definitely not a Linx distro, but they way they setup GNOME mimics the default Ubuntu GNOME desktop.

---

### Post by techmarks on 2008-06-20
Interesting project.

Not trying it anytime soon, but it will improve.

I must say one thing Sun released  this OS under a good license.

Much better than GPL, I'm not the great fan of GPL.

GPL is unfriendly to binary only and commercial software
or licenses not pure GPL.

By releasing under a license not GPL Sun has differentiated 
the OpenSolaris, and not just by claiming the derivation from
System V Unix (it's not a very big deal, as Linux is such a 
solid OS, even without the direct Unix history, so who cares
much)

There's very little reason to change to the very new OpenSolaris
right now, but with the good license and if it becomes
stable, could be a good choice development OS.

---

### Post by init1 on 2008-06-22
> **ibutho said:**
> Its definitely not a Linx distro, but they way they setup GNOME mimics the default Ubuntu GNOME desktop.
Yeah OpenSolaris looked very nice. It just didn't run too well. Hopefully they'll have a really great OS in a few years.

---

### Post by Ptero-4 on 2008-06-25
A few questions:

Will it recognize my rtl8187b wifi?

Can I install other DE's on it (and remove gnome)?

Does it have a proper bootsplash (someone said it have in a review, but other solaris systems didn't have)?

---

### Post by cardinals_fan on 2008-06-25
> **Ptero-4 said:**
> A few questions:

Will it recognize my rtl8187b wifi?

Can I install other DE's on it (and remove gnome)?

Does it have a proper bootsplash (someone said it have in a review, but other solaris systems didn't have)?
1. Doubtful, hardware support is awful.  But I haven't done any research, so check before writing it off.

2. If you can get an internet connection to install them with.

3. I think so, but I can't remember for sure.  Does this actually matter?!

---

### Post by Ptero-4 on 2008-06-26
About the bootsplash, I was just curious.

Also I forgot to ask.

How fast it is (got a Pentium Dual-Core at 1.6GHz)?
How much will it consume battery-wise (under vista the battery gives 3hrs)?
And is it better or worse than linux in the load_cycle HD thingie that seems to affect some systems that run ubuntu?

---

### Post by init1 on 2008-06-26
> **Ptero-4 said:**
> About the bootsplash, I was just curious.

Also I forgot to ask.

How fast it is (got a Pentium Dual-Core at 1.6GHz)?
How much will it consume battery-wise (under vista the battery gives 3hrs)?
And is it better or worse than linux in the load_cycle HD thingie that seems to affect some systems that run ubuntu?
On my computer (1.5Ghz) the live CD was painfully slow, too slow to be usable. That's probably just because of hardware issues though.

---

### Post by dca on 2008-06-26
It's Sun's first open release.  The nice thing is on the desktop is a driver utility dealie that indicates which hardware is not working and requires external driver...
 
I mean what the heck, it has a battle-hardened kernel & a default file system superior to ext3 & ReiserFS.
 
Other than that their license is poo.  Resulting in the best of both worlds not being able to join together.  Why not, it's better to have thousands of contributors (linux kernel devs) versus twenty or so (Solaris Unix kernel) developers...

---

### Post by cardinals_fan on 2008-06-26
> **dca said:**
> It's Sun's first open release.  The nice thing is on the desktop is a driver utility dealie that indicates which hardware is not working and requires external driver...
 
I mean what the heck, it has a battle-hardened kernel & a default file system superior to ext3 & ReiserFS.
 
Other than that their license is poo.  Resulting in the best of both worlds not being able to join together.  Why not, it's better to have thousands of contributors (linux kernel devs) versus twenty or so (Solaris Unix kernel) developers...
1. ...except that it doesn't list the only hardware that caused me issues (my wireless adapter) as having any problems.

2. Right on.

3. What?  OpenSolaris is OPEN SOURCE!  The only [non-technical] reason ZFS can't be ported to Linux (at the moment) is because the ***GPL*** refuses to accept it.

---

### Post by jmoore on 2008-07-05
I had the same issue when I tried to run the OS on a non-supported platform.  Here is a list of supported/certified platforms you should check:
 [http://www.sun.com/bigadmin/hcl/data/os/systems/views/all_desktops_all_results.page1.html](http://www.sun.com/bigadmin/hcl/data/os/systems/views/all_desktops_all_results.page1.html)


Best Regards.

---

