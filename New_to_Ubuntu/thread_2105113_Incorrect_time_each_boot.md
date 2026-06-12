---
title: "Incorrect time each boot"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by fractalman on 2013-01-15
Everytime i boot my pc the clock is out by 1 or 2 hours, i had a quick google but everything seems to be for dual booting with windows.  i only have ubuntu 12.04 lts on my pc so i'm not sure what the issue is

---

### Post by SlugSlug on 2013-01-15
Check the time in your BIOS then follow this
[http://rbgeek.wordpress.com/2012/04/30/time-synchronization-on-ubuntu-12-04lts-using-ntp/](http://rbgeek.wordpress.com/2012/04/30/time-synchronization-on-ubuntu-12-04lts-using-ntp/)

---

### Post by muteXe on 2013-01-15
knackered motherboard battery maybe?

---

### Post by Dodeca on 2013-01-15
[http://www.youtube.com/watch?v=ehbvzeU2Eh8](http://www.youtube.com/watch?v=ehbvzeU2Eh8)

---

### Post by Hexxus on 2013-01-15
Yeah, I would bet that its your CMOS battery on your  motherboard.

---

### Post by NikTh on 2013-01-15
> **Hexxus said:**
> Yeah, I would bet that its your CMOS battery on your  motherboard.

Me too :)

---

### Post by tgalati4 on 2013-01-15
Open a terminal:

```
sudo apt-get install ntp
```

It won't keep you from being late, but it will keep accurate time on your machine.

---

### Post by fractalman on 2013-01-16
Ok, Thanks for the replies guys.  

at boot this morning i entered bios and had to set the system time,  then i remembered i needed to find out what battery i have so i totally powered down, removed all mains connections and had a look, and a clean up too, was rather dusty... anyway, on rebooting my pc has held the correct time without me needing to adjust it even though there was no power in the system.

not sure if this would be the battery or not, i would have assumed that once i powered up again the time would need correcting.

I'm going to change the battery anyway as this pc is getting on a bit and hopefully that will sort the problem.

---

### Post by fractalman on 2013-01-18
I replaced the motherboard battery and when i booted up today the pc was displaying the correct time,  many thanks for the replies :)

---

