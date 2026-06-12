---
title: "Trying to install ubuntu from DVD - &quot;Selected boot device failed&quot;"
date: 2015-06-01
forum: New to Ubuntu
---

### Post by henry46 on 2015-06-01
I'm trying to install Ubuntu 14.04.2 64-bit on my Dell Latitude e6420. I downloaded the ISO, burned it to a DVD using windows explorer, and then tried to boot from it and got the message "Selected boot device failed. Press any key to reboot the system." I tried burning to another DVD and got the same problem. Any suggestions on what to try? I'm struggling to figure out where the problem could be - I deliberately used a DVD instead of a USB since USB's tended to be finicky whenever I use them, whereas with DVDs it's a very straightforward download -> burn -> boot.

---

### Post by leunam12 on 2015-06-01
Did you follow instructions from the Ubuntu website?

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

Maybe you have to enable legacy boot on BIOS

---

### Post by sudodus on 2015-06-01
Welcome to the Ubuntu Forums :-)

You need to 'burn an ISO image', which is different from making a data DVD with the iso file.

If you boot into Windows and insert the DVD disk, what do you see in Explorer?

- a lot of directories and files in the DVD? - this is correct.

- one big file, 'Ubuntu-something.iso' - this is wrong.

I'm quite used to USB boot drives, and prefer that method to using DVD disks. But both methods should work. See these links.

[http://www.wikihow.com/Burn-ISO-Files-to-DVD](http://www.wikihow.com/Burn-ISO-Files-to-DVD)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

 [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by henry46 on 2015-06-01
> **leunam12 said:**
> Did you follow instructions from the Ubuntu website?

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

Maybe you have to enable legacy boot on BIOS

Yep. It gave me slightly different options than in the tutorial (it gave me the choice between burning as a USB or as a CD/DVD - I chose CD/DVD). I am booting via legacy. Going into the boot options lists everything under the "legacy" section - if I go to the UEFI section, there aren't any options listed.

---

### Post by henry46 on 2015-06-01
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

You need to 'burn an ISO image', which is different from making a data DVD with the iso file.

If you boot into Windows and insert the DVD disk, what do you see in Explorer?

- a lot of directories and files in the DVD? - this is correct.

- one big file, 'Ubuntu-something.iso' - this is wrong.

I'm quite used to USB boot drives, and prefer that method to using DVD disks. But both methods should work. See these links.

[http://www.wikihow.com/Burn-ISO-Files-to-DVD](http://www.wikihow.com/Burn-ISO-Files-to-DVD)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

 [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

That must be the issue - it's just showing one big file. How do I fix that? Obviously I have to use a new DVD, but I'm not sure which methods of burning will result in one big file or all the directories.

---

### Post by sammiev on 2015-06-01
Hi henry46 and welcome,

I see sudodus gave you choices of DVD/USB. 

USB if you have one will save you the cost from burning another DVD.

It doesn&#8217;t really matter which way as they both work and all the answers are in the 1st 2 links.

If you still are having problems after reading those links, please ask.

---

### Post by sudodus on 2015-06-02
> **sammiev said:**
> Hi henry46 and welcome,

I see sudodus gave you choices of DVD/USB. 

USB if you have one will save you the cost from burning another DVD.

It doesn&#8217;t really matter which way as they both work and all the answers are in the 1st 2 links.

If you still are having problems after reading those links, please ask.

+1 ... or more directly, these two links:

[http://www.wikihow.com/Burn-ISO-Files-to-DVD](http://www.wikihow.com/Burn-ISO-Files-to-DVD)

[https://help.ubuntu.com/community/In...n/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Good luck :-)

---

### Post by RobGoss on 2015-06-02
I have used a number do DVD's for just about every distor that Ubuntu has but I almost always use a USB drive for my installations because they seem to be more reliable and the fact that you can just format them and burn yet another ISO is great.

---

