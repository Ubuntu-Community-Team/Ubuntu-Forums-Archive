---
title: "Grub error 15, can't boot...."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Kanaric on 2008-04-23
I had this problem for a while and was able to bypass it by booting from cd and selecting "first hard drive" and then i would have no problem.

I had a game that wouldn't run under Wine so I installed Windows on a separate hard drive that I had nothing in, now the CD boot way of doing things no longer works.

How can I fix grub error 15? Aside from that the OS was working perfectly, aside from the fact that when the OS boots the screen would be blank until the login screen but that is a separate issue.



I assume it has something to do with my hard drive setup. I am running 3 hard drives at the moment, 2 IDE and one SATA. The SATA drive is my linux partition. 

I have a Asus P5N-E SLI motherboard if that makes any difference.

---

### Post by phidia on 2008-04-23
When you install windows it presumes it's the only OS and sets up the MBR to boot windows. To get the grub menu back again boot from the cd you used for the ubuntu install and chose the re-install grub option or get the [super grub disk]("http://www.supergrubdisk.org/").

---

### Post by jeffemmert on 2008-04-23
I'm having a similar problem on a laptop with 2 hard drives. C: has XP Pro and F: has Ubuntu 7.10. When I initially installed Ubuntu, it loaded the Grub on C:, giving me the option at boot. After loading Mandriva Spring 2008 on an older machine, I liked it so much better, I decided to replace Ubuntu on the laptop (Ubuntu wasn't driving my ESS Allegro 1988 sound card correctly - left channel only). The problem was, Mandriva wouldn't completely install on the laptop and at reboot, all I got was error 2 or error 15 from Grub. To fix that, I tried reinstalling Ubuntu 7.10 from its live CD (which runs the audio fine, even though the installed version doesn't). After installing Ubuntu this second time, rebooting still results in Grub Error 15. Booting from the Live CD and checking its options (as mentioned in your previous post) doesn't show me anything about reinstalling Grub. How else could I fix this?

---

### Post by annda on 2008-04-23
this will take some reading, but it's worth it:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by jeffemmert on 2008-04-23
:KS:KS:KS Thank You!!! :KS:KS:KS
I got that SuperGrub CD burned on the older machine (first day with Mandriva Spring - still discovering) while reinstalling Ubuntu 7.10 on the laptop (third try). This time, by some miracle, Grub started working on its own, recognizing both OSs.

---

### Post by Kanaric on 2008-04-25
> **phidia said:**
> When you install windows it presumes it's the only OS and sets up the MBR to boot windows. To get the grub menu back again boot from the cd you used for the ubuntu install and chose the re-install grub option or get the [super grub disk]("http://www.supergrubdisk.org/").

Ok I will try that, I just want to make a note though that grub was doing this BEFORE windows installed just that I had to boot from the Ubuntu install CD and select "boot from first hard disk" in order to get grub to not give that error.

---

### Post by oloapota on 2008-04-25
> **Kanaric said:**
>  Aside from that the OS was working perfectly, aside from the fact that when the OS boots the screen would be blank until the login screen but that is a separate issue.




About this you should check this page, it's a known bug in 7.10
Also, boot up time will probably be faster afteryou make these changes
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/152726](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/152726)

---

### Post by JAGGEDSPHERE on 2008-04-25
Attempted installing HH last night. Error 15. I will try this when I get home tonight.

---

### Post by bobpur on 2008-04-28
For what it's worth, I had a similar problem with this machine. GRUB would not function correctly. Sometimes I would only get a black screen with the word GRUB and a blinking cursor. I could boot with the Super GRUB cd but that didn't fix the problem.
Finally, I looked in the BIOS. I have an ASUS A8N-32SLI Deluxe mobo. As I like to tinker, I figured I may have screwed something up in the BIOS at one time or another. I pressed F7 which reset the BIOS to the default settings and BANG! GRUB worked fine, flowers bloomed, birds sang and all was right with the world. Heck, I think gas prices may have even fell one or two cents. :) :) Alright, maybe I went too far with the gas price thing. :)
Anyhow, check your BIOS settings. I, honestly, don't know what was fixed when I hit F7 but it worked. F7 might not do the same thing on your board as mine so check it out first as this will really bork a machine if you're not careful.

Good Luck!

---

