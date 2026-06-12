---
title: "Install problem with Bios screen"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-05-14
I got a lap top from a friend of mine who doesnt remember his bios password. I want to put Ubuntu 8.04 on it but I cant get past the Bios screen withotu the password. Does anybody have any suggestions to get around this or is the computer garbage? Ive tried taking off the battery, the CPU battery, and all these other little tricks and nothing works. 

It is a Dell Latitude D610
 700 Mhz, 512 DDR Ram, and 60 GB HD.

---

### Post by will1911a1 on 2008-05-14
> **Bigtime_Scrub said:**
> I got a lap top from a friend of mine who doesnt remember his bios password. I want to put Ubuntu 8.04 on it but I cant get past the Bios screen withotu the password. Does anybody have any suggestions to get around this or is the computer garbage? Ive tried taking off the battery, the CPU battery, and all these other little tricks and nothing works. 

It is a Dell Latitude 700 Mhz, 512 DDR Ram, and 60 GB HD.

There's usually a jumper you can reset that will clear the CMOS, usually near the battery.

---

### Post by Bigtime_Scrub on 2008-05-14
Ive tried that it doesnt work. I did some research and Im told its stored on a security chip, but it didnt say how to reset it.

---

### Post by rockerphil on 2008-05-14
i've personally forgotten my BIOS password a couple of times, and i found that pulling the motherboard battery for about an hour or so resets the motherboard to factory settings (at least with my machine) hopefully this is also true with your machine. hope it helps

---

### Post by will1911a1 on 2008-05-14
> **Bigtime_Scrub said:**
> Ive tried that it doesnt work. I did some research and Im told its stored on a security chip, but it didnt say how to reset it.

I'm surprised that didn't do the trick.  I've never had resetting the jumper fail...

Maybe this will help:
[http://searchwindowssecurity.techtarget.com/tip/1,289483,sid45_gci1124083,00.html]("http://searchwindowssecurity.techtarget.com/tip/1,289483,sid45_gci1124083,00.html")
That page lists some BIOS backdoor passwords as well as some other suggestions.

Good luck.

---

### Post by Bigtime_Scrub on 2008-05-14
The gray screen of death is VERY frustrating. :mad:

---

### Post by Bigtime_Scrub on 2008-05-14
The password is in EEPROM and will be remembered for
longer than our lifetime. Jumpers and removing the battery will not work. I dont look forward to getting the run around from Dell when I call them. :(

---

### Post by will1911a1 on 2008-05-14
> **Bigtime_Scrub said:**
> The password is in EEPROM and will be remembered for
longer than our lifetime. Jumpers and removing the battery will not work. I dont look forward to getting the run around from Dell when I call them. :(

Yuck, sorry to hear that.

---

### Post by will1911a1 on 2008-05-14
I found a few sites with methods for clearng eeprom memory but they all seem to involve soldering...

---

### Post by Bigtime_Scrub on 2008-05-14
> **will1911a1 said:**
> I found a few sites with methods for clearng eeprom memory but they all seem to involve soldering...

Im going to try and short circuit this thing. It will either rest the p/w or totally brick it.

---

