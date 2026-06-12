---
title: "[SOLVED] ClamAV package - Stuck between a rock and a hard place"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by kwackher on 2008-09-12
Hey!
I use ClamAV as my primary anti-virus scanner because it's free software, and it works as well as anything else. The problem is, I can no longer download virus signatures because the scanning engine is outdated (I have 0.92.1). I checked their web site and they are no longer allowing outdated scanners to download new signatures, because obsolete scanning engines are incapable of detecting what the current engine can detect, even if the obsolete scanner is referencing new virus database signatures. So they block obsolete scanners because they are just wasting bandwidth. And I can't help but agree with them - why continue serving users running obsolete software with signatures their obsolete software can't use? And at the expense of users who keep their software up-to-date?

So that's one part of why I'm stuck. The second part is the Synaptic Package Manager has the same version of Clam I'm already running - 0.92.1. So I can't update through there. Now, I *could* uninstall it and install the current version from source, edit and troubleshoot the clamd and freshclam.conf files, and then synch it all with clamuko/dazuko and Clamtk. But then I'd have the whole set-up outside of the package manager, so Synaptic could not see it or control it (which could lead to compatibility issues). And I'd have to go through the entire process every time ClamAV released a new engine. 

So I would really, really, really like to stick with Synaptic. But it has 0.92.1. And it won't be updated for another month or so, when the next OS comes out. Until then, I basically can't use one of my favorite open source programs, without going to a whole lot of seemingly needless trouble. 

