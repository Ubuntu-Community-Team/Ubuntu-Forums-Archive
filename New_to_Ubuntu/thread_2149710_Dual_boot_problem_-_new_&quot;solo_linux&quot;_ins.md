---
title: "Dual boot problem - new &quot;solo linux&quot; installation the solution?"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by swehels on 2013-05-29
[FONT=arial]Hi 

I messed up as I tryed to install Ubuntu alongside Windows. After installation i just got to "grub rescue" but after runing boot-repair I get to the grub menu... from there nothing will start and when I try to start Ubuntu i just get: 
[COLOR=#444444][B]
Kernel panic[/B][/COLOR][COLOR=#444444] - not syncing: [/COLOR][COLOR=#444444]**No init found**[/COLOR][COLOR=#444444]. Try passing[/COLOR][COLOR=#444444]**init**[/COLOR][COLOR=#444444]= option to kernel

I tryed a couple of commands to repair MBR -  but frankley - [/COLOR]I don't have knowledge, skill or any idea of what I´m doing... 

Im stuck and just need to get the comuter to work whit any os.

- Can I just make a new installation of Ubuntu to write over Windows and any old installation? 
[COLOR=#444444]
 [/COLOR][/FONT]

---

### Post by arpanaut on 2013-05-29
Can you post:  The specs. of your computer, what Win OS, what options you chose on installation.
Do you have the pastebin link that boot repair gave you, If not run again and provide link.

---

### Post by swehels on 2013-05-29
It´s a Intel i5 - 128 SSD, Windows 8 - upgraded from windows 7. Its a acer whit at couple of partions - look att the link below... i just used the partion tool as I installed Ubuntu. 

I tryed to install it "alongside" on an Windows 7 computer (amd 64) and it worked fine so I just did the same thing whit the other one since its a Windows 8 upgrade, not preinstallation.  


boot-repair:

[http://paste.ubuntu.com/5711440/](http://paste.ubuntu.com/5711440/)

---

### Post by Bashing-om on 2013-05-29
[COLOR=#000000]swehels;

I am no longer knowledgable in respect to Windows, But I have seen the following advise several times;

In windows make up the partition that ubuntu is to be installed onto, (older scheme max of 4 primary partitions)
Then defrag windows at least twice, and run Windows' check disk utility,
Make sure "UEFI" is not a factor,
Determine Windows' partitioning scheme ...is GPT a factor (where does grub get installed to ?)? 

Once the Prior Prudent Planning is done -> then install ubuntu 
[/COLOR][INDENT=2][COLOR=#000000]
just hope this helps

[/COLOR][/INDENT]

---

### Post by swehels on 2013-05-30
I can´t seem to access uefi - legacy via bios (insydeh20 3.7) and i can´t start windows... is there any ofter way? USB Ubutu?  


[COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of     the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks     [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos6[COLOR=#666666])[/COLOR]/boot/grub on this drive. [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]4.04 and higher[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb.

---

### Post by swehels on 2013-05-30
BTW: Thanks for the input!



...back to the starting question, will this salve my problem:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

What will happen if i reinstall linux 12.04 from usb and chose the "replace" option?

---

### Post by mastablasta on 2013-05-30
you will overwrite the current ubuntu install.

if the USB disk is ok then it should work unless you need to do some special setup.

what is : /dev/sda8       233291776   250066943     8387584   84  OS/2 hidden C: drive

Are you sure you have less than 4 primarry partitions? Do you actually use UEFI? you said mashcine has windows 7 they didnt' have UEFI usually. if they did i think the solution was a boot partition.

---

### Post by swehels on 2013-05-30
I don´t think I have UEFI - but even if I did woldent it be possible to just write over eveytking whit a fresh linux installation and get the maschine to work?


[COLOR=#000000]what is : /dev/sda8 233291776 250066943 8387584 84 OS/2 hidden C: drive  [/COLOR]
I think it said "hybernation partition" or something like that when i looked at the disk prior to the installation...

---

### Post by grahammechanical on 2013-05-30
Of course you can choose the installation option of Erase Disk and Install Ubuntu. It is a simple if brutal solution. It is your choice.

I think that people giving advice here do not recommend it because we have seen too many posts where someone says that they have removed Windows and now they have changed their minds. And then they expect us to tell them how to put Windows back when they do not have Windows installation disks.

We also like to fix things, which can take longer and runs the risk of making things worse. So, even with Ubuntu a re-install is sometimes the easiest and quickest fix.

Regards.

---

### Post by swehels on 2013-05-30
[COLOR=#000000]We also like to fix things, which can take longer and runs the risk of making things worse.
[/COLOR]
- Sounds good, but what shuld I try to do then? get Windows to boot to fix the partitions?

---

### Post by swehels on 2013-05-31
Ok, heres how the hard drive and grub look like: 



And from boot-reparir: [http://paste.ubuntu.com/5711440/](http://paste.ubuntu.com/5711440/)



Linux error = Krenel-Panic init is missing 

Windows error = unrecognized file system -> grub rescue

windows recovery will load and run but wont change anything it seems... 

What do I do next?

---

### Post by swehels on 2013-05-31
Ok, heres how the hard drive and grub look like: 

[ATTACH=CONFIG]243321[/ATTACH]
[ATTACH=CONFIG]243322[/ATTACH]
And from boot-reparir: [http://paste.ubuntu.com/5711440/](http://paste.ubuntu.com/5711440/)


Linux error = Krenel-Panic init is missing 

Windows error = unrecognized file system -> grub rescue

windows recovery will load and run but wont change anything it seems... 

What do I do next?

---

### Post by presence1960 on 2013-05-31
If windows is on an SSD do not run Defrag! An SSD saves files differently than a HDD, no need to defrag. Also defrag will waste precious read/write cycles and hasten the end of your SSD as it gets closer to it's read/write cycle limit.

---

### Post by presence1960 on 2013-06-01
Your windows is not installed to a primary partition. You have the System Reserved at sda2. This contains the windows OS boot files. It is marked as boot which it should be. However you have no other primary NTFS partitions. Windows must be on a primary partition, not on a logical partition.

---

