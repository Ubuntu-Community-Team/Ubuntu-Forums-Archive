---
title: "I can't get Windows 7 and Lubuntu to Dual Boot"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by Lee_Smith on 2014-05-19
This Question maybe already answered in another thread but I couldn't find it! **[Why won't my windows 7 dual boot into Lubuntu ?]("https://uk.answers.yahoo.com/question/index?qid=20140518125202AArfwXH")**


[FONT=Helvetica Neue][COLOR=#000000]I have a a year old laptop running Windows 7 home premium and I installed Lubuntu from a usb drive. I wanted to set-up a dual boot so I chose the option to install Lubuntu along side Win7. Although the install went well and the partition was created successfully my computer just install straight into windows 7 and there seems to be no option to select which OS to boot into. I've never attempted a dual boot before or another OS so I hope someone can help me with clear easy to follow instructions. Thank you.[/COLOR][/FONT]

[FONT=Helvetica Neue][COLOR=#000000]When I asked this question on Yahoo Answers  This was the reply:  You need a Windows boot loader and not the one Linux Uses. This is a common issue with dual booting some systems, with vista, windows7 and windows 8 because of the format of the Windows hard drive. I run into this issue several different times with Linux as an operating system.[/COLOR][/FONT]

[FONT=Helvetica Neue][COLOR=#000000]So I'd like to know the following:  [/COLOR][/FONT][FONT=Helvetica Neue][COLOR=#000000]Okay so how do I setup Windows boot loader/can I fix this or do I have to re-install Lubnbu? If a re-install is required I do I set it up so it uses windows boot loader?  I don't know which version of Lubuntu I have but it should be the latest version for AMD 64 bit.[/COLOR][/FONT]
[COLOR=#000000][FONT=Helvetica Neue]
[/FONT][/COLOR]

---

### Post by jones quest on 2014-05-20
Sometimes UEFI can cause problems with the bootloader (grub). 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You should check if you have fastboot/quickboot enabled in the "bios" and disable it. You can then run boot-repair to fix problems with grub. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2014-05-20
I do not suggest the EasyBCD route as it makes grub less reliable and uses grub4dos to chainload to grub2. A few who are primarily Windows users have used it with Windows 7 and say it works.

But grub is designed to boot multiple systems. If you are booting Windows either you have a UEFI system and did not change selection in UEFI to boot ubuntu entry or grub did not install correctly.

May be best to see details. Post link to BootInfo report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jerrylamos on 2014-05-23
I have Lubuntu 64 and Windows 7 running dual boot (actually, many boot, various partitions running Utopic, Tahr, ...)

I install Lubuntu to the USB drive, actually a 2.5" left over laptop drive in a $10 case from Amazon or Tiger Direct.

Beforehand I have a partition picked out to use on the USB drive.

I select "something else" option ("alongside" and "guided" don't do what I want and have screwed up for me).

Install the Lubuntu into the chosen partition on the USB drive.

Install wants to put the boot loader wherever, I select the USB drive.

My netbook and notebook are set to boot from the USB drive first if connected.

Grub as installed on the USB drive then lists the expected bunch of partitions including Lubuntu and also the Windows 7 loader.

Now this is lubuntu utopic.  I'm usually running development level ubuntu's since Dapper Drake. bugs, crashes, and all.

Therefore I have an exec I call "setup" that does my personalization mostly automatic.  I expect to do an install on one pc or another every couple weeks.  No big deal.

---

