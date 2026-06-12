---
title: "Can't boot after clean install - here's my Boot Repair results"
date: 2015-11-23
forum: New to Ubuntu
---

### Post by tom214 on 2015-11-23
EDIT - I've solved my boot problem. (no further help needed on post below). I think my solution was a combination of messing around with a Super Grub2 ISO on usb, and then following oldfred's terminal commands in post #2 here: [http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408).  On the Super Grub2 usb I found a grub repair option or some such. I ran it, then afterwards tried oldfred's post. I'm not sure if SG2 made a difference, as I had not tried oldfred's post beforehand.

Another oldfred success story :)  Thanks all.

=======================================================

Hello All,

Here's my boot repair results:
[http://paste.ubuntu.com/13465465/](http://paste.ubuntu.com/13465465/)    (plus see attached photos of Gparted)[ATTACH=CONFIG]265740[/ATTACH][ATTACH=CONFIG]265741[/ATTACH]

Result highlights:
[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/sda.

[COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]4.04 and higher[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb.  (I Think this is my live USB)

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/sda1 already mounted or /mnt/BootInfo/sda1 busy
mount: /dev/sda2 already mounted or /mnt/BootInfo/sda2 busy

Here's my details:
- had Unbuntu 14.04 running on new Toshiba laptop. I had similar no boot problem before after install, but can't recall how I fixed it.
- used live USB to wipe drive with Wipe utility
- used live USB to do clean install with Full Disk Encryption, chose not to overwrite blank space. No other OS on PC.
- I can access the PC's BIOS settings to change boot order or select UEFI vs. CSM.
- booting without live USB fails - get "insert proper media and reboot" error.
- when I try to do mount commands in terminal running live USB, I get "[FONT=Verdana]/dev/sda1 already mounted or /mnt/BootInfo/sda1 busy"
[/FONT]- when I try to install grub in terminal I get "cannot find canonical path to /cow"
- when running live USB I can see EFI->Ubuntu folder and also grub files on my drives, which are of course all unmounted.
- in Gparted I applied a "boot" flag to my Ubuntu sda2 partition (see photo). 
- in Gparted I guess the sda1 FAT32 partition is blank space I chose not to overwrite during my clean install (not sure why I chose that)?

Thanks all.

---

### Post by sandyd on 2015-11-23
Seems like boot repair doesn't like LUKS.
Did you install Ubuntu in UEFI or BIOS mode - Ubuntu will only boot in the way it is installed. Ubuntu created a FAT32 partition for the EFI, so I assume you installed in UEFI mode.

Post the output after running the following
```

sudo crypsetup luksOpen /dev/sda3 #will ask for password
sudo lvmdiskscan #scan disks for LVM PVs
sudo vgchange -ay #activate the LVM VGs
sudo lvscan #make sure LVs are detected
sudo lvdisplay #Display LVs

```

---

### Post by tom214 on 2015-11-23
Thanks for reply. Unfortunately I don't recall having to select either UEFI or BIOS mode during the install. 

Photos are the only way I can post the output of the commands- see attached.


[ATTACH=CONFIG]265743[/ATTACH][ATTACH=CONFIG]265744[/ATTACH]



Btw, I noticed when I boot up with the liveUSB (the only way I can boot), I see different results from one boot to another when checking GParted. On some boots one of the drives gets mounted and a mount point is shown in GParted, on other boots no drives are mounted. Also, in the cases where a drive is mounted, the mount points in GParted are not always the same. One was something like media/ubuntu/[UUID].  I believe I saw a mount point /mnt on one occasion. Also, when I explore the file directories I can see a grub folder, but it appears to change location from one boot to the next. Not sure if this is because I've run some mount commands in prior sessions, in an attempt to use the grub-install command. So, my drives seem to be all over the place :)

---

### Post by oldfred on 2015-11-23
How you boot install media UEFI or BIOS/CSM/Legacy is then how it installs.
Since you have the FAT32 partition, you installed in UEFI mode.
But with gpt partitioning, the boot flag must only be on the ESP - efi system partition.
Do not confuse an ESP which has to have boot flag, with your /boot partition. They are different.

So move boot flag back to the FAT32 partition.
And see if you can boot in UEFI mode.

What brand/model system?

---

### Post by tom214 on 2015-11-24
Thanks for reply oldfred.

See newest screenshot of GParted, The boot flag is on the FAT32 partition. I set the BIOS firmware to UEFI and HDD first in boot order, but I got the “Insert proper media and press any key to reboot” error.

[ATTACH=CONFIG]265746[/ATTACH]

Maybe my other screenshots (see below) will give some clues to what the issue is?
 
 Details of screenshots:
- (shot01) contents of unencrypted 256 MB volume.
- (shot02) contents of grub folder on the unencrypted 256 MB volume.
- (shot03) contents of boot folder on device “Computer”.
- (shot04) contents of boot->grub folder on device “Computer

[ATTACH=CONFIG]265747[/ATTACH][ATTACH=CONFIG]265748[/ATTACH][ATTACH=CONFIG]265749[/ATTACH][ATTACH=CONFIG]265750[/ATTACH]

Not shown here - the boot folder was empty on the 496 MG encrypted volume (I viewed it after I unlocked the volume with the passphrase).

---

### Post by mastablasta on 2015-11-24
> **tom214 said:**
> 
Photos are the only way I can post the output of the commands- see attached.


you can mark the output of commands with the mouse, right click and select copy. then you can paste the text in forums using the code tags (the # icon). 

unfortunately I can't help much with your setup. default install should work well out of the box. but as I understand you were doing some changes in UEFI.

---

### Post by oldfred on 2015-11-24
What brand, model.
Acer requires you to set a password and trust on Ubuntu/grub's efi boot files.
HP, Sony and now many others have modified UEFI to include description. That is not allowed per UEFI, but perhaps some large Operating System vendor suggests that, since the only valid description is "Windows".
But there are many work arounds. Details in link in my signature. And this thread also.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

I have saved many links to threads where users did one of the work arounds and said brand/model of system.
If only Ubuntu, the preferred choice is often, just a new entry that says "Windows" but really uses shim not Windows efi boot file.
       
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by tom214 on 2015-11-24
My bad for forgetting the brand - it's a Toshiba Satellite Laptop - AMD A4 Series. As for my install method, I just did it straight out of the box and didn't see anything about UEFI along the way. I've assumed UEFI got messed up somehow when I removed Windows 8.

Install history details:
- the Toshiba came with Windows 8.
- first I installed Ubuntu 14.04 with a LiveUSB without Full Disk Encryption alongside Win 8 - no problems there. I could boot into either OS.
- then I decided to remove Win 8 and in the process used LiveUSB to reinstalled Ubuntu with Full Disk Encryption. - that's when boot problems started. Somehow I wound up having to use a strange boot method where in order to get the installed Ubuntu to boot, I had to have the LiveUSB connected when I booted up. Once the installed Ubunto booted, I could remove the liveUSB with no effect. If that wasn't odd enough, this method failed on every other boot attempt (I would just get a black screen). But I didn't mind. I'm pretty sure I had the boot method set to CSM at that time. So, apparently something about having the LiveUSB connected allowed the PC on boot to find the correct Grub (i.e. the grub on the installed OS), while bypassing Grub on the LiveUSB (?).
- I recall in that previous install I chose to "overwrite free disk space". _There was no FAT32 partition created_. Sda1 was type "ext", and sda2 was cyrpt-luks. I also recall in GParted sda2 was nested under sda1. Now in GParted I see no such nesting, and as discussed there's now a FAT32 partition.

I hope the above details may help instead of muddying the waters :)  If I don't figure this out soon, I'm wondering if I should try again from scratch - use Gparted to delete all partitions until it's 100% unallocated, then do a Full Disk Encryption install, overwriting all free space. Then try to sort out Grub from there?

---

### Post by oldfred on 2015-11-24
If you get the FAT32 partition with boot flag that is the ESP - efi system partition for UEFI boot.
If you do not have that, but have a tiny 1 or 2MB unformatted partition with the bios_grub flag then you have BIOS boot on a gpt partitioned drive.
Or you can have BIOS boot on a MBR partitioned drive.

If in UEFI boot mode, you have to have UEFI on in UEFI/BIOS. Depending on if you installed with Secure Boot on, you may or may not need Secure boot off.
If in BIOS mode you have to have UEFI off, and CSM/BIOS/Legacy mode on.

UEFI & CSM/BIOS are not compatible. 

Many systems and we have seen newer Toshibas with the issue that they modify UEFI to use description as part of boot.  That is not allowed per UEFI specification. But there are many work arounds.

If only Ubuntu installed, you can add an entry that says Windows, but really boots with shim.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
            
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

     
More details & other work arounds also in link in my signature.

---

### Post by tom214 on 2015-11-24
[SIZE=3]Thanks oldfred and others for the detailed replies.  I will proceed shortly and report back.

One thing I forgot to ask - is Full Disk Encryption possible with the "Something Else" install?

Edit - I see from another source the answer is yes, but it appears to be a relatively complicated install process. I'm now considering the "Something Else" install option, since that option requires you to manually create a boot partition. So, perhaps with the Something Else option there would be less chance of having the same boot problems as with the other install options? [/SIZE]

---

### Post by tom214 on 2015-11-29
I thought I might catch a break trying a fresh install, but no such luck. 

- I made sure to boot up the LiveCD in UEFI mode.
- in LiveCD I used GParted to delete all partitions.
- I ran the new install, again opting for Full Disk Encryption. 
- install completed successfully and I rebooted as per install dialog.
- now getting the familiar "install proper media and reboot" error.

New Boot Repair results: paste.ubuntu/com/13561848

I haven't yet reviewed my Boot Repair results in detail, but I can see they are certainly different than before. I've attached a screenshot of the Boot Repair message " /boot detected. Please check the options.", but I'm not sure what is meant by "please check the options".

I've attached a screenshot of GParted and some messages related to Grub shown on what I guess was the install log(?) while the install was running.

[ATTACH=CONFIG]265830[/ATTACH][ATTACH=CONFIG]265831[/ATTACH][ATTACH=CONFIG]265832[/ATTACH][ATTACH=CONFIG]265833[/ATTACH][ATTACH=CONFIG]265834[/ATTACH]

Btw, before I ran this install I tried to fix the previous install by running the "Windows Boot Manager" command line as suggested in an earlier post, but got the error "command doesn't exist".

---

### Post by oldfred on 2015-11-29
Generally with Desktop installs, you do not need a separate /boot partition. That is where grub & kernels are. 
But with a full drive encryption install and LVM or logical volume partitions you have to have the separate /boot partition as grub & kernel cannot be encrypted. LVM is an advanced partitioning system.
Boot-Repair sees the /boot partition but you have to tick the option so it reinstall grub to correct place. And you have to un-encrypted your install for it to work.

Is this yours? easier if clickable link.
[http://paste.ubuntu.com/13561848/](http://paste.ubuntu.com/13561848/)

Newer Toshibas now seem to need one of the work arounds. Since you only have Ubuntu this is often the easiest. Most are dual booting and have to copy grub or shim into /EFI/Boot and rename to bootx64.efi. You can do that also as another way to boot.

       
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

