---
title: "Stuck on boot loading screen"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by abney317 on 2012-09-28
Just installed Ubuntu with a USB and it all went well until I restarted... 
It just gets to the logo/boot loading screen and just sit there forever.

I'm not really sure how to go about fixing the issue though =/

I've got it set up for dual boot with windows 7. I've also got a RAID 0 set up.

---

### Post by 2F4U on 2012-09-28
Can you provide more information about your hardware? Is the screen staying black/blank or does it display the Ubuntu text that is usually shown during loading the OS?

---

### Post by abney317 on 2012-09-28
> **2F4U said:**
> Can you provide more information about your hardware? Is the screen staying black/blank or does it display the Ubuntu text that is usually shown during loading the OS?
[img]http://imageshack.us/a/img42/9636/specst.png[/img]

It's displaying the Ubuntu logo with the the loading dots

---

### Post by abney317 on 2012-09-28
Am I allowed to bump? These threads get buried quickly :|

---

### Post by Bashing-om on 2012-09-28
abney317; Hi !

Apologies for the delay..

Bumping...rule of thumb is 24 hrs.

Your boot issue is complicated by the raid setup ..been a long time since I looked at raid 0/grub..Bet others are in the same boat.

Now it gets a bit more complex: 
 Is your raid array set up onboard motherboard, hardware raid controller, or is it set up in software....hardware raid or software raid ? ubuntu will deal with them all, but different tools will be required for each.

As an aside, do not be too surprised that you  will be directed to re-install ubuntu from the alternate install disk as that install supports raid arrays.

gone to look at my raid notes ==> BDQ

---

### Post by abney317 on 2012-09-28
Hey, thanks for the reply :)

I honestly don't know if it's hardware or software raid... I'm not sure how to figure out since I didn't set it up myself.
Didn't have much luck finding any details on the motherboard itself... it's an Alienware if you by chance know whether they are commonly hardware or software raid

---

### Post by Bashing-om on 2012-09-29
ok...recon well figure it out. 

How do you know you have raid 0 ? ..We Have to Know the raid level in order to set up and install grub.

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by abney317 on 2012-09-29
> **Bashing-om said:**
> ok...recon well figure it out. 

How do you know you have raid 0 ? ..We Have to Know the raid level in order to set up and install grub.
[INDENT]regards <==BDQ

[/INDENT]
if you look at my screenshot of my specs that I posted above, the hard drive is named "M17XR4_RAID0"... so it seemed pretty safe to assume that it was raid 0

---

### Post by Bashing-om on 2012-09-29
Yeah... I see that ..but, raid level 0 requires at least 2 drives (or maybe partitions ?) preferably at least 3 drives.

However...upon looking and consideration; This is above my skill level and knowledge of windows. I would not willingly be a part of damaging your operating system.

This might be doable with 3 drives. It is a huge undertaking.

Here are the links to make it happen:
[http://supportex.net/2010/11/determine-raid-controller-type-model/](http://supportex.net/2010/11/determine-raid-controller-type-model/)
[http://ubuntuforums.org/showthread.php?t=1886279 ,-triple boot raid 0](http://ubuntuforums.org/showthread.php?t=1886279 ,-triple boot raid 0)

This being my situation. I suggest that you start another thread to get  the attention of others more qualified to help you. Emphasize raid 0 - windows- ubuntu  in the title of the new thread .[INDENT]I wish you success in this endeavor <==BDQ

[/INDENT]

---

