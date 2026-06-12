---
title: "Installation issues with Ubuntu 16.04.3"
date: 2018-01-11
forum: New to Ubuntu
---

### Post by sonicbunnny on 2018-01-11
Hello, I became interested in salvaging my old Laptop that Microsoft discontinued the Vista OS for. I thought it was gone and left it in the storage room for a few years, but recently found out that it is fully functional but lacks an OS. Hence, I tried out a free OS like Ubuntu (optional donation for developers). 

I have successfully used Rufus 2.18 to create a bootable usb flashdrive for Ubuntu 16.04.3 iso (64 bit). After rebooting, I am stuck at the installation types window that does not offer any options to use. I tried clicking (+) and (change) options for partitions, but the installation windows just freezes. 

For Rufus the settings are: MBR partition scheme for BIOS or UEFI for partition scheme, FAT32 for file system, 8192 bytes for cluster size.

What can I do to get ubuntu downloaded successfully? What other information should I provide (screenshots, logs, etc)? Or am I using the wrong ubuntu for this?

_**My Old Laptop's specs are:**_
[TABLE="width: 100%"]
[TR]
[TD]Type:[/TD]
[TD]Notebook/Laptop[/TD]
[TD]Hard Drive Capacity:[/TD]
[TD]160GB[/TD]
[/TR]
[TR]
[TD]Brand:[/TD]
[TD]Dell[/TD]
[TD]Operating System:[/TD]
[TD]Windows Vista Home Basic (Now it doesn't have an OS)[/TD]
[/TR]
[TR]
[TD]MPN:[/TD]
[TD]1500[/TD]
[TD]Processor Type:[/TD]
[TD]Intel Core 2 Duo[/TD]
[/TR]
[TR]
[TD]Screen Size:[/TD]
[TD]15.4in.[/TD]
[TD]Model:[/TD]
[TD]1500[/TD]
[/TR]
[TR]
[TD]Graphics Processing Type:[/TD]
[TD]Dedicated Graphics[/TD]
[TD]Processor Speed:[/TD]
[TD]1.40GHz[/TD]
[/TR]
[TR]
[TD]Memory:[/TD]
[TD]2GB[/TD]
[TD]Storage Type:[/TD]
[TD]HDD (Hard Disk Drive)[/TD]
[/TR]
[TR]
[TD]Hardware Connectivity:[/TD]
[TD]USB 2.0[/TD]
[TD]Product Line:[/TD]
[TD]Vostro[/TD]
[/TR]
[/TABLE]

---

### Post by dagorret2 on 2018-01-11
> [COLOR=#000000][FONT=Ubuntu]For best compatibility with newer hardware, keep the [/FONT][/COLOR]*Partition scheme and target system type*[COLOR=#000000][FONT=Ubuntu] set as [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]MBR partition scheme for UEFI[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]. However, if you need to use the USB stick with older hardware, change this to [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]MBR Partition Scheme for BIOS or UEFI[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu].[/FONT][/COLOR]

See this page: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

---

### Post by sonicbunnny on 2018-01-11
I already created a bootable drive successfully, but I'm stuck at the installation window for Ubuntu. My old laptop currently does not have an OS (the tutorial says I need windows XP or later). ["No root file system is defined" error during installation]("https://askubuntu.com/questions/135705/no-root-file-system-is-defined-error-during-installation").

[IMG]https://i.stack.imgur.com/JgFKp.png[/IMG]

Although this image is not from my laptop, but another user with the same problem. My window only has +, -, and change options above device for boot loader installation. I am basically stuck at this window.

---

### Post by mörgæs on 2018-01-13
What happens if you click *New partition table?*

---

### Post by RobGoss on 2018-01-14
From my experience I find Pendrive a good tool for creating a Bootable USB drive you can try it here [https://www.pendrivelinux.com/](https://www.pendrivelinux.com/)

What website are you downloading Ubuntu's ISO file from? you should always download Ubuntu's ISO files from their main website, [https://www.ubuntu.com/](https://www.ubuntu.com/)

Have you tried other versions of Ubuntu on this machine?

---

### Post by oldfred on 2018-01-14
Are you installing Lubuntu or Ubuntu.
I have a similar vintage Toshiba and did find newest Ubuntu worked, but most suggest the lightweight versions. 
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[URL="https://wiki.ubuntu.com/UbuntuFlavors"]https://wiki.ubuntu.com/UbuntuFlavors
[/URL] 

If using Something Else and no partitions already shown, drive is either blank or defective.
If you press + can you add your/ (root) partition ext4, 25GB? Then add 2GB swap at end of drive. And use rest as /home, ext4.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 

[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

---

### Post by galacticstone on 2018-01-14
I don't know if this will help or not, but I had a similar experience recently when trying to load 16.04 on to my wife's old HP laptop.

After installing from a USB stick, the system rebooted back to the installation menu instead of the new log-in screen.

So, from that installation screen, I hit the <Esc> key, which took me to the GRUB prompt.

From there, I issued a "reboot" command, which then took me to the usual log-in screen.

I think this is because on some machines the boot order is not properly reset by the installation, so it just keeps going back to the USB stick on reboot.

---

### Post by sonicbunnny on 2018-01-15
> **mörgæs said:**
> What happens if you click *New partition table?*

The only options I have are change, -, + on my window. I'll upload a screenshot of it with my phone within an hour. If I click "change" or "+" the window just stops responding. I can click "-" which gives me the option to skip the partition setup and install, but the OS is stuck downloading for hours when I left it overnight installing Ubuntu like that.

A better screenshot is in the attachment now.

> **RobGoss said:**
> From my experience I find Pendrive a good tool for creating a Bootable USB drive you can try it here [https://www.pendrivelinux.com/](https://www.pendrivelinux.com/)

What website are you downloading Ubuntu's ISO file from? you should always download Ubuntu's ISO files from their main website, [https://www.ubuntu.com/](https://www.ubuntu.com/)

Have you tried other versions of Ubuntu on this machine?

It's from the Ubuntu site. The file name is ubuntu-16.04.3-desktop-amd64. I tried Lubuntu as well, but this same issue occurs.

> **oldfred said:**
> Are you installing Lubuntu or Ubuntu.
I have a similar vintage Toshiba and did find newest Ubuntu worked, but most suggest the lightweight versions. 
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[URL="https://wiki.ubuntu.com/UbuntuFlavors"]https://wiki.ubuntu.com/UbuntuFlavors
[/URL]
If using Something Else and no partitions already shown, drive is either blank or defective.
If you press + can you add your/ (root) partition ext4, 25GB? Then add 2GB swap at end of drive. And use rest as /home, ext4.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 


I have not tried Ubuntu version 14 yet, but I did try the latest Lubuntu. I tried clicking the "+" button but the window just freezes and stops responding.

> **galacticstone said:**
> I don't know if this will help or not, but I had a similar experience recently when trying to load 16.04 on to my wife's old HP laptop.

After installing from a USB stick, the system rebooted back to the installation menu instead of the new log-in screen.

So, from that installation screen, I hit the <Esc> key, which took me to the GRUB prompt.

From there, I issued a "reboot" command, which then took me to the usual log-in screen.

I think this is because on some machines the boot order is not properly reset by the installation, so it just keeps going back to the USB stick on reboot.

I'll take a look at that. I did change the reboot priority and set usb stick/removable media as number 1.

---

### Post by oldfred on 2018-01-16
Is drive set for AHCI?
Was RAID (or Intel SRT) part of drive configuration. That has to be removed for partitioning to work.
Did in Windows you create more than 4 primary partitions. That converts drive to Microsoft proprietary dynamic partitions. That may leave data on drive also.
Did you ever use dd to directly install ISO to hard drive. That is not a standard format as hybrid DVD/flash drive configuration and first sector has to be erased to make drive usable. If nothing on drive, you can dd the MBR.
 Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446.
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1 



What does Disks show?
In Disks and icon in upper right corner is Smart Status. It can run lots of tests, but all I know is good/bad on drive.

---

### Post by sonicbunnny on 2018-01-24
I have tried Ubuntu 14.04.1 but I still get the same situation as the attached thumbnail above.

> **oldfred said:**
> Is drive set for AHCI?
Was RAID (or Intel SRT) part of drive configuration. That has to be removed for partitioning to work.
Did in Windows you create more than 4 primary partitions. That converts drive to Microsoft proprietary dynamic partitions. That may leave data on drive also.
Did you ever use dd to directly install ISO to hard drive. That is not a standard format as hybrid DVD/flash drive configuration and first sector has to be erased to make drive usable. If nothing on drive, you can dd the MBR.
 Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446.
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1 

What does Disks show?
In Disks and icon in upper right corner is Smart Status. It can run lots of tests, but all I know is good/bad on drive.

1. I am not sure, but it might be Intel since it is a dell similar to my other laptops.
2. I don't think I made 4 different partitions, but I do remember it had two drives prior to the Vista OS being expired. One was the main drive and another was the backup(?) of system files. It's been too long for me to be sure. 
3. I used Rufus to copy the iso onto a hard drive, then inserted it into my old laptop, then pressed f12 on the logo, then clicked install full ubuntu. What's dd mean? 

Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446.
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1 

Is this for the command prompt?

4. I used to get an error that "hard drive is not connected" or something in the past. I'll do the tests again from reboot screen.

---

### Post by oldfred on 2018-01-24
The dd command is a very powerful command that overwrites data with new data. It does not ask for checks and any typo causes major issues. Its nickname is Data Destroyer.
But it is often used to copy ISO to flash drives as Ubuntu ISO are a hybrid that works.
And then to get flash drive to work again as a partitioned drive, you have to use dd to erase first sector of drive.
I probably should not have posted that command until we knew that flash drive was in hybrid configuration and we wanted to reconfigure to a standard partitioned drive.

Post these from live installer.
       sudo parted /dev/sda unit s print 

 sudo fdisk -lu /dev/sda

---

### Post by sonicbunnny on 2018-01-25
Some additional infromation:

It used to use Intel (R) 82801 HEM/HBM SATA AHCI Controller driver looking at the old backup cd's. I also discovered that it was a 32 bit OS.

Also whenever I turn on the laptop, I get a hard drive not found error. Is this the issue? The hard drive is not connected or loose? I tried reinstalling the windows vista OS with the old backup cd, but it's not recognizing any drives there either.

I couldn't access the terminal from full installation, so I selected the try Ubuntu without installing option. I'm using ubuntu 14.04.1 LTS since it seems more compatible now. 

sudo parted /dev/sda unit s print results

Model: PNY USB 2.0 FD (scsi)
Disk: /dev/sda: 31950720s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number: 1
Start: 2048s
End: 31950719s
Size: 31948672s
Type: primary
File system: fat32
Flags: boot, lba

I attached the images as well for both results.

---

### Post by Yellow Pasque on 2018-01-25
> Also whenever I turn on the laptop, I get a hard drive not found error. Is this the issue?

Yes, if the BIOS can't detect the disk, the OS definitely won't detect it. Go into your BIOS or "system setup" and see if it detects the disk model.

> The hard drive is not connected or loose?

Or dead...

---

### Post by sonicbunnny on 2018-01-27
Under System Info I can see the system, bios version, and service tag. But under Device Info it says Primary Hard Drive is (none). What does that indicate? Any indications if the hard drive is dead? The laptop used for the Daycare to entertain toddlers, so its possible that it fell a few times.

Is it possible for an amateur to open it up and re-align the hard drive if it is loose?

---

### Post by oldfred on 2018-01-27
Only if it is a loose connection. Check cables both power & signal.

New hard drives are so precise it is just about impossible for anyone without very specialized equipment to recover data from hard drive.

One more reason why good backups must be standard procedure.

---

### Post by Yellow Pasque on 2018-01-27
> But under Device Info it says Primary Hard Drive is (none). What does that indicate? Any indications if the hard drive is dead? 

It indicates the motherboard doesn't detect the hard disk, which indicates you're probably in the market for a new hard disk.
It could be a loose/bad connector or a problem with the system board's SATA controller, but those are far less likely.

> Is it possible for an amateur to open it up and re-align the hard drive if it is loose?

It depends on the model. Usually, the hard disk is easy to get to. If it's a Vostro 1500, the 4 screws for the disk are accessible without removing anything (other than cord/battery as precautions).

---

### Post by sonicbunnny on 2018-01-28
Okay thank you everyone. I think you can close this forum topic now. 

[https://www.youtube.com/watch?v=ZILBkW7Zmfo](https://www.youtube.com/watch?v=ZILBkW7Zmfo)

I'll probably have to buy a new hard drive, then try it again. I'll post a new topic then if I have an issue.

The hard drive most likely being dead is the issue here.

---

### Post by tps-mail on 2018-01-29
I'm late to the party, but if you are still stuck, the button on the right of the +- that says New Partition Table, you may have better luck...

---

