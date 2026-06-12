---
title: "upgrading from 12.04 to 1210"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by jeff82 on 2014-07-26
hi get the following message when i try and upgrade(same message "failed fetch" from update manager)
  	 	 	 	   jeff@jeff-Aspire-R3610:~$ sudo do-release-upgrade -d 
 Checking for a new Ubuntu release 
 Err Upgrade tool signature                                                      
   404  Not Found [IP: 91.189.92.200 80]                                         
 Err Upgrade tool                                                                
   404  Not Found [IP: 91.189.92.200 80]                                         
 Fetched 0 B in 0s (0 B/s)                                                       
 WARNING:root:file 'quantal.tar.gz.gpg' missing 
 Failed to fetch 
 Fetching the upgrade failed. There may be a network problem.  
 jeff@jeff-Aspire-R3610:~$

---

### Post by howefield on 2014-07-26
12.10 is end of life, you might be better upgrading straight to 14.04.1

---

### Post by jeff82 on 2014-07-26
that is what i want to achieve but i presumed i needed to get to 1210 first?

---

### Post by howefield on 2014-07-26
No, you can upgrade from one LTS (Long Term Support) release to the next LTS release.

12.04 and 14.04 are both LTS releases. I haven't been following the upgrade path closely but I believe you should be offered the upgrade automatically.

---

### Post by jeff82 on 2014-07-26
just checked the upgrade notes again for clarity its says to go to 1210 and not to 1404.....so im a bit stuck

---

### Post by kansasnoob on 2014-07-26
> **jeff82 said:**
> just checked the upgrade notes again for clarity its says to go to 1210 and not to 1404.....so im a bit stuck

I'd like to see the upgrade notes you're reading. It's never OK to upgrade to an EOL release - never!

You can upgrade directly from 12.04 to 14.04 but you need to open the Update Manager, click on settings in the lower left hand corner, then make sure the Notify me of new verson is set to LTS versions:

[ATTACH=CONFIG]255045[/ATTACH]

But first open the terminal and run:

```
uname -r
```

If that shows you're running the 3.13 series kernel DO NOT upgrade to Trusty because of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

---

### Post by ajgreeny on 2014-07-26
Update-manager is not yet offering the update to 14.04.1 but apparently will be doing so in the very near future, so just wait a few days/weeks and it should be available.

---

### Post by jeff82 on 2014-07-26
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
these were the notes "to avoid damaging your running system, upgrading should only be done from one release to the next release"

---

### Post by kansasnoob on 2014-07-26
> **jeff82 said:**
> [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
these were the notes "to avoid damaging your running system, upgrading should only be done from one release to the next release"

The problem with Community Wiki pages is that anyone can change them, and they're often out of date, that page shows:

> UpgradeNotes (last edited 2014-04-18

The Current and Supported Versions is badly out of date, this is correct:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

So the only currently supported versions of Ubuntu are Precise and Trusty. Upgrades from Precise to Trusty are broken if the Trusty HWE upgrade has been installed in Precise:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

That said, upgrades are rather notorious for causing breakage even without the presence of critical bugs ;)

---

### Post by QIII on 2014-07-26
Often it is not wise to listen to those who say "trust me", but in this case please do.

Wait for the upcoming point release of 14.04 (which is 14.04.1) and do an LTS to LTS upgrade as recommended by others.

Don't choose an upgrade path that includes EOL versions.

---

### Post by monkeybrain20122 on 2014-07-26
Just backup your data and do a fresh install. A LOT faster and issue free. Forget about fooling with 'upgrade', even if you manage to get it to 'work' you may end up with a broken system after a few hours of waiting and end up having to do a fresh install anyway.

---

### Post by ss1133xx on 2014-09-28
Hello:  Can someone provide the pros and cons of a fresh install of 14.04 versus an upgrade from 12.04?  I am hoping an upgrade (or fresh install) to 14.04 will resolve the problem described in this post:
 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187/comments/806](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187/comments/806)

Thanks.

---

### Post by Impavidus on 2014-09-29
Tonnes of threads about this. In short:
Upgrading is easy. With a single click you get all your applications back for as far as they are still available from the repos and it keep all your setting for as far as they still apply. The downside is that it takes a long time before you get back a working system, during which time nothing should go wrong as it will make a complete mess of your system, and it's less reliable, especially if your system is less clean or if you have proprietary drivers. But I never had serious problems in 8 release upgrades I tried. Reinstalling is reliable and fast, but that doesn't include the time you need for reinstalling and reconfiguring all your applications. So some people always recommend reinstalling, others say upgrading is fine.

---

