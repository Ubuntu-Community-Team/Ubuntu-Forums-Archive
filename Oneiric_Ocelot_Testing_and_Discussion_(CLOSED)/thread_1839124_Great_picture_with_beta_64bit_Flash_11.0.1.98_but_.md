---
title: "Great picture with beta 64bit Flash 11.0.1.98 but no sound"
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sum1nil on 2011-09-05
Hi, 
I downloaded and installed the beta 64bit Flash player in Oneiric but there is no sound. The picture is perfect and way less choppy than my laptop's Natty.

Can anyone tell me how to get/fix:guitar: sound out of Flash beta?


[Solved] ****************************************
Duh. Unmute the sound under the icon. Way sorry!!!

---

### Post by sonicb00m on 2011-09-05
I had this problem and had to remove all the flash plugin binaries and reinstall.

```

sudo updatedb
locate libflash

```

I noticed that the npwrapper versions were also still hanging around and deleted those too.

Then I used the PPA in Ubuntu Tweak for the 64 bit latest version and it fixed my problem

---

