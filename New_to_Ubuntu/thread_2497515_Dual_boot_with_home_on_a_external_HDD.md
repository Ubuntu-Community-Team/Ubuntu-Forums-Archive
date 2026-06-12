---
title: "Dual boot with home on a external HDD"
date: 2024-05-08
forum: New to Ubuntu
---

### Post by krassegrand2 on 2024-05-08
Hello!
My first post here.
I used to use the Swedish Ubuntu Forum but is seems to be down.
I have just bought a HP Pavilion Gaming Desktop TG01 / GTX 1650 / Ryzen 3 4300G / 8GB / 512GB NVMe with Windows 11.
I would like to install Ubuntu, dual boot and thinking about to have the Home or the entire Ubuntu on a different hard drive. 
Is that a stupid idea?
I have earlier (a long time ago) installed a dual boot (Windows and Ubuntu) with separate home but still would like a detailed instruktion.

Have a nice evening guys,

Jörgen

---

### Post by oldfred on 2024-05-08
I have both.
But always keep /home (only) in / (root) so user settings are on fastest drive and always available. 
I do keep a large data partition where main working install of Kubuntu is on NVMe drive. 

But I also have two external SSDs. I updated SSD in desktop to NVMe drive and moved M.2 SSD drive to USB adapter. That has worked so well I bought another NVMe drive & USB adapter, and now do not plan on more USB flash drives as I have a lot already, larger ones with full install & data.
Full installs on external drives with copies of data in separate data partitions.

I have used UEFI install of Kubuntu with Dell laptop, my 2017 desktop build, and even with my 2006 BIOS only laptop. I put BIOS boot stanza on old laptop to directly boot external install.

Kubuntu is a bit  lighter weight  than standard gnome based Ubuntu, so I find it works a bit better. But user choice of gui is what Linux is about.

External drive install details depend on version.
Older versions used Ubiquity installer that only installs grub to first drive's ESP, unless you do one of many work arounds.
New versions of Ubuntu use Subiquity installer that gives choice.
Kubuntu used Ubiquity until 24.04 and now uses Calamares installer which works correctly. Already installs to second internal drive & external SSD.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)  & 
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
[https://ubuntuforums.org/showthread.php?t=2488332&p=14149243#post14149243](https://ubuntuforums.org/showthread.php?t=2488332&p=14149243#post14149243)
Label=WD1 /d/WD1 ext4 defaults,nofail,nodev,nosuid,noexec  0 2

---

### Post by krassegrand2 on 2024-05-09
I have a Ubuntu image on my old laptop and a 8Gb USB that was read protected and I tried to clear it with Gparted but no luck so I tried the advise on the link. 

[https://www.pcforalla.se/article/1713390/hur-raddar-jag-mina-forstorda-usb-minnen.html](https://www.pcforalla.se/article/1713390/hur-raddar-jag-mina-forstorda-usb-minnen.html) 

It worked fine to assign but then I had a USB that eater Ubuntu or Windows can detect.

I might back when I have bought a new USB.

---

### Post by grahammechanical on 2024-05-09
If you do decide to dual boot Windows and Ubuntu on the same drive remember to use Windows tools to work on Windows file systems/partitions. Defrag Windows before and after expanding/shrinking/moving Windows partitions. Create unallocated space. Make sure Windows still loads. You may need to use a Windows rescue disk.

Use Linux tools to create Linux (EXT4) partitions. The Try Ubuntu session has GParted that will create/resize Linux partitions. You can select the Install Alongside options if you want. I have not ever tried that with a dual boot with Windows. So, I cannot predict the results.

I would suggest that installing on a separate drive is preferable. Disable or disconnect the Windows drive.

Regards

---

### Post by krassegrand2 on 2024-05-10
Sounds resonable!
I am on hold now until I get a new USB stick.

---

### Post by krassegrand2 on 2024-05-10
Now I have bootable stick and have tried it on the new used desktop.
Now I need to know exactly how to set up the installation to get a separate home and a dual boot with the Windows 11 that is already on the desktop.
I have in the past made a dual boot anda a separate home but I did not get it all right. the home partition stayed empty but the partition with the installation got full after a while.

Any step by step instructions that You can recommend?

---

### Post by psychohermit on 2024-05-10
I like to keep /home on a separate partition.  That way it can survive a reinstall and 90% of your customization is left intact.

--glenn

---

### Post by krassegrand2 on 2024-05-10
Does that mean that I choose "something else" during the install?
I think I need some more help.

---

### Post by tea for one on 2024-05-10
> **krassegrand2 said:**
> I would like to install Ubuntu, dual boot and thinking about to have the Home or the entire Ubuntu on a different hard drive. 
Is that a stupid idea?
No, not a stupid idea.
If you are new to using Ubuntu on a separate disk, it's easier to allow the installer to automatically create the necessary partitions i.e. entire Ubuntu.
> **grahammechanical said:**
> Disable or disconnect the Windows drive
Kindly confirm that you can follow this excellent suggestion?
It will prevent any untoward catastrophe during installation

---

### Post by krassegrand2 on 2024-05-10
> **tea for one said:**
> 
Kindly confirm that you can follow this excellent suggestion?
It will prevent any untoward catastrophe during installation


That is a good idea, maybe I should get another hard drive before I install?
On the other hand, I don't have any important personal info on the Windows partition.

One question, If I disconnect the Windows drive while installing Ubuntu, do I still get a GRUB?

---

### Post by oldfred on 2024-05-10
You have grub, but if only one install, menu should not normally appear. 
If abnormal shutdown or some issue menu may appear so you can use recovery mode to make repairs.
Or you can change grub settings to have menu appear.
And with UEFI/gpt install, you can press escape near beginning of boot. After UEFI/BIOS screen, but before grub menu normally would appear.

---

### Post by krassegrand2 on 2024-05-10
I still need to know exactly what the partitions need to be named, if I want a separate home.

Am I close with these suggestions?

[COLOR=#282828][FONT=Arial]fat /boot/efi[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]ext4 /[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]ext4 /home[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]linux-swap[/FONT][/COLOR]

---

### Post by tea for one on 2024-05-10
Yes, you are close but you do not need to make a swap partition.
The Ubuntu 24.04 installer will automagically create a swap file.

---

### Post by krassegrand2 on 2024-05-12
I have installed now Dual boot but not separate home.
How do I find the programs like Synaptic and Terminal?

---

### Post by tea for one on 2024-05-12
Terminal is included in Ubuntu 24.04
Show Applications > Help > Start Applications

Synaptic is available via the App Centre
App Centre > Search (type synaptic) > Filter by Debian packages
Alternatively, via the terminal
```
sudo apt install synaptic
```

---

### Post by krassegrand2 on 2024-05-12
Great! Thanks!
I have now found the terminal and have Gparted ans synoptic installed.

How do I choose my desktop settings? I would like to have the X for closing in the left corner among other things.

---

### Post by krassegrand2 on 2024-05-12
I found the startup application but I can't get the command right, or at least Thunderbird wont start on startup.
I have seen on my laptop that the command is "/usr/bin/thunderbird " but on the new instillation there is no thunderbird file in that folder.
I have found loads of files named thunderbird and have tried a few of them but no luck.
How do I know witch of the files starts Thunderbird?

---

### Post by krassegrand2 on 2024-06-05
I have the Thunderbird on startup now.
Thanks for the help.

---

### Post by psychohermit on 2024-06-07
IF you disconnect the ******* drive the OS PRober won't find ******* to make a boot provision for it.

--glenn

---

