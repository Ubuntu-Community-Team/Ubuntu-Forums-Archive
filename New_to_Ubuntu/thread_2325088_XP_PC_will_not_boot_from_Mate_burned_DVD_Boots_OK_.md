---
title: "XP PC will not boot from Mate burned DVD Boots OK from Burned Linux Lite 2.8 dvd"
date: 2016-05-19
forum: New to Ubuntu
---

### Post by rob162 on 2016-05-19
XP3
Pentium 4 3.0 GH
Mem 991MB
Intel 82915G/GV/910GL Graphics card
500MB HD

Both Linux Lite and Mate burned from desktop downloads with Express Burn (installed 5/8/16). Lite booted up OK from the DVD (I did not install it after boot up) Wanted to try Ubuntu Mate 16.04 desktop i386 on this computer, it will not boot from the DVD. I tried 2 different burned DVD from 2 different download sites. When I start the computer, goes straight to Windows XP

---

### Post by Quarkrad on 2016-05-19
A couple of things to try.  Have a look in your bios (normally press the Del button during boot) and see if the *boot order* of the pc is CD - Hd.  This is the 'normal' boot order and the pc should first boot to the CD first.   Second, on a lot of machines pressing F12 during the boot phase brings up a *boot order* window - from there you can arrow down to your CD.  Thirdly, install 16.04 Mate onto a memory stick and by pressing F12 boot from the stick (I used this method last week to upgrade three machines).

---

### Post by rob162 on 2016-05-19
DVD boot is first. The computer booted from the Linux Lite dvd. Right after that I tried booting from 2 different Mate DVD'S The computer would not boot from either one.  I tried Lite again, the computer booted to Lite

---

### Post by Quarkrad on 2016-05-21
Have you tried burning the iso to a memory stick and booting from the stick?   I use to burn CDs but many years ago started to use memory sticks - if there are any issues you can keep using the same stick rather than wasting CDs.  I use a product called UNetbootin to burn the image to a memory stick.

---

### Post by Impavidus on 2016-05-21
I prefer usb drives nowadays for live disks, but not al old computers boot from usb. And even if they're supposed to do, they may fail depending on an unknown function of usb drive brand and model, used usb port, tool to create the bootable usb and phase of the moon. Despite being a waste of blank dvds, booting from dvd should work.

Have you tried booting from the Mate dvds on a different computer? A newer one for example.

Have you used the [official download page]("https://ubuntu-mate.org/download/")? Have you checked the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of your download (not necessary if you used the torrent)?

---

### Post by mastablasta on 2016-05-21
Linux lite has different (older) kernel. Kernel is where the drivers are in linux.
from their DL page:
> **BASE:** Ubuntu 14.04.3 LTS

Is there a same issue if you use 14.04 Mate image?

furtheremore you can try with PLOP boot manager and create a boot CD (or a boot floppy) that will help you boot from USB, if this is not an option in BIOS.

---

### Post by rob162 on 2016-05-22
My 11 year old Pentium 4 computer does not have USB boot. For those saying I should just buy a newer computer. I have one. This a project computer used for XP Adobe Graphics software. My goal is to install Ubuntu Lite, or Mate to keep the old girl going for internet, and lite work, with more modern software. As I mentioned above. Lite will boot from the DVD. mastablasta mention that Lite has an older kernel made me think, maybe an older version of Mate will work. Or am I wasting time, because the CPU is too old for any version of Mate? And I should just use Lite.

---

### Post by mörgæs on 2016-05-22
There is no need for changing hardware but you could check if there is a newer BIOS available which supports booting from USB.

If you choose this or that distro is mostly a matter of taste. Just go for the latest release within each distro and keep applying updates. The kernel number is not that important for old hardware.

---

### Post by mastablasta on 2016-05-22
> **rob162 said:**
> My 11 year old Pentium 4 computer does not have USB boot.  

PLOP boot manager can boot from CD or floppy and then it will ask where to boot from (HDD, USB...). it's a great workarround for PC's that can't boot directly from USB. note that you can put multiple linux distros on one USB using Yumi for example.: Yumi USB multiboot USB creator: [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

PLOP boot manager: [https://www.plop.at/en/bootmanager/download.html](https://www.plop.at/en/bootmanager/download.html)
PLOP how to make bootable media (CD, Floppy...): [https://www.plop.at/en/bootmanager/plpbt.bin.html](https://www.plop.at/en/bootmanager/plpbt.bin.html)

> 
 Or am I wasting time, because the CPU is too old for any version of Mate? And I should just use Lite.

you can try Xubuntu. : [URL="http://xubuntu.org/getxubuntu/"]http://xubuntu.org/getxubuntu/
[/URL]Xubuntu screenshots: [http://xubuntu.org/screenshots/](http://xubuntu.org/screenshots/)


or try 14.04 version of Mate.

make sure you do md5sum check after download: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

if there is only one bit different than original image on server you will get issues.
the correct way is:
[LIST]
[*]download image 
[*]md5sum check 
[*]burn 
[*]verify burned data 
[/LIST]

md5sum check is not needed when you download via torrent as it does it on the fly.

---

### Post by rob162 on 2016-05-25
Solved!! I finally gave up on Mate. Saw an article written by Steven J Vaughan-Nichels  on ZDNet 3/31/2014. The article was about Mint as a replacement for XP. He recommended Mint 17.1 cinnamon 32 bit for older computer, instead of the newer 17.3. He was spot on. I downloaded the desktop fMint 17.1 rom their site, which was fairly fast, and burned a DVD with Express Burn. Just like Linux Lite, Mint booted right up. Looked great, I installed it next to XP. Installation was very easy. When I start the computer I have a chose of Mint or XP.
I wish I had tried Mint first. It feels good right from the start, for someone coming over from XP.

---

### Post by rob162 on 2016-05-25
Solved!! I finally gave up on Mate. Saw an article written by Steven J Vaughan-Nichels  on ZDNet 3/31/2014. The article was about Mint as a replacement for XP. He recommended Mint 17.1 cinnamon 32 bit for older computer, instead of the newer 17.3. He was spot on. I downloaded the desktop fMint 17.1 rom their site, which was fairly fast, and burned a DVD with Express Burn. Just like Linux Lite, Mint booted right up. Looked great, I installed it next to XP. Installation was very easy. When I start the computer I have a chose of Mint or XP.
I wish I had tried Mint first. It feels good right from the start, for someone coming over from XP. 
This newbe gives a hardy thanks to everyone for your help. Now if I can only find out to Tag post this as Solved.

---

### Post by RobGoss on 2016-05-25
> **rob162 said:**
> Solved!! I finally gave up on Mate. Saw an article written by Steven J Vaughan-Nichels  on ZDNet 3/31/2014. The article was about Mint as a replacement for XP. He recommended Mint 17.1 cinnamon 32 bit for older computer, instead of the newer 17.3. He was spot on. I downloaded the desktop fMint 17.1 rom their site, which was fairly fast, and burned a DVD with Express Burn. Just like Linux Lite, Mint booted right up. Looked great, I installed it next to XP. Installation was very easy. When I start the computer I have a chose of Mint or XP.
I wish I had tried Mint first. It feels good right from the start, for someone coming over from XP. 
This newbe gives a hardy thanks to everyone for your help. Now if I can only find out to Tag post this as Solved.

At the top of this thread there is a **Thread Tool** tab from the drop down menu you can choose the solved option from there

---