### Post by ss1133xx on 2014-10-01
Thanks, helpful.  You mentioned "it takes a long time before you get back a working system ..."  How long does it?  Hours, days?

Have you installed 14.04, and if so, thoughts?

---

### Post by Impavidus on 2014-10-02
Hours. Depending on the amount of installed software, the speed of your internet access and the speed of your computer it can be anything from one hour to half a day. A power failure in this time interval can cause enough disruption to necessiate a clean install after all. I have one power failure every 5 years on average, so I don't care, but your situation may be different.

Usually I upgrade, as it seems to work reliably for me, but to change from 12.04 to 14.04 I did a clean install. But that was because at the same time I upgraded my computer's memory and changed from 32 to 64 bits. It worked at once, and then it took me 2 weeks (not continuously) to get all my applications installed and customised again, including a fancy wallpaper switching script that I had to rewrite completely because of some subtle changes in the desktop manager. But that last part would have been necessary too if I had upgraded.

---

### Post by JKyleOKC on 2014-10-02
I'm in the process of changing this box from 12.04 to 14.04, and like Impavidus made the switch from 32 to 64 bits at the same time. I also installed a brand new 1.5-GB drive in it and did a clean install of 14.04 there, so that I did not impact the 12.04 system at all and have all of its configuration files available to help me restore all their settings.

Even so, it's been a full two weeks and I'm still quite a ways away from having everything duplicated. I estimate it will be at least another month yet! However it's turning out to be well worth the effort...

---

### Post by ss1133xx on 2014-10-02
The reason I'm thinking of upgrading to, or installing, 14.04 is because my computer is freezing up on a fairly regular basis, as described in this post:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187/comments/806](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187/comments/806)

It sounds like, if I upgrade and my computer crashes midway through the upgrade, I will have to do a new install instead.  Is that right?

(Also, would be interested to hear why Impavidus and JKyleOKC both switched from 32 to 64 bits.  Wondering if I should do that, so could learn from you folks.)

Thanks.

---

### Post by JKyleOKC on 2014-10-03
> **ss1133xx said:**
> (Also, would be interested to hear why Impavidus and JKyleOKC both switched from 32 to 64 bits.  Wondering if I should do that, so could learn from you folks.)
This machine was using 32-bit code simply because I had done an upgrade from 8.04 to 12.04 rather than doing a clean install. When I went from 7.04 (my first Xubuntu experience, having migrated from Mandrake/Mandriva) to 8.04 in order to be on Long Term Support releases, more than five years ago, the 64-bit versions were still being a bit flaky at times and the general recommendation was to remain with 32 bits unless one was feeling a bit experimentally inclined.

That recommendation hasn't been true for several years now; the 64-bit versions are now every bit as reliable as are the 32-bit ones, and in addition the 64-bit versions are able to run 32-bit programs in the rare case that no 64-bit version of a package exists. When I had to replace another box in my home office a couple of years ago, due to a blown motherboard, I installed 12.04's 64-bit version on the new machine and was quite happy with its improved performance -- although for other reasons (different CPU speed, mostly) the improvement wasn't spectacular.

Still, since I was doing a clean install on a separate drive this time, I chose to make both systems the same at 64 bits -- although the other box will remain at 12.04 for a while, primarily so that I won't have to invest in a second drive for it, also. Once I have 14.04 tuned to my satisfaction, I can back up the files from the other box to this one via my LAN, and do a clean install there also.

Only you can decide which way you want to go, but it seems to me that 64 bits is the wave of the future (having started on a TRS-80, back when 8 bits was as wide as we could get).

---

### Post by Impavidus on 2014-10-03
> **ss1133xx said:**
> 
(Also, would be interested to hear why Impavidus and JKyleOKC both switched from 32 to 64 bits.  Wondering if I should do that, so could learn from you folks.)
When I first installed Xubuntu on this computer (version 10.04 LTS), I didn't really think about whether to use 32 or 64 bits. I happened to have a 32 bits live disk, so I installed 32 bits. When you have between 2 and 3GiB of memory it doesn't matter too much. 64 bits is a little faster, 32 bits can do a little more with the available memory. I had 3GiB of memory in my computer, so I left things as they were when upgrading to 12.04.

But last spring I decided to upgrade the memory to the maximum of 8GiB. 32 bit systems cannot effectively use that amount of memory, so I had to change to 64 bits. There is a hack called PAE that allows you to use more than 4GiB on a 32 bit system, but it still doesn't allow more than 4GiB of memory to be assigned to a single application, and for me that was no option.

Of course, to use 64 bits you need a 64 bit processor, but most processors sold in the past 10 years are 64 bit capable.

---

