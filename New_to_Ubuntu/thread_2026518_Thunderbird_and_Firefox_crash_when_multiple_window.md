---
title: "Thunderbird and Firefox crash when multiple windows are opened"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by Charlie Chick on 2012-07-15
I'm running a clean install of 12.04LTS 64 bit on a 5 year old Dell Dimension 3100 computer. Since the install, whenever I write a new e-mail and need to refer back to an old one, I click the Thunderbird icon and get the two half sized windows for me to choose which one. It is at this point that the computer freezes. Exactly the same happens in Firefox. Only a hard boot works afterwards. 

As I've used Ubuntu for 7 years, I'm not used to the computer crashing. Am I doing something wrong?

Many thanks in advance for your help.

---

### Post by cogier on 2012-07-15
I looked at the original specifications for your Dell and they say the standard memory is 128k. If you only have this amount then this could be your problem.

If you are not sure how much memory you have open Terminal with
[Ctrl] + [Alt] + T
and type **free -m** and look at "total" (the -m forces the output to be in MB).

You could try Ubuntu 32 bit or better still Lubuntu.

---

### Post by Peripheral Visionary on 2012-07-15
I have a Dell Dimension also, a little older, with 512 RAM. I think the 64-bit version is the problem. Switching to the 32-bit version may solve it.

I use Xubuntu 12.04 32-bit, and Seamonkey (integrated Mozilla browser and e-mail that works like older versions of Firefox + Thunderbird) trouble-free and fast.

---

### Post by Charlie Chick on 2012-07-16
I upped the memory to 2GB (the maximum the motherboard will take) and have a 750Gb hard drive. I had no probems with versions before 12.04 on the same hardware and have always used Thunderbird and Firefox.

---

