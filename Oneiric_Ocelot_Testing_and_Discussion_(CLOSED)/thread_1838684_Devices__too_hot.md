---
title: "Devices  too hot"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-09-04
Since a few days on i386 i've my hdd becoming too hot (putting my fingers on) and really think that is because the fan is running too slowly.
An other user have reported about his graphic card : 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/840828](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/840828)

The problem is to tweak the values/settings of temps/fans, cant find how to do that.

---

### Post by lucazade on 2011-09-04
have you tried to check temp with hddtemp?

install hddtemp and answer yes to start daemon at startup and also about port,
then after a reboot or manually start the service
sudo hddtemp /dev/sda

30-40°C are usually ok

about the fan I suppose you're referring to gfx card one.. I have this issue only using nouveau drivers, with binary blob temp and fan are ok.
and from what i've read this issue with nouveau will be fixed and merged in time for kernel 3.2

---

### Post by dino99 on 2011-09-04
i've previously used hddtemp but finally removed it because its makes hdd very noisy. Will try again.

---

### Post by lucazade on 2011-09-04
> **dino99 said:**
> i've previously used hddtemp but finally removed it because its makes hdd very noisy. Will try again.

really? never noticed the noise.. i'll check as well, i've it installed on all my machines :P

---

### Post by pressureman on 2011-09-04
Check that it's not zeitgeist maxing your CPU, as is mentioned in another thread on this forum. That ramps up the temperature of my notebook until I kill the process.

---

### Post by dino99 on 2011-09-04
tested results: ~50°c, so acceptable
but still 10°c higher than previously, so still looking to tweak fans speed.

---

### Post by dino99 on 2011-09-04
> **pressureman said:**
> Check that it's not zeitgeist maxing your CPU, as is mentioned in another thread on this forum. That ramps up the temperature of my notebook until I kill the process.

yeah it was using 100% of a cpu, so i've purged the zeitgeist stuff a few days ago, no really need it.

---

### Post by dino99 on 2011-09-04
installed psensor to get details, and the fans max speed are totally borked, some are as lower to 200 and highest is 90000 !!! Really broken (lmsensor-atk0110) and need to fix them.

---

