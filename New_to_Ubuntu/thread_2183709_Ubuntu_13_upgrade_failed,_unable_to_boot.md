---
title: "Ubuntu 13 upgrade failed, unable to boot"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by Crossbow on 2013-10-26
I tried to upgrade to 13.10, which took several hours and eventually the computer just froze. I waited 24 hours and finally shut down. I am now not able to do anything even in recover mode. The error message I get in root says I have to manually run "dpkg --configure -a" to correct the error but it doesn't recognize that. I'm probably doing it wrong. "apt-get update" does nothing. I mean nothing, it just hangs there. The "repair" option also does nothing. 

I'm currently booting from my old version 7 disc. I am completely ready to give up on Ubuntu. Up until 12.10 I liked it a lot better than Windows, but my upgrade to 12.10 was a disaster, and this is even worse. This OS is supposed to be user-friendly for those of us who are computer illiterate, and when I started using it it was, but every new version seems to have more and more problems and require more and more computer knowledge just to use it.

---

### Post by fantab on 2013-10-26
Upgrading internally from one version to another is mostly messy. I always do a clean install of the new version. It is not only cleaner and fresh, its also a time saver. May I suggest the same to you? Do a fresh install of 13.10.

---

### Post by craig10x on 2013-10-26
> **fantab said:**
> Upgrading internally from one version to another is mostly messy. I always do a clean install of the new version. It is not only cleaner and fresh, its also a time saver. May I suggest the same to you? Do a fresh install of 13.10.

If one has only 1 ubuntu installed on their drive, usually the live iso installer will give you the option to upgrade...i have been using that and my experience has been very good..i suspect it works a lot better most of time that using the software updater method of upgrading...

I'd suggest he tried to re-upgrade using that method...nothing to lose at this point...worse case scenario: he will have to re-install but do a clean one...

---

### Post by fantab on 2013-10-26
> **craig10x said:**
> If one has only 1 ubuntu installed on their drive, usually the live iso installer will give you the option to upgrade...i have been using that and my experience has been very good..i suspect it works a lot better most of time that using the software updater method of upgrading...

I'd suggest he tried to re-upgrade using that method...nothing to lose at this point...worse case scenario: he will have to re-install but do a clean one...

Well, you have a new ubuntu version on DVD/USB already, why do a upgrade when you can with equal ease get a fresh install. However, I have my Partitions setup for clean installs. I don't use /home, and I don't save my personal data in Home folder which is on my / partition. All my data is saved to a simple ext4 formatted partition. I just find more value in clean installs. And an additional 30mins for tweaking ubuntu to my taste.

But then... "to each his own".

---

### Post by craig10x on 2013-10-26
Like you...i ALWAYS did clean installs...never tried to do upgrades...figured they would be very troublesome and not worth the effort...but after each clean install, seems i spent at least a day or two putting all programs back on, restoring settings, adding my data back in (music, videos, documents, etc)...and after doing my first UPGRADE using the iso installer method...only had to spend about 20 to 25 minutes putting back what didn't make it in or was changed back to default...so i enjoy the time and work it saves me and that's why i decided to continue to use that method...

But i can't really speak for the software updater method of upgrade since i have never done it, though i get the impression that while it CAN work out well, there is a much greater chance of problems with it that the installer method i outlined...

---

### Post by buzzingrobot on 2013-10-26
What version did you try to upgrade from?  Were you running 13.04 and did you use the distribution upgrade option it offered?  In-place upgrades that jump multiple releases (e.g., 12.10 to 13.10) aren't really supported.  They should be done by upgrading to each intervening release.

Any and all PPA's should be backed out and the installation returned to pre-PPA state before an update.

Is there any response at all to "dpkg --configure -a"?  Does it display an error message, or just hang? 

Any OS upgrade, on any sustem, will be problematic if the user has made changes to some of the core files.

---

### Post by fantab on 2013-10-26
> **craig10x said:**
> Like you...i ALWAYS did clean installs...never tried to do upgrades...figured they would be very troublesome and not worth the effort...but after each clean install, seems i spent at least a day or two putting all programs back on, restoring settings, adding my data back in (music, videos, documents, etc)...and after doing my first UPGRADE using the iso installer method...only had to spend about 20 to 25 minutes putting back what didn't make it in or was changed back to default...so i enjoy the time and work it saves me and that's why i decided to continue to use that method...

But i can't really speak for the software updater method of upgrade since i have never done it, though i get the impression that while it CAN work out well, there is a much greater chance of problems with it that the installer method i outlined...

@craig10x: Have you read this: [http://ubuntuforums.org/showthread.php?t=1748541&p=10765330#post10765330 ]("http://ubuntuforums.org/showthread.php?t=1748541&p=10765330#post10765330")

---

### Post by craig10x on 2013-10-26
@fantab: interesting idea....though to be honest, it's easier to use the upgrade method i have been using...less fuss involved ;)

I have a suggestion: try it the next time you are going to clean install ubuntu...if it doesn't work out to your satisfaction, you can always re-install clean (as you would have done anyway)...
In case you hadn't already read it, you might want to read about my experience with it in this thread:
[http://ubuntuforums.org/showthread.php?t=2181643](http://ubuntuforums.org/showthread.php?t=2181643)

As i said, i am talking about the installer upgrade option here and NOT the software updater method that so many use...worked identically for me TWICE and a local friend of mine did it too and worked the same for him...

---

### Post by Crossbow on 2013-10-30
A clean install is not an option at this point because the machine is unusable so I can't download anything. Is there nothing I do from recovery mode? I guess I could install version 7 and try to download 13 using that if I have to.

---

### Post by buzzingrobot on 2013-10-30
If that version 7 CD is a live image, and if it just isn't too old, here  are some instructions about booting into a liveCD and using it to  recover an installation.  Note the guidance about fixing a failed  upgrade:[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery).

Here is the Recovery Mode page:  [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode),  If you can mount the filesystem, you ought to be able to follow the same upgrade procedures,

---

### Post by craig10x on 2013-10-30
@crossbow: i have a suggestion...try the method i outlined previously...if you were only running 1 version of ubuntu, just boot up from the live cd of 13.10...if you don't have one (since you can't download)...perhaps you can have a friend download and burn an iso for you...see if it offers the option to UPGRADE....yeah, i know you are already running 13.10, but you can Upgrade again anyway...I've done it (did that to clean out excess stuff, i was running 13.10 in development and used the final to upgrade 13.10 again) it might save everything for you because it will do everything over again...worth a try, anyway...

---

### Post by Crossbow on 2013-11-02
Fixed. I found the answer, or at least a partial answer, [here]("http://askubuntu.com/questions/361959/ubuntu-13-04-to-13-10-upgrade-failed").

From the recovery menu, I first tried to enable networking but nothing happened. Decided to go ahead anway. From root: 

```

mount -o remount,rw /
dpkg --configure -a

```

That ran for a while and set up a bunch of stuff, then "processing stopped due too many errors." Ran apt-get update and sure enough, it wasn't connecting to the internet. But this time when I went to enable networking, I succeded! Then I did "fix broken packages" and that set up everything else. One last apt-get update and everything seems fine now. 

RE: Live grades: Up until 12.10, I never had any trouble with them. After the 12.10 disaster I should have known better. Next time, clean install. Actually I originally tried to do a clean install with 12.10 but for whatever reason, I could not get the disc to burn. Probably should just have had someone else do it for me.

---

