---
title: "Ubuntu 18.04 Freezing Up Issue - Log Interpretation"
date: 2019-10-05
forum: New to Ubuntu
---

### Post by michael-bielesky on 2019-10-05
Dear All,

After installing Ubuntu on a desktop PC (AMD® Ryzen 5 2400g processor; graphics: AMD® Raven; 64-bit; 250 GB SSD) it would crash few hours into browsing and streaming. Things got better after upgrades were installed. Still it would occasionally happen, but a lot less frequently. In the last few days I haven't had a crash even when the computer was left on for few days (knock on wood). I saved the Logs info from my last crash (I attached two .txt files: "All" logs: [ATTACH]284147[/ATTACH] and a shorter list "Important" logs: [ATTACH]284148[/ATTACH] . I was wondering if any of you could have a look at it and tell me if I should be concern about something. I'm completely new to Linux and programming but I decided to challenge myself and learn computers via Linux. Understanding those logs is important for me regardless if the problem prevails or not.

Sincerely,
Mike

---

### Post by michael-bielesky on 2019-10-05
Unfortunately, it froze up on me again while I was just browsing on the net. Are there any utilities that could help me determine the source of the problem?

Mike

---

### Post by CatKiller on 2019-10-06
> **michael-bielesky said:**
> Ryzen 5 2400g

The support for the Raven Ridge APUs wasn't done in time to be put into the 18.04 release. You could try using one of the PPAs that gives a newer Mesa stack, or one of the newer Ubuntu releases, and see if that helps.

---

### Post by michael-bielesky on 2019-10-06
Thanks CatKiller. I followed your suggestions an upgraded to Mesa 19.08 which I believe is the newest version out there. In case it does not help, will getting a Ryzen chip without an integrated graphics solve the instability problem?

Mike

---

### Post by michael-bielesky on 2019-10-06
For others without experience like me here's a link on how to upgrade to Mesa stack 19.0.8: 
[http://ubuntuhandbook.org/index.php/2019/07/install-mesa-19-0-8-ubuntu-18-04-19-04/](http://ubuntuhandbook.org/index.php/2019/07/install-mesa-19-0-8-ubuntu-18-04-19-04/)

---

### Post by michael-bielesky on 2019-10-06
I've also updated my motherboard's (ASUS PRIME B450M-A) BIOS. I will update you in few weeks.

Mike

---

### Post by CatKiller on 2019-10-06
The support for those APUs not being available until just after they were released, and the software cycle for 18.04 finishing some time before they were released, was definitely a thing that happened.

The motherboard OEMs being caught flat-footed by Ryzen not being a cheap-and-nasty solution, but it actually required some attention and effort on their part, was also definitely a thing that happened. 

The steps you've taken - BIOS update and getting on a newer graphics stack - should definitely put you in a good place in terms of support. It should, in time, help you to establish whether it's fixed your problem or if there's something else that needs looking at. Intermittent faults are really frustrating.

Another thing that's probably worth checking - just in case - is to run memtest overnight. Memory timing was one of the things that the OEMs struggled to get a handle on at first - to the extent that there were spreadsheets of memory module model numbers so that people could get exactly the right actual chips. It got a lot better with Zen+ and with updated BIOSes, but it's potentially worth poking at to see if there's a residual problem. If anything shows up you have quite a lot of scope to relax the timings a touch.

---

### Post by mörgæs on 2019-10-06
> **michael-bielesky said:**
> ... upgraded to Mesa 19.08 which I believe is the newest version out there. In case it does not help, will getting a Ryzen chip without an integrated graphics solve the instability problem?


Ubuntu 19.10 has Mesa 19.2. 

It's to early to conclude that it's a hardware problem which requires hardware changes. There are still more software options to try.

---

### Post by michael-bielesky on 2019-10-06
> **CatKiller said:**
> (...) Another thing that's probably worth checking - just in case - is to run memtest overnight. Memory timing was one of the things that the OEMs struggled to get a handle on at first - to the extent that there were spreadsheets of memory module model numbers so that people could get exactly the right actual chips. It got a lot better with Zen+ and with updated BIOSes, but it's potentially worth poking at to see if there's a residual problem. If anything shows up you have quite a lot of scope to relax the timings a touch.

I ran MemTest86 v8.2 Free from a bootable USB as instructed here: [https://www.memtest86.com/download.htm](https://www.memtest86.com/download.htm)

Instruction from Readme.txt:

*"For Linux:*

*1) Insert a USB drive into a USB slot.*
*2) Determine which device the USB drive is assigned as (eg. /dev/sdc).*
*3) As root, use the 'dd' command to write the image to the USB drive. For example,*

*sudo dd if=memtest86-usb.img of=<dev>*

[I]where <dev> is the device the USB key is assigned to. Use the base device (ie. /dev/sdc) not a partition designation (ie. /dev/sdc1)."

[/I]The test was completed with zero errors, but I'm attaching the output as an HTML file in case you want to look at it: [ATTACH]284154[/ATTACH]

Mike

---

### Post by michael-bielesky on 2019-10-08
Hi!

So things look a lot better, but the system still has a tendency to freeze up once in while. It's rare enough that it wouldn't particularly bother me, if it wasn't for molecular computations that I'm planning to run, some which might need several days to complete. Any other suggestions on how to further improve the system's stability before I start looking into getting a new CPU and graphics card?

Cheers,
Mike

---

### Post by mörgæs on 2019-10-10
It's a bit difficult to answer. What is the status? What have you tried and which results did you get?

---

### Post by michael-bielesky on 2019-10-14
Hi,

The system wasn't stable enough even after updating to Ubuntu 19.04. The instability was especially noticeable when scanning all files with Clamav: within a minute the computer would freeze. I decided to replace the chip with Ryzen 7 2600, add Nividia Geforce GTX GPU and reinstalled Ubuntu 18.04. Now, the complete Clamav scan finishes within 5 min. I'm a noob so I don't know why the Clamav would exaggerate the instability problem or maybe it was because I was running it on Ubuntu 19.04 (?). Anyway, thanks for all the comments. 

Mike

---

