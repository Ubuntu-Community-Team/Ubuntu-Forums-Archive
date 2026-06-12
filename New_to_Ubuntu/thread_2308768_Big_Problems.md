---
title: "Big Problems"
date: 2016-01-05
forum: New to Ubuntu
---

### Post by Mocton on 2016-01-05
Hello dear Ubuntu Community i had this problem with every distro i tried so maybe you can help me solve this.
First of all i can't connect to internet no matter what i tried everything.
when i try to creat my partition or simply install a distro i got this error: The attempt to mount a file system with type ext4 in SCSI5 (0,1,0).
Now i am trying to install Ubuntu 14.04.3 LTS and it wont enter into live mode from usb it get's stuck at the loading screen but before that i think it says something about failed PCC i am not sure it disappear to fast.

PC Specs:
Motherboard:Gigabyte GA-970A-DS3                 

Videocard:nVidia Geforce 9500 GT

HDD:Samsung 500GB

Ram:8GB

for internet i use the inboard Realtek GbE LAN chip
please help me figure this out

---

### Post by howefield on 2016-01-05
What a horrible post to read. Breaking your post up into intelligible sentences with full stops, paragraphs, ect, might help others to help you.

Try taking a step back, which operating system are you trying to install and what is the (first) problem ?

---

### Post by Mocton on 2016-01-05
i try to install ubuntu 14.04.3 LTS and i can't get into live usb or instlling it it stucks at the loading screen

---

### Post by grahammechanical on 2016-01-05
Do you see the first purple screen with an icon of a person and an icon of a keyboard? If you do press Enter at that screen. At the next screen select the language (the default is English) and press Enter. At the underlying screen press F6 - other options and a menu will appear at the bottom left of the screen. Select nomodeset and press enter. That will take you to a screen where you can select Try Ubuntu.

Here is a page which shows the screen images that you will see. Go to the heading Changing the CDs Default Boot Options and then go to Section 6 - F6 Other Options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You may need to select a combination of those F6 options. But selecting nomodeset might be enough. The installer might be having trouble detecting the optimum default resolution of the monitor which is stored in a chip in the monitor. The nomodeset option bypasses that action.

The live session loads using an open source video driver which should work fine with that GT950. When we install we are asked if we want also to install third party software. This software download includes useful audio and video codecs. It also includes a proprietary video driver. Your Nvidia card needs Nvidia 340 driver. And that is available. It is the one I am using for my GT220.

Regards.

---

### Post by Mocton on 2016-01-05
So i tried but it was useless so i downloaded the latest version but i still cant connect to the internet i have a wired connection obviosly i have a router for my laptop but my pc has a wierd connection sorry but i am not native english and it's hard for me to explain this and i still got that error when i am at partitioning 

PS:it shows that i am connected but i am not i tried to ping google and 8.8.8.8 and nothing i cant even connect to my router setup

---

### Post by yancek on 2016-01-05
It isn't clear from your post whether you are still trying to install Ubuntu from a usb or whether you have installed it and now have the problems with the internet.  Which is it?
If you are still trying to boot from the flash drive, how did you put the Ubuntu installation software on the usb, what software did you use for that?
You don't mention any other operating system so that means you have nothing on the drive presently, correct?

---

### Post by Mocton on 2016-01-05
i am on the ubuntu right now live from the usb i used unetbootin and i resolve the boot problem using the lates version of ubuntu the ideea is that in the live medium i can not connect to the internet it appears to be connected but it wont work i am sorry for my bad english i try to explain as i can the problem right now is that i can not connect to my wired connection and if i try to install ubuntu on my PC i got that error with:The attempt to mount a file system with type ext4 in SCSI5 (0,1,0) 
that kind of error i got on any distro i tried to install linux mint kali or arch

---

### Post by Bucky Ball on 2016-01-05
When you get to the partitioning section of the install, which option are you choosing? There should be a few. One of them is 'Something Else' to partition manually.

Is there anything on the drive you want to install to? If not, 'Try Ubuntu', launch Gparted at the desktop, delete any partitions on the drive by right clicking and 'delete', then try installing again.

---

### Post by Mocton on 2016-01-05
i tried something else to do it manually i found some instruction here on form but it was usless it did not work and when i choose to use the entire hard disk i got the same error

---

### Post by Bucky Ball on 2016-01-05
Without some details of what you tried and/or links to pages you're looking at, it is hard to give much help, sorry. You tried what else to do what manually?

---

### Post by Mocton on 2016-01-05
i tried to creat the partion on my own with the indication i got from [here ]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation")

Look sorry i will try to explain everything i did as best as i can.

1.it seems that i had some problems with my hard drive partition table some errors with the MBR i try to fix it right now with testdisk to see if that was the problem
2.I cannot connect to the internet from the live environment that ubuntu is providing and i don't know why and i need the be connected to the internet so i can download updates while i am installing but here we go to the first point with that error.

I tried many times to install a linux distro and i could not because of these to problems but now i am sick of windows i want something else and i truly want ubuntu i had ubuntu on virtualbox while i had linux and i like it but i want it to be my only os i do not want dual boot in the first post i have my specs i hope i make it clear now what it bothers me.

---

### Post by Bucky Ball on 2016-01-05
Have you tried plugging in an ethernet cable? That should get you online. Wireless doesn't always work in a live session. 

You don't need to download updates/upgrades when installing. You can do that later.

---

### Post by Mocton on 2016-01-05
i am runnin an wired connection so i do not care anymore but right now i have to fix my hdd somehow it seems that MBR is pretty ****ed up and now i do not know how to fix it

---

### Post by cariboo on 2016-01-06
For your internet connection problem, I'd suggest you try a different ethernet cable.

---

### Post by Mocton on 2016-01-06
I changed the cable still nothing, it's wierd because on windows i do not have those kind of problems

---

