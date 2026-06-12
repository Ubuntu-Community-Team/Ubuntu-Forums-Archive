---
title: "downgrading to 7.10 w/o losing files??"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by lunanueva on 2008-08-01
hello to all,
about two months ago i upgraded to hardy heron and sadly i now regret it.  too many problems have surfaced so i would like to downgrade to gutsy gibbon 7.10, where all was well.  is there a way of downgrading to 7.10 without losing any files???  thanks to all that can help.

---

### Post by dca on 2008-08-01
No, you have to do a fresh install...
 
We're discussing possible upgrade issues in this post:
 
[http://ubuntuforums.org/showthread.php?t=877147](http://ubuntuforums.org/showthread.php?t=877147)
 
 
...seeing as how you have to copy all your personal data off, you might as well try to do a fresh install (wipe the entire drive) w/ the Ubuntu 8.04...  I've noticed many improvements on some of my systems that have newer hardware that never worked in 7.x such as webcam on a laptop and media card reader on a PC...

---

### Post by dca on 2008-08-01
...in other words it's a possibility that some of the issues you're encountering are a side effect of upgrading the OS versus doing a fresh install.

---

### Post by dca on 2008-08-01
One more thing, if you decide to give it a go and try to do a fresh install of 8.04 on your system(s), then let the forum know what issues you encounter or if it's something out of the ordinary file a bug report...

---

### Post by lunanueva on 2008-08-01
after i back up my files, i'll do a fresh heron install, then i'll post my results.  thanks for your help.

---

### Post by lunanueva on 2008-08-04
So, i ran DBAN to clean up the hard drive before i went to bed last night and it was successful, then i tried to do a fresh install of Hardy Heron this morning and this showed up on the screen:

[  31.818575]ACPI: EC:acpi_ec_wait  timeout, status=0, expect_event=1
[  31.818626]ACPI: EC: read timeout, command=128

When i tried to run a 'check' on the Heron disk, this code (i don't know what else to call it) popped up again and locked me out.  

The code showed up for the first time after upgrading to 8.04 from 7.10, right after i restarted my laptop (sony vaio VGN-N320E).  This code showed up sporadically when i would restart my laptop and would lock me out.  The only way i could deal with it was to hard restart my laptop again and go in through safe mode, which was annoying.     

I'm running 7.10 now, which installed successfully after the Heron failure.  Does anyone know why this happened or what that string of code means??

---

### Post by LowSky on 2008-08-04
Hardy has some odd issues. I know from experience as I've used it since Alpha, but I've run Alphas/Betas since 7.04 and Hardy has been the worse Final release I seen yet. For some reason Gutsy would install just fine, but Hardy would not. turned out that it was a bad data cable that Hardy didn't like yet Gutsy didn't mind it. It seems Hardy has a more stringent install then previous versions. I don't know if its me or what but 7.04 was the most stable verison of Ubuntu that I've run. Maybe because it was an improve on LTS? I cant wait for 8.10 hoping its better.

---

### Post by starcannon on 2008-08-04
Your best bet would be to back up all of your important data to an external source, check the source on another computer making sure that it is faithfully represented. Then when you do a fresh install be sure to choose manual partitioning during the install process and create /home on its own partition, in this way you won't have a problem switching around again in the future, or indeed even trying entirely different versions of linux.

Anyway thats how I'd tackle it (and have).

GL

---

### Post by bobnutfield on 2008-08-04
> **LowSky said:**
> Hardy has some odd issues. I know from experience as I've used it since Alpha, but I've run beta since 7.04 and Hardy has been the worse Final release I seen yet. For some reason Gutsy would install just fine, but Hardy would not. turned out that it was a bad data cable that Hardy didn't like yet Gutsy didn't mind it. It seems Hardy has a more stringent install then previous versions. I don't know if its me or what but 7.04 was the most stable verison of Ubuntu that I've run. Maybe because it was an improve on LTS? I cant wait for 8.10 hoping its better.

+1 to these comments.  I,too, started with Hardy in beta and followed through with the updates til the final release.  It has never been as quick or stable as Gutsy was.  I have Hardy on both a laptop and a desktop (completely different hardware) and both still experience a lot of issues.  My laptop is of particular concern because I am still getting the occassional freeze requiring a hard reset and we all know that that can lead to eventual bad sectors on my disk.  I love Ubuntu and will not give up on it.  I, too, am hoping that 8.10 is going to correct these problems, but for now I have to depend on Slackware for a stable system on my laptop (dual boot).

---

### Post by Oldsoldier2003 on 2008-08-04
> **bobnutfield said:**
> +1 to these comments.  I,too, started with Hardy in beta and followed through with the updates til the final release.  It has never been as quick or stable as Gutsy was.  I have Hardy on both a laptop and a desktop (completely different hardware) and both still experience a lot of issues.  My laptop is of particular concern because I am still getting the occassional freeze requiring a hard reset and we all know that that can lead to eventual bad sectors on my disk.  I love Ubuntu and will not give up on it.  I, too, am hoping that 8.10 is going to correct these problems, but for now I have to depend on Slackware for a stable system on my laptop (dual boot).

Although I have had nothing but good experiences with hardy since alpha, I am a firm believer in keeping all data on a separate partition. This helps when sharing data between distros and when doing a upgrade by clean install. I'm not a fan of the shared home directory anymore... 

So I'll say +1 to backing up and verifying your data, then doing a clean install.

---

### Post by bobnutfield on 2008-08-04
> Although I have had nothing but good experiences with hardy since alpha, I am a firm believer in keeping all data on a separate partition. This helps when sharing data between distros and when doing a upgrade by clean install. I'm not a fan of the shared home directory anymore...

So I'll say +1 to backing up and verifying your data, then doing a clean install.

An excellent point....and while I do not share a data or home directory between Ubuntu and Slackware, I DO synchronize by home and data folders between the two.

But, thank you for that.  A shared data folder is going to be my next priority on a fresh install.

---

### Post by galileon on 2008-08-04
> **bobnutfield said:**
> +1 to these comments.  I,too, started with Hardy in beta and followed through with the updates til the final release.  It has never been as quick or stable as Gutsy was.  I have Hardy on both a laptop and a desktop (completely different hardware) and both still experience a lot of issues.  My laptop is of particular concern because I am still getting the occassional freeze requiring a hard reset and we all know that that can lead to eventual bad sectors on my disk.  I love Ubuntu and will not give up on it.  I, too, am hoping that 8.10 is going to correct these problems, but for now I have to depend on Slackware for a stable system on my laptop (dual boot).

+1. Downgraded to Gutsy Gibbon, problems solved.

---

### Post by lunanueva on 2008-08-04
Thanks to all that replied.  I was very hesitant to upgrade to Heron, but I did it anyway hoping that everything would work out.  I never had any problems before that upgrade, but I'm not going to give up on Ubuntu, I like it too damn much.  I too shall wait on 8.10 and hope for the best.  Until then I'm going to stick with good old Gutsy.

---

