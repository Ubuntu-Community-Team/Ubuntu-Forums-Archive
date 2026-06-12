---
title: "dual-booting Ubuntu 12.04 and Windows 7"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by Aeonis on 2013-01-03
Per suggestion, I am creating a post for this.  I've been running Windows 7 for my home stuff.  My wife has her computer now, so I can go back to full blown Linux, which is perfect timing since my drive was wiped.

Long story short, I had to rebuild my pc as well and ended up going with Ubuntu 12.04 LTS.  I was in process of installing StarCraft II and then read some posts where Linux users were getting banned for "cheating".  No proof has been brought forward, but it seems Blizzard isn't supporting gamers that use Linux.

Before anyone jumps on the "just boycott Blizzard" train, no.  I really enjoy playing Starcraft II.  Their other games are neat, but that's my game that I enjoy the most as far as RTS goes.

I have 2 hard drives in my system.  My second drive was pretty much for storage.  I have one that is a Seagate Momentus XT that's about 250 GB that has Ubuntu on it.  I read an article that said to install Windows 7 first and then install Ubuntu.  I wanted to see if I should lose all the work I did setting it up to do it this way and then install Ubuntu 12.04 afterwards.

I don't mind doing this, but I think the key for Win 7 I have is for the x86 build and that would limit the OS (to my understanding) to only seeing about 4 GB of the 8 GB that's installed.

What would you guys suggest?

---

### Post by cariboo on 2013-01-03
The first thing you should do is make a backup of your /home directory. Then Windows needs a 200MiB boot partition installed at the start of the drive. This partition is created automagically during the install process. I'd suggest you set the Win 7 partition to about half of the total size of the hard drive, and leave the rest of the drive unpartitioned, as Ubuntu will partition the empty space correctly during the install process.

Unfortunately the only way you are going to get Windows to see above 4GiB is to purchase a copy of 64-bit Windows 7.

---

### Post by Mark Phelps on 2013-01-04
Sorry ... but Win7 does not REQUIRE a boot partition.  That's created automatically when Win7 is installed on a BLANK drive.

If you create an NTFS partition, Win7 will install in that -- just be sure to REFORMAT the partition as part of the installation.

---

### Post by Fahim Abdun-Nur on 2013-01-04
Another alternative would be install Win7 in a virtualbox VM... (or the other way round with ubuntu in a VM; but I get the feeling you are planning to use linux more often)

---

### Post by mastablasta on 2013-01-04
> **Aeonis said:**
>  
Long story short, I had to rebuild my pc as well and ended up going with Ubuntu 12.04 LTS. I was in process of installing StarCraft II and then read some posts where Linux users were getting banned for "cheating". No proof has been brought forward, but it seems Blizzard isn't supporting gamers that use Linux.
 
 
that was for Diablo 3 and Blizzard admitted it's mistake and gave accounts back i believe.
[http://www.cinemablend.com/games/Blizzard-Admits-Linux-User-Was-Wrongly-Banned-Offers-Refund-49339.html](http://www.cinemablend.com/games/Blizzard-Admits-Linux-User-Was-Wrongly-Banned-Offers-Refund-49339.html)
 
[http://www.cinemablend.com/games/Blizzard-Re-Review-Banned-Diablo-3-Linux-Accounts-Request-49431.html](http://www.cinemablend.com/games/Blizzard-Re-Review-Banned-Diablo-3-Linux-Accounts-Request-49431.html)

---

### Post by Aeonis on 2013-01-04
@mastablasta:  Your name reminds me of a game I used to play back on NES called "Blaster Master".

I called Blizzard yesterday and talked to a gentleman and he reported that they only see games where there is an unfair advantage given by a third party software and ban the account that was using it.  Wine wasn't considered a "third party software" and he understood that it needed to be used to run.  Very nice guy.

@Fahim:  Yes, I'd love to use Ubuntu more.  I used to use it as my primary OS, but my wife has these little games you get for $10 at Wal-Mart that Wine, PlayOnLinux, and a VM wouldn't run.  For some reason, some video plugin wouldn't cross over and I couldn't get those games to work.  Everything else did.  When I ran StarCraft through a VM, I could only use it at the lowest settings even though I was running a heck of a machine.  I gave my VM a ton of resources and it still ran like crap.  So I bought us a copy of Win 7 and installed it.  Now, she has her own laptop, so I want to get back into using Linux and getting more comfortable in it.

---

