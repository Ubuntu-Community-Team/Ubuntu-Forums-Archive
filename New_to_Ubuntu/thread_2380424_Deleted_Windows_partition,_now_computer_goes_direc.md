---
title: "Deleted Windows partition, now computer goes directly to BIOS"
date: 2017-12-17
forum: New to Ubuntu
---

### Post by softengi on 2017-12-17
I've been dual-booting windows 10 and xubuntu 16.04 for about a year  now. Recently, I had problems with Windows and was unable to use the  recovery option so I decided to simply format the partition where it was  installed. From that moment, every time I start my computer it goes  straight to BIOS, as if Linux was no longer installed.


  I tried using boot-repair from a live-usb. Here is the log:


  [URL="http://pastebin.ubuntu.com/26202232/"]http://pastebin.ubuntu.com/26202232/

[/URL]

  If you need more information about my problem, don't hesitate asking.  Right now I simply don't know what I should try or what information is  relevant to my problem... Thank you.

---

### Post by yancek on 2017-12-17
I'm not really sure what you did or deleted but given the output of boot repair, I would not expect you would be able to boot either the insalled Xubuntu or windows 10.  You are missing several partitions.  Generally, partitions are named in numerical order, sda1, sda2, sda3, etc.  You seem to be missing sda1, 3, 4, 5 and 8.  The boot repair software generally lists the boot files for windows and Xubuntu as well as the EFI files.  Your output shows an EFI partition on sda2 but does not show any of the boot files needed to boot windows.  You should have EFI files in the EFI partition for both windows and Xubuntu.

Boot the Live usb you are using and open a terminal and mount sda2 and take a look at or post the contents of that partition.

Step 1:  sudo mkdir /mnt/sda2
Step 2: sudo mount /dev/sda2 /mnt/sda2
Step 3: ls /mnt/sda2

You should show several folders including one labelled Microsoft and one Ubuntu.  Take a look at these folders or post the output here for help.

---

### Post by oldfred on 2017-12-17
You show sda2 as ESP - efi system partition, but also shows NTFS. The ESP must be FAT32 with boot flag.
If you can just change format, not totally reformat, then do so. You may be able to preserve the /EFI/ubuntu boot folder.
But ESP also has GUID and UEFI uses that GUID in the boot entry.

```
blkid entry:
 /dev/sda2: UUID="11EF39BC5B142530" TYPE="ntfs" PARTLABEL="EFI system partition" PARTUUID="[COLOR=#ff0000]dce91694-a75d-42ae-9d93-add23ad74abf[/COLOR]" 
UEFI entry:
      
 Boot0008* ubuntu    HD(2,GPT,[COLOR=#ff0000]dce91694-a75d-42ae-9d93-add23ad74abf,[/COLOR]0x12c800,0x96000)/File(EFIUbuntugrubx64.efi) 


```    

Not sure how you changed sda2 to NTFS, but it must be FAT32. And if you reformat it all the UEFI entries will not have correct GUID (PARTUUID).

---

### Post by leunam12 on 2017-12-18
I find strange that it goes to BIOS instead of giving you a black screen with a blinking cursor. But if you only need Ubuntu 
it is easier to format the drive entirely and re-install. If you need Windows and you have your COA sticker on your computer 
and the key is legible, then install Windows from scratch and activate it and fetch the drivers from the computer manufacturer's 
website. Then, install Ubuntu.

---

