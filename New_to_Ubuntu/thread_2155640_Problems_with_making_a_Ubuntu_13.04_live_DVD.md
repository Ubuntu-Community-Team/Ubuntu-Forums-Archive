---
title: "Problems with making a Ubuntu 13.04 live DVD"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by phoenixpenguin1 on 2013-06-18
Hello Ubuntu! I am new to Linux but I am not completely clueless about it. I am not sure which distro to start out with first (its between Mint and of course Ubuntu). I want to see which distro fits my preferences/hardware so I want to make a live DVD of each distro. I decided to make the Ubuntu live DVD first so I followed the instructions on the Ubuntu website. Once I had the live CD file downloaded, I tried to burn the file onto the DVD like the Ubuntu website instructed ([http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)) using Windows Disc Image Burner. When I actually tried to burn the DVD, the program said "The selected disc image file isn't valid." I am not sure how to fix this problem and would love to get started with this live DVD to test out Ubuntu for myself. In case you guys were wondering, I am trying this on a HP computer running Win 7 Home Premium and I am trying to burn it on a DVD+R.

---

### Post by critin on 2013-06-18
USB sticks and unetbootin are easier.  (for me)

---

### Post by Impavidus on 2013-06-19
Have you checked the MD5 sum? That error sounds like there is no valid partition table or whatever it is called on optical media.

---

### Post by phoenixpenguin1 on 2013-06-19
I've checked the MD5 sum and it is different from the one that is listed from Ubuntu. How do I fix it and where do I go from here?

---

### Post by craig10x on 2013-06-19
When i got my new computer, before i removed windows, i was running windows 7 for a while and installed a really nice (free) cd/dvd disc burner called cdburnerxp....i made my ubuntu iso using that to burn my disc...so perhaps you should install that and it may work better for you then using the default windows burner...Also, when you burn it, select the slowest burn speed like say 2x or 3 x....And you would also need to change your bios settings (when you first boot up) to boot off a cd/dvd first, that way when you restart it will boot off the live iso...once in it, you will be able to select to "try ubuntu" first on the live session without installing...

[http://cdburnerxp.se/](http://cdburnerxp.se/)

If you get into the live session ok and want to do a little web surfing, go to the software center and install the ubuntu restricted extras so that all the codecs and flash will be added on to the live session...of course, when you actually install you will need to do that again (lol)...When installing, you could either have it wipe windows and replace with ubuntu or dual boot ubuntu side by side with windows...

---

### Post by Zill on 2013-06-19
> **phoenixpenguin1 said:**
> I've checked the MD5 sum and it is different from the one that is listed from Ubuntu. How do I fix it and where do I go from here?
If the [MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM") for your downloaded file is different to that listed on the Ubuntu website then you have a corrupted download and it is pointless burning a CD/DVD unless the MD5 sum *exactly* matches.

You need to [download the Ubuntu iso]("http://www.ubuntu.com/download/desktop") file again.

---

### Post by Rob Sayer on 2013-06-19
Ditto on downloading again.  The file's corrupt, which is what a different md5sum result means.  Try the torrent download.  It's a more reliable method.

And, as a former Mint user, I would definitely recommend ubuntu over mint for an inexperienced user.  Mint tech support on their forums is *pitiful* compared to ubuntu's.

---

### Post by wc711 on 2013-06-19
I just installed 13.04 and the only problem I had was the Nvidia graphics driver, which I was able to handle with the additional drivers icon.  Difficult to read the screen until I got the driver loaded.   As for installing, I just downloaded the 13.04 iso file then burned it to a fresh DVD+R the I opened the a program called Penn Drive which will install 13.04.  It gives you plenty of options as you go along.  I chose the partition option which open up a partition screen that shows you your partitions and has a slide that lets  you adjust the sizes.  Once that is done, just click install and Penn Drive installs it.
[URL="http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"]Universal USB Installer – Easy as 1 2 3 | USB Pen Drive Linux 

[/URL]

---

### Post by phoenixpenguin1 on 2013-06-19
The Linux Mint live DVD booted with no problems. I'm going to try to download the iso file one more time. If that does not work, I'll just download the torrent version.

---

### Post by craig10x on 2013-06-19
Good idea...i forgot to mention that...bad md5 sum means not a good download so definitely do it again...if standard download isn't good...try torrent...

---

### Post by mastablasta on 2013-06-20
torrent does a md5 sum checkup while downloading. so it has higher chance that the download will be perfect.

---

