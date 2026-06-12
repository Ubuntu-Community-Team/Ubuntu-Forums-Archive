---
title: "Freespire and PCLinux won't install. :("
date: 2007-02-12
forum: Other OS Talk
---

### Post by Ryupower on 2007-02-12
Hey there guys, I downloaded both distos and I wasted like, 3 or 4 CD's on EACH thinking it'd be just some bad burn.- None of them worked.
-I checksummed the ISOS, it said by both are correct.
- I burnt them in various speeds, thinking it'd be a bad burn. They all didn't work.
- I redownloaded them, thinking it's just a bad download, checksum was fine, burnt them, still didn't seem to work.

I don't know what to do! I tried that all, and all I ever get is the GRUB command thingy. But nothing else...am I supposed to get the GRUB commandline or something?

---

### Post by lbyrd33 on 2007-02-12
I downloaded freespire a while back and I remember that it loaded up fine without any commands. Did you try downloading at a really slow speed because some of these really compressed iso's need to be burned either on a really good burner or a really slow speed.

---

### Post by Adamant1988 on 2007-02-12
> **Ryupower said:**
> Hey there guys, I downloaded both distos and I wasted like, 3 or 4 CD's on EACH thinking it'd be just some bad burn.- None of them worked.
-I checksummed the ISOS, it said by both are correct.
- I burnt them in various speeds, thinking it'd be a bad burn. They all didn't work.
- I redownloaded them, thinking it's just a bad download, checksum was fine, burnt them, still didn't seem to work.

I don't know what to do! I tried that all, and all I ever get is the GRUB command thingy. But nothing else...am I supposed to get the GRUB commandline or something?

For Freespire you'll be brought to the grub selection menu... you select either Install (the default I believe) or Freespire Live! 

For PClinuxOS I think it defaults to the liveCD so that is a bit confusing.

---

### Post by Ryupower on 2007-02-12
> **Adamant1988 said:**
> For Freespire you'll be brought to the grub selection menu... you select either Install (the default I believe) or Freespire Live! 

For PClinuxOS I think it defaults to the liveCD so that is a bit confusing.