And I assure you this has nothing to do with protecting my system (it takes care of itself, I just don't give root access/privileges to unsigned, unknown, or otherwise unverified source/code). What this is about is my desire to use an excellent open source program instead of something closed source (F-prot, Avast, etc) to avoid contaminating my Windows-loving friends, and also to improve ClamAV by bringing it to their attention when I find something ClamAV doesn't detect.

So, that's why I say I'm "stuck." Does anybody know who to get in touch with about updating the ClamAV package? I would say it's a security issue. Also ClamAV releases many updates within a six-month time frame, so perhaps it's package should receive extra attention? 

Those are my thoughts. I'd appreciate any advice/input/feedback anyone might have, and also a heartfelt thanks to everyone who puts in their time and money on open source projects. It's always appreciated.

---

### Post by macvr on 2008-09-12
i too have clamav 0.92.1
but i'm ABLE to update!!!

what is the error message u get, post screenshot...

---

### Post by kwackher on 2008-09-12
Just fyi, this where I get it that they block obsolete versions:  [http://www.clamav.net/support/mirror-problem](http://www.clamav.net/support/mirror-problem)
I absolutely could be wrong about that, but my network is not experiencing problems (because I can update other programs without a hitch) and other Clam users can obviously still get it... I am confused.

But this is what I get in response to "sudo freshclam":

ClamAV update process started at Fri Sep 12 23:42:53 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.94
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.inc is up to date (version: 48, sigs: 399264, f-level: 35, builder: sven)
Ignoring mirror 219.117.246.122 (due to previous errors)
Ignoring mirror 61.192.198.25 (due to previous errors)
Ignoring mirror 61.206.123.121 (due to previous errors)
Ignoring mirror 203.178.137.175 (due to previous errors)
Ignoring mirror 203.212.42.128 (due to previous errors)
Ignoring mirror 211.10.155.48 (due to previous errors)
Ignoring mirror 218.44.253.75 (due to previous errors)
Ignoring mirror 219.106.242.51 (due to previous errors)
ERROR: getpatch: Can't download daily-8218.cdiff from db.local.clamav.net
Ignoring mirror 219.106.242.51 (due to previous errors)
Ignoring mirror 219.117.246.122 (due to previous errors)
Ignoring mirror 61.192.198.25 (due to previous errors)
Ignoring mirror 61.206.123.121 (due to previous errors)
Ignoring mirror 203.178.137.175 (due to previous errors)
Ignoring mirror 203.212.42.128 (due to previous errors)
Ignoring mirror 211.10.155.48 (due to previous errors)
Ignoring mirror 218.44.253.75 (due to previous errors)
ERROR: getpatch: Can't download daily-8218.cdiff from db.local.clamav.net
Ignoring mirror 218.44.253.75 (due to previous errors)
Ignoring mirror 219.106.242.51 (due to previous errors)
Ignoring mirror 219.117.246.122 (due to previous errors)
Ignoring mirror 61.192.198.25 (due to previous errors)
Ignoring mirror 61.206.123.121 (due to previous errors)
Ignoring mirror 203.178.137.175 (due to previous errors)
Ignoring mirror 203.212.42.128 (due to previous errors)
Ignoring mirror 211.10.155.48 (due to previous errors)
ERROR: getpatch: Can't download daily-8218.cdiff from db.local.clamav.net
Ignoring mirror 211.10.155.48 (due to previous errors)
Ignoring mirror 218.44.253.75 (due to previous errors)
Ignoring mirror 219.106.242.51 (due to previous errors)
Ignoring mirror 219.117.246.122 (due to previous errors)
Ignoring mirror 61.192.198.25 (due to previous errors)
Ignoring mirror 61.206.123.121 (due to previous errors)
Ignoring mirror 203.178.137.175 (due to previous errors)
Ignoring mirror 203.212.42.128 (due to previous errors)
ERROR: getpatch: Can't download daily-8218.cdiff from db.local.clamav.net
Ignoring mirror 203.212.42.128 (due to previous errors)
Ignoring mirror 211.10.155.48 (due to previous errors)
Ignoring mirror 218.44.253.75 (due to previous errors)
Ignoring mirror 219.106.242.51 (due to previous errors)
Ignoring mirror 219.117.246.122 (due to previous errors)
Ignoring mirror 61.192.198.25 (due to previous errors)
Ignoring mirror 61.206.123.121 (due to previous errors)
Ignoring mirror 203.178.137.175 (due to previous errors)
ERROR: getpatch: Can't download daily-8218.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Ignoring mirror 203.178.137.175 (due to previous errors)
Ignoring mirror 203.212.42.128 (due to previous errors)
Ignoring mirror 211.10.155.48 (due to previous errors)
Ignoring mirror 218.44.253.75 (due to previous errors)
Ignoring mirror 219.106.242.51 (due to previous errors)
Ignoring mirror 219.117.246.122 (due to previous errors)
Ignoring mirror 61.192.198.25 (due to previous errors)
Ignoring mirror 61.206.123.121 (due to previous errors)
ERROR: Can't download daily.cvd from db.local.clamav.net
Trying again in 5 secs...

(After a minute or two of that...)

ERROR: Can't download daily.cvd from database.clamav.net
Giving up on database.clamav.net...
Update failed. Your network may be down or none of the mirrors listed in freshclam.conf is working. Check [http://www.clamav.net/support/mirror-problem](http://www.clamav.net/support/mirror-problem) for possible reasons.

---

### Post by macvr on 2008-09-12
y dont u install the gui from the add/remove programs and update from that?

well thats how i do it! it kept saying initially 'permission denied' but i ran the GUI as root [added gksudo if front of the menu entry] and it got updated...

---

### Post by kwackher on 2008-09-12
I have the GUI. I tried that and it says "Unable to retrieve updates. Try again later." I've checked the mirror status page and it looks like they are all up. And I didn't have this problem until 9/12. As of late Sept 11 I could update everything with no problems.

---

### Post by macvr on 2008-09-13
y dont u try other antivirus?... clamav just scans, it doesnt remove/disinfect viruses!

even avg doesnt help to remove/disinfect viruses
i recently tried avast, it seems good, also fprot... only these 2 have removal options...

---

### Post by cariboo on 2008-09-13
Have you tried any of the suggestions on the page that you linked to

[http://www.clamav.net/support/mirror-problem](http://www.clamav.net/support/mirror-problem)

I tried:

```
host -t txt current.cvd.clamav.net
```

in a terminal as suggested on the page and the resulting output is:

```
current.cvd.clamav.net descriptive text "0.94:48:8230:1221276541:1:35"
```

If you don't get the same result, like the page says your network is broken. Check /etc/resolv.conf to make sure your dns servers are right.

Jim

---

### Post by Sef on 2008-09-13
> y dont u try other antivirus?... clamav just scans, it doesnt remove/disinfect viruses!That is not correct.  Clam can remove them.

moved to absolute beginners.

---

### Post by kwackher on 2008-09-13
It was the stinkin DNS servers! I really hate my ISP. Why do we even have ISP's?

I changed those in my router about a month or two ago because of the caching vulnerability (which my ISP still hasn't fixed apparently), but I had to take the router out of my network earlier this week and forgot to update /etc/resolv.conf. So that's why it stopped working yesterday. 

Thanks for the help everybody! I would still like to see ClamAV get an updated package in the repository though...

---

### Post by macvr on 2008-09-14
> **Sef said:**
> That is not correct.  Clam can remove them.

moved to absolute beginners.

oh!!! then it means i dont know how to use clamav properly!!! i cant find an option to remove from the gui!

how do u remove?

---

### Post by o0splitpaw0o on 2008-10-23
Ubuntu

The Ubuntu packages are maintained by Ubuntu MOTU Developers. ClamAV has been officially included in the Ubuntu distribution since the first Ubuntu release. Run apt-cache search clamav to find the name of the packages available for installation.

There are two classes of clamav packages available for Ubuntu users:

The released set (release, *-updates, and *-security) are patched for security updates. Following extensive testing of clamav and the packages that use it in the backports repository, they may be updated to a newer version. These are official Ubuntu packages and supported by community developers.

The Ubuntu backports repository will contain the newest clamav version that has been at least lightly tested to work with that version. These packages can be installed by enabling the backports repository in your system. These are official Ubuntu packages and supported by community developers.

---

### Post by pot_roast on 2008-11-12
I have to agree with some of the others. I understand that the fixes have been backported, but the checks that the ClamAV folks are doing is simply blocking the Ubuntu package from retrieving updates because the version number is outdated.

To many folks, this is a very serious problem. It means that we are not getting any database updates because the version number is considered "old" by the ClamAV folks. 

I'm talking about folks using ClamAV in their mail server environment, not the "I have antivirus because I have Windoze boxes on my LAN" GUI users. 

Is it going to be a huge issue for the package maintainers to bump the version? Or are those of us that really *need* to have ClamAV functioning expected to pull the version out of the Intrepid tree? That doesn't seem very user friendly (or logical) at all. Also, aptitude was reluctant to install the newer version from the deb anyway - I believe that it had some deps that it was unable to resolve.

My other option is to spin up another ubuntu box, download ClamAV from source, compile it, and copy the appropriate binaries over to my production server.

Thoughts?

---

