---
title: "64 to 32 bit"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Nevyn on 2008-05-01
Didn't find anything when searching, so I'm asking instead.

I've had nothing but trouble with the 64-bit version, both 7.10 and 8.04. Since I need the computer for work really soon I just need it to work, then the easiest seems to be to change into 32-bit Ubuntu instead.

Can one change from 64 to 32 bit without re-installing the system?

---

### Post by iSplicer on 2008-05-01
> **Nevyn said:**
> Didn't find anything when searching, so I'm asking instead.

I've had nothing but trouble with the 64-bit version, both 7.10 and 8.04. Since I need the computer for work really soon I just need it to work, then the easiest seems to be to change into 32-bit Ubuntu instead.

Can one change from 64 to 32 bit without re-installing the system?

No, unfortunately, the architecture is different and therefore you need to make a clean install

Good Luck

---

### Post by SunnyRabbiera on 2008-05-01
yeh the two are completely different, so you have to go to the 32 bit version the hard way.

---

### Post by iSplicer on 2008-05-01
> **SunnyRabbiera said:**
> yeh the two are completely different, so you have to go to the 32 bit version the hard way.

its not REALLY that hard, just back up your data (no need if you have a seperate /home partition), and just install ubuntu onto your existing partition. It should take up one hour MAX to set everything up.

Just holler if you run into any problems

---

### Post by Nevyn on 2008-05-02
Ok, thanks for the answers. Too bad, it would have been convenient not having to re-install. =)

---

### Post by Paqman on 2008-05-02
Personally i'd try out a 32-bit LiveCD first. It's probably pretty unlikely that 64-bit itself is the source of your troubles. It would be a shame to reinstall and discover you had exactly the same problems on 32-bit.

---

### Post by iSplicer on 2008-05-02
> **Paqman said:**
> Personally i'd try out a 32-bit LiveCD first. It's probably pretty unlikely that 64-bit itself is the source of your troubles. It would be a shame to reinstall and discover you had exactly the same problems on 32-bit.

I agree. Perhaps you could tell us what problems you are experiencing in a bit more detail?

---

### Post by Kobalt on 2008-05-02
And IMHO you should definetly [have a separate /home partition]("http://www.psychocats.net/ubuntu/separatehome") ,,,

---

### Post by iSplicer on 2008-05-02
> **Kobalt said:**
> And IMHO you should definetly [have a separate /home partition]("http://www.psychocats.net/ubuntu/separatehome") ,,,

I agree with that too. Having a separate /home partition will enable you to keep your data even if you change distros, screw up your system, etc. 

Or if you are dual booting, I suggest having a large DUMP partition, using FAT32 or NTFS, so that both windows and ubuntu can write to it.

---

### Post by Nevyn on 2008-05-02
> **iSplicer said:**
> 
[QUOTE=Paqman;4860197]Personally i'd try out a 32-bit LiveCD first. It's probably pretty unlikely that 64-bit itself is the source of your troubles. It would be a shame to reinstall and discover you had exactly the same problems on 32-bit.
I agree. Perhaps you could tell us what problems you are experiencing in a bit more detail?[/QUOTE]

Yes, I'll try the live cd first to see if it works better, especially flash.

Well, programs (like FF and OpenOffice) have been stalling every now and then. I can shut them down when they do so, but the system isn't nearly as stable as when I tried whatever Ubuntu-version was the newest in 2005 (I loved that, great Java-development enviroment!). The same goes for sound and flash, something I've seen many 64-bit users having trouble with. I've been following a number of how-to's, uninstalling and  re-installing a few of the flash-components, updating alsa-base and so forth, but the things that have worked for others didnt seem to work for me.

I'd rather try and solve the issues since that's the best way to learn the OS, but right now I can't afford it to go wrong since I've got deadlines to keep in my work. Maybe I'll give the 64-bit another go when things slow down a bit =)

I'll holler if I run into problems! =)

---