I have no install option,
just a grub command prompt...:(

Also, yes I burnt them at slow speeds, down to 4x even...

HELP! PWEASE! >.<

---

### Post by RAV TUX on 2007-02-13
> **Ryupower said:**
> Hey there guys, I downloaded both distos and I wasted like, 3 or 4 CD's on EACH thinking it'd be just some bad burn.- None of them worked.
-I checksummed the ISOS, it said by both are correct.
- I burnt them in various speeds, thinking it'd be a bad burn. They all didn't work.
- I redownloaded them, thinking it's just a bad download, checksum was fine, burnt them, still didn't seem to work.

I don't know what to do! I tried that all, and all I ever get is the GRUB command thingy. But nothing else...am I supposed to get the GRUB commandline or something?

> **Ryupower said:**
> I have no install option,
just a grub command prompt...:(

Also, yes I burnt them at slow speeds, down to 4x even...

HELP! PWEASE! >.<

Have you ever booted any live CD on this computer before?

if its any consultation I have never been able to boot PCLinuxOS on my computer either, and I have tested over 200 distros...I believe it may be something to do with PCLinuxOS lack of good hardware detection, thus the reason for unreliability....

I have never tried Linspire

If you have never booted any Linux CD/DVD before it may have more to do with your SATA Manager &/or RAID settings....

if not it may be your choice of distros, I suggest you first try KNOPPIX.

and please post your results

what are you using to burn with and at what exact speed?

---

### Post by Ryupower on 2007-02-13
> **RAV TUX said:**
> Have you ever booted any live CD on this computer before?

if its any consultation I have never been able to boot PCLinuxOS on my computer either, and I have tested over 200 distros...I believe it may be something to do with PCLinuxOS lack of good hardware detection, thus the reason for unreliability....

I have never tried Linspire

If you have never booted any Linux CD/DVD before it may have more to do with your SATA Manager &/or RAID settings....

if not it may be your choice of distros, I suggest you first try KNOPPIX.

and please post your results

what are you using to burn with and at what exact speed?

Yeah, I tried liveCD's before, -that's why I'm using Ubuntu! ( and my favourite Linux so far. ^^ )

So
I used two different burners
Nero
and
k3b ( which allowed me to checksum it, claiming it's fine.. )

I burnt them mainly with 4x and 16x...

btw: WOW, I didn't even know there ARE 200 distros..o.o

---

### Post by RAV TUX on 2007-02-13
> **Ryupower said:**
> 

btw: WOW, I didn't even know there ARE 200 distros..o.oThere are probably over 600 at the very least, buts whose counting, there are more I have not tried:)

---

### Post by Ryupower on 2007-02-14
ALSO, I prefer not to use knoppix, - my dad tried it before. It had horrible hardware detection  in those days.
Hey, since I'm having this issue with the distros not booting from liveCD,  can you help me find the right distro? ( since there are well over 200 I see...o.o maybe even 600 :O )

I'd like one that: 
- has good hardware detection ( it needs to have my wireless working )
- uses KDE ( I want to try it )
- Uses RPM's ( since the kde's I tried can't install debian packages for some reason )
- Is NOT (Open) SuSE.

thanks in advance :)

---

### Post by RAV TUX on 2007-02-14
> **Ryupower said:**
> ALSO, I prefer not to use knoppix, - my dad tried it before. It had horrible hardware detection  in those days.
Hey, since I'm having this issue with the distros not booting from liveCD,  can you help me find the right distro? ( since there are well over 200 I see...o.o maybe even 600 :O )

I'd like one that: 
- has good hardware detection ( it needs to have my wireless working )
- uses KDE ( I want to try it )
- Uses RPM's ( since the kde's I tried can't install debian packages for some reason )
- Is NOT (Open) SuSE.

thanks in advance :)

try Sabayon.

---

### Post by Ryupower on 2007-02-14
> **RAV TUX said:**
> try Sabayon.

Sabayon? 

Cool name too! :D

I'll look into it...thanks. ^^

---

### Post by Ryupower on 2007-02-14
BTW: awww...the download mirrors are down...:(

could you suggest another good one that's RPM based, KDE, and has good hardware detection ( besides SuSE? ). It doesn't necessarily have to be a liveCD. :)

---

### Post by RAV TUX on 2007-02-14
> **Ryupower said:**
> Sabayon? 

Cool name too! :D

I'll look into it...thanks. ^^

> **Ryupower said:**
> BTW: awww...the download mirrors are down...:(

could you suggest another good one that's RPM based, KDE, and has good hardware detection ( besides SuSE? ). It doesn't necessarily have to be a liveCD. :)

hmm perhaps [**StartCom**]("http://www.startcom.org/")

btw download the Sabayon Torrents here:
[http://linuxtracker.org/torrents-search.php?search=sabayon](http://linuxtracker.org/torrents-search.php?search=sabayon)

the most up to date versions are hear:

[http://linuxtracker.org/torrents-details.php?id=3406](http://linuxtracker.org/torrents-details.php?id=3406)
[http://linuxtracker.org/torrents-details.php?id=3407](http://linuxtracker.org/torrents-details.php?id=3407)

---

### Post by Ryupower on 2007-02-15
Thank you. :)

---

### Post by Hendrixski on 2007-02-15
are you sure you downloaded the CD for the correct architecture?

---

### Post by igknighted on 2007-02-15
Berry Linux is based on Fedora and uses KDE, I just downloaded the iso but havent tried it yet.  Also, you can install KDE on top of a normal Fedora install as well.  You might also try Mandriva, there are some decent versions of that as well, although I'd stick with Fedora/Berry (then again, I'm a little biased there).

I wouldn't blame the Debian based distro's failures on the package manager, you might want to give the new Mepis a chance.  Also, I know PCLOS failed you before, but a lot of people claim it is the most user friendly RPM based distro there is, so you might want to give test 2 that just came out today (or the final whenever it comes out) another shot.

PS, if your knock against Suse is the novell/MS deal... wow we are all petty... I don't like the deal either, but suse is 100% free and developed by the community, and they are one of the leading innovators in linux.  If you boycott Suse then boycott XGL and compiz (and by extension beryl) because those are Novell sponsored projects too.  Besides, its WAY too early to see what the deal is going to mean anyway, so lets everybody chill out.

---

### Post by RAV TUX on 2007-02-15
> **igknighted said:**
> Berry Linux is based on Fedora and uses KDE, I just downloaded the iso but havent tried it yet.  Also, you can install KDE on top of a normal Fedora install as well.  You might also try Mandriva, there are some decent versions of that as well, although I'd stick with Fedora/Berry (then again, I'm a little biased there).

I wouldn't blame the Debian based distro's failures on the package manager, you might want to give the new Mepis a chance.  Also, I know PCLOS failed you before, but a lot of people claim it is the most user friendly RPM based distro there is, so you might want to give test 2 that just came out today (or the final whenever it comes out) another shot.

PS, if your knock against Suse is the novell/MS deal... wow we are all petty... I don't like the deal either, but suse is 100% free and developed by the community, and they are one of the leading innovators in linux.  If you boycott Suse then boycott XGL and compiz (and by extension beryl) because those are Novell sponsored projects too.  Besides, its WAY too early to see what the deal is going to mean anyway, so lets everybody chill out.Berry Linux is actually very nice.

---

