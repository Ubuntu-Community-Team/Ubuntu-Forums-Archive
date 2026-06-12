---
title: "USB Boot Problem"
date: 2015-12-29
forum: New to Ubuntu
---

### Post by remote87 on 2015-12-29
Hi there!
This is my first step in Linux / Ubuntu / and there goes the first problem:
1.I used an USB flash drive / 2 gb /, downloaded the Universal-USB-Installer-1.9.6.2 / from [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/).
2.Downloaded Ubuntu 14.04 from the official site / I needed a 32-bit, because the machine I am using is a bit old /.
3.Changed my BIOS settings - boot from USB - HDD as a first choice.
And now all I get is this:
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot:
Now what? I have tried to google it but still nothing. Please help! :)
Thank you!

---

### Post by Bashing-om on 2015-12-29
remote87; Hello ; Welcome to the forum .

Did you verify the downloaded .iso file's integrity ?
What is the host operating system you are burning the USB from ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
As we have to have a known solid foundation to proceed.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Vladlenin5000 on 2015-12-29
Hi and welcome.

If your making the USB from Windows then prefer [Rufus]("https://rufus.akeo.ie/"). And irrespective of the tool used, make sure your downloaded ISO is fine.

---

### Post by brian-mccumber on 2015-12-29
I used pendrivelinux software to create a bootable usb drive from Windows right before I swapped to Ubuntu. The first one I made did not work, so I went back and redownloaded the ISO, come to find out the first ISO download was corrupted but the second worked just fine and I've used it to install Ubuntu on 3 computers so far.

---

### Post by remote87 on 2015-12-29
Ok, I have checked the hash with md5sum, used Rufus to make the new USB iso, the moment of truth...fingers crossed! :)

---

### Post by remote87 on 2015-12-29
Okkkkayyy....new problem.What the heck is this?!
[IMG]http://s27.postimg.org/6it253i9f/boot1.jpg[/IMG]

---

### Post by sandyd on 2015-12-29
Hi, was the USB drive formatted as FAT32?

---

### Post by remote87 on 2015-12-29
Yes, it was.

---

### Post by remote87 on 2015-12-29
[COLOR=#111111][FONT=Ubuntu]No matter what I do ( changed to GPT when using Rufus, renamed the isolinux folder to syslinux as well as the .cfg and the .bin files, tried all usb ports ) I still get the same window as in the attached file...It seem's that I am going to keep using windows after all :([/FONT][/COLOR]

---

### Post by leunam12 on 2015-12-30
What are your boot options in BIOS? I have found by experience that on some old computers that refuse to boot from USB, they boot if I select "USB Floppy Disk Drive" as my booting device from the temporary boot menu. Of course, I am not using a FDD, I still have the USB stick inserted. Another thing you can do is burn a DVD and see if it boots from it.

---

### Post by mörgæs on 2015-12-30
The screen shots indicates that you have some old hardware. Better to give it Lubuntu 15.10 than Ubuntu.

---

### Post by remote87 on 2015-12-30
leunam12, thank you for the advice. I will give it a try and will see what happens. The problem is that my CD rom is not working that's why I need to boot it from USB

---

