---
title: "Cannot Open Display on toshiba satellite"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by rte4 on 2013-10-02
Hi, absolute beginner here, still haven't even used ubunto for a single second yet outside of the command line...

here's the issue: I have a Toshiba Satellite C55D-A and I'm trying to get Xubunto 13.04 up and running on it. I disabled SecureBoot in the BIOS and installed 13.04 using a live USB. It looked like the installation process worked (except I had to manually restart after installation when it tried to restart, not sure if that is meaningful...). Upon restarting it just loaded the command line. I tried running startx but get the message "Fatal server error: no screens found". I have also just tried the "Try Ubunto Without Installing" option using the live USB with the same results. Any advice is appreciated

Thanks,
rte4

---

### Post by DuckHook on 2013-10-02
Welcome to the forums, rte4,

Without more info, it's hard to know where to begin. At a minimum, we need to know if you are dual-booting Win8, using UEFI, installing to GPT or MBR, how you partitioned, and if you installed the bootloader when install process asked you to. Also, does the command line have a flashing '$' or '#'? Going by memory here, but the former means you have a basic OS; the latter means you are just at GRUB (which is not as good).

[Here]("https://help.ubuntu.com/community/UEFI") is a good page on installing to UEFI BIOSes in new computers. As you can see, you must also disable FastBoot. Oddly enough, I believe the newest Ubuntus have kernels signed for Secureboot, so that may be an option that you *don't* actually have to disable.

---

### Post by morgan4 on 2013-10-02
I have a Toshiba Satelite and what you are describing happened to me too when I installed 12.04 about two weeks ago. If I remember correctly, it had too do with the screen and I needed to edit Grub in some fashion (something along the lines of acpi_ before quiet splash, thing, sorry not so technical). 

This blog, I followed the steps that applied to me and I have been happily using Ubuntu since, I hope it helps you. 

[https://coderwall.com/p/ydbldg](https://coderwall.com/p/ydbldg)

---

### Post by rte4 on 2013-10-03
ahhhaaa, thank you sir, that did it!

---

### Post by rte4 on 2013-10-03
issue resolved, thank you.

---

### Post by mörgæs on 2013-10-03
Good, then please mark the thread 'solved' using Thread Tools.

---

