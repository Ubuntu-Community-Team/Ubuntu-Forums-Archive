---
title: "Ubuntu 8.10 CD boot problem"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Don1947 on 2008-11-22
I downloaded Ubuntu 8.10 Desktop i386 from University of Oxford server, converted to a CD-R. 
CD booted beyond menu (view but do not instal option selected) but stopped with following error message a minute or so later:


"[127.177223]
end_request: I/O error devsr0, sector1431296
127.177286 Buffer I/O error on device SR0, logical block 178912."

Thinking I had a bad download I spent another 3 hours plus downloading from University of Kent server. Converted to CD-R. 

Booted then same problem and message.

I then used a different brand of CD-R 

Booted that and got same message and problem again. 

So unlikely to be bad download or bad media. (Maxell & TDK used)

I have established that device "SR 0" is the DVD player/CD burner-( a Samsung that has never given me any problems before)

Anyone any idea what the problem is here?

---

### Post by laurielegit on 2008-11-22
Did you check the disk integrity. Also try downloading through torrents as a solid download has a high risk of becoming corrupted.

Good luck,

Laurie

---

### Post by hankinator on 2008-11-22
Okay,
1. Try a different download location.
2. Download and burn to a disk and _VERIFY_ if theres a option too.
3. Before Installing verify the disk.
4. If it still doesn't work, I would say it might be your burner, in that case buy a ubuntu disk off of ebay or another site for like 2$ to make sure.
5. If not your Reader/Motherboard IDE/SATA, is bad, or going bad, if its IDE, then most likely, I've had the same problem before.

---

### Post by Don1947 on 2008-11-22
Thanks Laurie-Just realised that  as I intend to use this with a 64 bit processor I might be better off downloading the 64 bit version?

Sorry, know nothing about torrents or checking disk (CD, I presume) integrity.

---

### Post by Don1947 on 2008-11-22
> **hankinator said:**
> Okay,
1. Try a different download location.
2. Download and burn to a disk and _VERIFY_ if theres a option too.
3. Before Installing verify the disk.
4. If it still doesn't work, I would say it might be your burner, in that case buy a ubuntu disk off of ebay or another site for like 2$ to make sure.
5. If not your Reader/Motherboard IDE/SATA, is bad, or going bad, if its IDE, then most likely, I've had the same problem before.

Thanks for the reply

1. Tried 2 already-second has never let me down-tried first as it is very near me.
2. No option to verify on (free) ISO burner-used for 8.04 and performed flawlessly.
3. No idea how to do this
4. Good idea-had already found a local source with view to eliminating the burner (which, happily, is still under build warranty along with the rest of the (SATA) rig!)

---

### Post by hankinator on 2008-11-22
> **Don1947 said:**
> Thanks for the reply

1. Tried 2 already-second has never let me down-tried first as it is very near me.
2. No option to verify on (free) ISO burner-used for 8.04 and performed flawlessly.
3. No idea how to do this
4. Good idea-had already found a local source with view to eliminating the burner (which, happily, is still under build warranty along with the rest of the (SATA) rig!)

Okay i had a good idea, do you have Wine installed?

---

### Post by Don1947 on 2008-11-22
> **hankinator said:**
> Okay i had a good idea, do you have Wine installed?

Not on that particular computer-(I have 2) Only Windows XP on one of 2 partitions-was going to use other partition for Ubuntu 8.10 maybe. 
The other computer-much older -currently runs 8.04-and I did install Wine soon after Ubuntu installation as I thought i might need to use it to run some stuff ported over from other computer-but have not needed to use it as yet-as I have found suitable, and in some cases better, alternatives.
I have only been into Linux for a few weeks.

---

### Post by hankinator on 2008-11-22
> **Don1947 said:**
> Not on that particular computer-(I have 2) Only Windows XP on one of 2 partitions-was going to use other partition for Ubuntu 8.10 maybe. 
The other computer-much older -currently runs 8.04-and I did install Wine soon after Ubuntu installation as I thought i might need to use it to run some stuff ported over from other computer-but have not needed to use it as yet-as I have found suitable, and in some cases better, alternatives.
I have only been into Linux for a few weeks.


oic, i thought u had all ubuntu computers 

```
http://www.poweriso.net/PowerISO43.exe
```

download install that, and burn the ISO with the verify option. and try it then.

---

### Post by luke0927 on 2008-12-11
I have the same problem i have burned Ubuntu and Kubuntu from multiple dowloads and verified the checksum and i get this too i haven't been able to get a succesful install yet...I'm still messing with it. Im burning to maxell CD's also

---

