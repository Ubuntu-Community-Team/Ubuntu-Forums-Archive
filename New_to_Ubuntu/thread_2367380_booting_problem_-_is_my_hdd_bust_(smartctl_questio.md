---
title: "booting problem - is my hdd bust? (smartctl question)"
date: 2017-07-29
forum: New to Ubuntu
---

### Post by gabim3 on 2017-07-29
Hello

I keep having problems with booting my single OS ubuntu machine, when I startup my laptop I keep getting errors such as: "Checking Media - failed", "Failure reading sector 0x... from 'hd0'", and so on. When OS does boot up and I can use the laptop, after some time the OS blocks (possibly when I use Chrome) and crashes. Sometimes when I enter the BIOS UEFI bootup configuration I don't see a "boot from HDD option", only LAN or USB.

Sollutions I have tried: 
- fcsk
- restarting the laptop many number of times
- switching between bootup mode (UEFI, Secure On), (UEFI, Secure Off), (Legacy)
- reinstalling Ubuntu from Legacy bootup or from UEFI Secure On/Off
- replacing Ubuntu 16 with Ubuntu Mate 16 or with Linux Mint 16 (all x64)
These work sometimes and I can use my laptop for a few days but then I get errors again. Sometimes it is enough to just restart the laptop many times and it will boot.

I bought the laptop with Ubuntu 12 as single OS and it worked fine for 2-3 years before I started getting these errors. Then I installed Linux Mint, about 6 months ago and it worked fine until 3-4 weeks ago, only rarely giving booting error. At one point I ran a disk analysis from Ubuntu or Mint and also from a bootable USB and it didn't find any problem. I can redo the test if you suggest me a good tool.

**My question**: is my HDD bust and needs to be replaced? or is there some other problem? how can I be sure it is my hdd before spending on a new one? I find it wierd that the OS starts eventually. I would expect that, if the HDD were broken, it would never start.

My system: Dell Inspiron 15R-5521, Hdd 1TB SATA3 5200 rpm, i7, 8 GB RAM

Thanks

EDIT: 
The last error I got at startup is: error: environment block too small. Error: attempt to read or write outside disk 'hd0'.
I also ran Dell ePsa Pre-boot system assessment. [DST Short test]("https://www.techwalla.com/articles/what-is-the-laptop-dst-short-test") for HDD was passed but the Long one got blocked at 60%...
I managed to boot my Ubuntu (touchpad wasn't working though) and **I ran smartctl -a. Can anyone interpret the attached results please?**
[page-1]("https://imagebin.ca/v/3V5BPqBPNdEL") [page-2]("https://imagebin.ca/v/3V5BflPsnMVx") [page-3]("https://imagebin.ca/v/3V5BoVQXFrCw")

---

### Post by Autodave on 2017-07-29
Assuming it has a spinning HD, it is quite possible that the HD is on its way out. Better get whatever it is that you don't want to lose copied externally before it refuses to boot.

One other thing to try.....and don't laugh.....I have fixed more than one laptop this way:

   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

It is worth a shot and won't cost a thing.

---

### Post by mrgnome on 2017-07-29
I have a fair amount of kernel output experience. Yes, your HDD (if you have one) is almost certainly on the way out. Upgrade ASAP

---

### Post by gabim3 on 2017-07-29
Thanks @autodave. It didn't work.

---

