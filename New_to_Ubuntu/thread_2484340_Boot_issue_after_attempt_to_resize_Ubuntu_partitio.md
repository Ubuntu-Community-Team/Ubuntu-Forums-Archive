---
title: "Boot issue after attempt to resize Ubuntu partition"
date: 2023-02-23
forum: New to Ubuntu
---

### Post by vermiou on 2023-02-23
Hello everyone,

I have a boot issue. When I boot Ubuntu, I'm sent to a GNU Grub command line prompt. Here is the diagnosis made with boot-repair:

[https://paste.ubuntu.com/p/qRWjgQxHQk/](https://paste.ubuntu.com/p/qRWjgQxHQk/)

I have a dual boot (Windows 11 / Ubuntu). And the problem came when I tried to resize the Ubuntu partition. Here exactly what I did:
- I followed this [tutorial]("https://lecrabeinfo.net/redimensionner-agrandir-reduire-une-partition-sur-linux.html") (it's in French)
- so I booted a live Ubuntu session from a USB drive
- I opened the terminal
- I typed the commands indicated in the tutorial
- I got stuck at point 9 in the tutorial, which is typing "e2fsck -f /dev/nvme0n1p4". But the terminal said I "hadn't the r/w permission or root" or something like that, so the command didn't work
- I tried typing something that wasn't in the tutorial (which was a very bad idea, I know... :( ): I typed "sudo e2fsck -f /dev/nvme0n1p4"
- then I retyped "e2fsck -f /dev/nvme0n1p4"
- then I rebooted the PC, and this is where the issue came

Thank you very much for your help!

---

### Post by tea for one on 2023-02-23
Line 65 - OS#1:   Windows 10 or 11 on nvme0n1p3

Conflicting info from boot-repair below
Line 135 - nvme0n1p4 637718528  952291327 314572800   150G [COLOR="#0000FF"]Linux filesystem[/COLOR]
Line 175 - nvme0n1p4 [COLOR="#0000FF"]ntfs[/COLOR]     66ACCA2BACC9F619                     876993de-3415-7b4e-91f6-22d4fbcd024c Nouveau nom 
Partition nvme0n1p4 is probably damaged
Boot-repair has only detected one operating system - Windows 11

Do you have data backups?
Can you boot into Windows?
If not, you will need a bootable Windows iso on a USB to repair the Windows Boot Manager.

As soon as you have successfully booted into Windows, let us know and we can help to repair the damaged partition and re-install Ubuntu.

---

### Post by vermiou on 2023-02-24
Thank you for your reply!

No I don't have backups of the data on Ubuntu.
Yes I can boot Windows without problems via the F12 key.

---

### Post by tea for one on 2023-02-24
Good news that Windows 11 is accessible via F12.

I would suggest:-

Boot into Windows and back up data (if you haven’t already done so)
Power off and ensure Windows is not hibernating/sleeping/encrypted
Boot into a live session of Ubuntu 22.04 in UEFI mode
Try and navigate to nvme0n1p4 - see if any data is recoverable and back up

Open Gparted and remove hidden flag from nvme0n1p1 (see line 115 – nvme0n1p1 hidenESP)
Tick flags esp and boot

Delete partition nvme0n1p4
Re-install Ubuntu in the free space via “Something Else” option 
Allow the installer to find the existing ESP nvme0n1p1

---

### Post by vermiou on 2023-02-24
Thank you very much! I'm not sure I'm capable of doing all of this, so I think I'm going to bring the PC to a computer repairer. Anyway thank you! I've really appreciated your help!

---

### Post by tea for one on 2023-02-24
> **vermiou said:**
>  so I think I'm going to bring the PC to a computer repairer.
The steps that I've suggested are not particularly onerous, if you approach it cautiously and diligently.
Let's try and do it slowly with forum support.

First, boot into Windows and back up your data.
When you are happy with the back up, revisit this thread with your progress.

---

### Post by vermiou on 2023-02-24
Okay, let's try! Your patience is very appreciable :)

Okay, I've just made a backup. Now how to make sure Windows is not hibernating/sleeping/encrypted after turning off the PC?

---

### Post by tea for one on 2023-02-24
While you are in a Windows session:-
To prevent encryption, turn off Bitlocker (it may already be disabled)
To prevent hibernation, navigate to Power Options and disable Fast Startup (if enabled)

Alternatively, when you power off Windows 11, press and hold the shift key
Pressing the Shift key tells the PC to do a full shutdown rather than a hybrid shutdown.

---

### Post by vermiou on 2023-02-24
Alright

Now, I know how to open a live session of Ubuntu, but don't know what UEFI mode is. How to make sure the live session is opened in UEFI mode?

Just for info, when I choose to boot with the USB drive, here are the options :
- try or install ubuntu
- ubuntu (safe graphics)
- OEM install (for manufacturers)
- Boot from next volume
- UEFI firmware settings

---

### Post by tea for one on 2023-02-24
After you have booted into a live (Try) Ubuntu session, can you open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

When you boot a USB device to install an operating system, you can sometimes have two options per device if both Legacy and UEFI are allowed in the firmware settings.
The attachment shows the two options.
You need the option beginning with UEFI: (i.e. UEFI followed by a colon)

---

### Post by vermiou on 2023-02-24
Okay, I ran the command and it printed "UEFI mode" so I guess we're good?

If so, could you please help me to navigate to nvme0n1p4, see if any data is recoverable and backup?

---

### Post by tea for one on 2023-02-24
> **vermiou said:**
> Okay, I ran the command and it printed "UEFI mode" so I guess we're good?
Yes, good progress
Open the file manager (Files) > Other Locations > Click /dev/nvme0n1p4
If it opens, backup any data you need.
If it doesn't open, it's probably damaged.
Let's see what happens............?

---

### Post by vermiou on 2023-02-24
It opens but there almost nothing in it. Just a file called 'WPSettings.dat' in a folder called 'System Volume Information'. Nevermind there wasn't any important files in this partition, so let's move onto next step

> Open Gparted and remove hidden flag from nvme0n1p1 (see line 115 – nvme0n1p1 hidenESP)
Tick flags esp and boot

Here's what I've just done
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291832&stc=1[/IMG]
Is it good?

If so, the next question I would like to ask you is how to delete partition nvme0n1p4?

---

### Post by tea for one on 2023-02-24
Yes, looking good - Two flags (boot and esp) ticked - not far to go now.

While using Gparted, right click /dev/nvme0n1p4 (will open a new menu) > delete

---

### Post by vermiou on 2023-02-24
Great!

The delete button isn't selectable (it's grey). There are few selectable buttons
- unmount
- name partition
- manage flags
- information

Here's what pops when I click 'Information'
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291833&stc=1[/IMG]

---

### Post by tea for one on 2023-02-24
The partition is still mounted
Choose unmount then delete

---

### Post by vermiou on 2023-02-24
Alright, done

> Re-install Ubuntu in the free space via “Something Else” option 
I'm configuring the installation
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291834&stc=1[/IMG]
What should I do here?

---

### Post by tea for one on 2023-02-24
I've never seen "Configure Secure Boot" before.
Secure boot is disabled in my system but that is my personal preference.

Anyway, do not unmount /dev/nvme0n1 because the disk contains the EFI System Partition (ESP), which is needed by Ubuntu.
Also, your free space is there
Press continue.

The next page - click "Something Else"
Select your previously created [COLOR="#0000FF"]free space[/COLOR]
Click the plus (+) sign to use the free space.
Format to ext4 file system
Mount point = / (i.e. system root)
No need for a separate swap partition - the Ubuntu installer will create a swap file

---

### Post by vermiou on 2023-02-24
Alright, we did it! Linux is now reinstalled and works perfectly!

Thank you so much for your help. You're a great explainer and without you I would still be annoyed with this boot problem right now. Thank you! :)

---

### Post by tea for one on 2023-02-24
Well done - I'm pleased to have helped.
Remember to backup your Windows and Ubuntu data regularly (if not daily)

---

### Post by vermiou on 2023-02-24
Understood, thanks for the advice

---

