---
title: "Is ubuntu the right OS if I want to use my laptop as a MP3 music player?"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by Malmberg on 2013-03-21
Gents,
The "Newbie" is lost :-)
I’m trying to configure my old HP laptop with Ubuntu 12.04 so I can use Rhythmbox as a "music player". I have a Win7 HP server in my basement, that holds +50.000 MP3 files.
Mounted through Samba, Rhythmbox did create a library, it took forever - but eventually I could see my music. 
But,I can't play it - the progress bar is moving - but no sound at all - just some 2 sec electronic noise, when I press play?
Should I revert to Win7, I would hate it - or go for another Linux flavour?

Btw - It use to work under version 10.xx :-) - I could just downgrade!!

Cheers

---

### Post by ManamiVixen on 2013-03-21
You need to install ubuntu-restricted-extras package "sudo apt-get install ubuntu-restricted-extras"

---

### Post by DuckHook on 2013-03-21
MP3 is a problematic codec for adherents of free and open source software (FOSS) because it contains code with copyrights antithetical to the tenets of the FOSS movement. Ubuntu gets around this by simply segregating such stuff onto an add-on repository so that you have to make a conscious decision to install it (i.e. you actually have to initiate and accept the responsibility of "tainting" your install). You will have to make sure that your software sources include "multiverse" and then do as per @ManamiVixen's instructions. You may wonder whether anyone refrains from using MP3, but many Linux purists store their music files as Ogg Vorbis, which does not have the same copyright problems.

To make sure multiverse is available: In Update Manager>Settings>Ubuntu Software make sure "Software restricted by copyright or legal issues (multiverse)" is checked. While there, it is a good idea to make sure "universe" and "restricted" are checked as well, and make sure "Installable from CD-ROM/DVD" is ***not*** checked.

---

### Post by sudodus on 2013-03-21
You may also need to tweak the audio settings. In standard Ubuntu 12.04 LTS you find it via the system settings

or directly via the terminal command
```
 gnome-control-center sound-nua
```

---

### Post by Malmberg on 2013-03-22
Hi,
@[**[COLOR=#000000]ManamiVixen[/COLOR]**]("http://ubuntuforums.org/member.php?u=1777813"): I have installed this extra package, see below :-)

@[**[COLOR=#000000]DuckHook[/COLOR]**]("http://ubuntuforums.org/member.php?u=1256508"): understood!

@[**[COLOR=#000000]sudodus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1499021"): I have had a look here!

-and, I forgot to mention that I can play all my music - if I use XBMC, so I think it must be related to Rhythmbox???

Cheers

---

### Post by DuckHook on 2013-03-22
> **Malmberg said:**
> ...I can play all my music - if I use XBMC, so I think it must be related to Rhythmbox...

Hmmm. What does dmesg show immediately after trying to run Rhythmbox? Might it have something to do with [this]("http://askubuntu.com/questions/127272/rhythmboxs-not-playing-music-from-network-share")? Is your samba share mounted statically or dynamically? I.e. have you defined a mount point in /mnt (or /media) at boot, or do you rely on gvfs to mount each time system invokes a link? If the latter, you may wish to try the solution contained in my referenced thread. This essentially makes your samba share a permanent mount point so that your system treats it as a local file. If it works, you will have to delete your Rhythmbox database, though, and rebuild it based on the new path.

---

### Post by lykwydchykyn on 2013-03-22
> **DuckHook said:**
> MP3 is a problematic codec for adherents of free and open source software (FOSS) because it contains code with copyrights antithetical to the tenets of the FOSS movement. 

There's also that part about needing a license from MPEG-LA to legally distribute support for MP3 in some countries.

@OP: Have you tried VLC, or any other mp3 players (clementine, amarok, audacious, etc)?  Can your server do UPNP?  This might perform better than Samba.

---

### Post by Malmberg on 2013-03-23
Gents,
I "solved" my problem :-)
I swapped my laptop drive with  a spare 500GB I had - this is big enough to hold my music collection.
So I started from scratch with Ubuntu and so on. I made a shared folder - and my Win7 server is using this as back-up!
And - viola - after a couple of days, Ill have all my music on my laptop!
Thanks for your help!

Cheers
Steen

---

### Post by DuckHook on 2013-03-23
...and this has the added advantage of backing up your music collection. Sometimes brute force solutions are also the best ones. 

Good luck and Happy Ubuntuing!

---

### Post by Malmberg on 2013-03-23
> **DuckHook said:**
> ...and this has the added advantage of backing up your music collection. Sometimes brute force solutions are also the best ones. 

Good luck and Happy Ubuntuing!

Exactly :-)

Thanks

---

