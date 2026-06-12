---
title: "USB not found in UEFI, while trying to install doual boot with windows"
date: 2021-05-17
forum: New to Ubuntu
---

### Post by littlezombie on 2021-05-17
Hello Community,
for the past few days I tryed to install ubuntu 16.04 on my second hard drive. I partitioned my second hard drive and made room fpr ubuntu, downloaded the iso file and used the Rufus tool to create a bootable USB stick, but when I enter the UEFI menu, I cant select the Stick. I tryed turning the save boot mode off, but it doesn't help. I even tryed to install with a DVD, but my Notebook does not have a DVD-drive so I used a USB DVD-drive. This created a lot of errors like this "blk_update_request i/o error" and eventually froze. 
Hopefully someone can help.

---

### Post by Autodave on 2021-05-17
Please give us some info on your hardware.

---

### Post by ajgreeny on 2021-05-17
There is no point installing 16.04 now as it has lost any further support.

I strongly recommend that you start again using an iso of **Ubuntu 20.04** or any other of the family, eg Xubuntu, Ubuntu-Mate, Kubuntu etc etc which still have either 2 or 4 years support remaining, depending on what you choose.

I can't help with Rufus as I have never used it, not having Windows any more, but there are many USB Boot disk creators available which you could try instead eg unetbootin.

---

### Post by oldfred on 2021-05-17
What are specs of your system?

Is second drive gpt partitioned which should be used for UEFI installs, but can be used for BIOS installs if only Ubuntu or data.

Rufus creates either a UEFI/gpt installer or a BIOS(CSM)/MBR installer. You want the UEFI version.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
And you have to select the UEFI option in the UEFI boot screen.
The UEFI setting in UEFI/BIOS is usually only the default mode for installed systems.
And UEFI Secure boot has to be off, if you want any proprietary drivers for video or WiFi.

You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Depending on size of external drive 100 to 500MB for ESP, 1 or 2MB for bios_grub and if not large just one ext4 partition for / (root). If larger drive then  30GB or more for / and rest for /home and/or data partition(s).

Ubuntu's Ubiquity only installs grub2's boot files into the ESP - efi system partition on first drive. Normally it adds a folder into the Windows drive's ESP. That works, but often better to have Ubuntu's boot files on its own drive. But Ubiquity does not make it easy or obvious. The boot drive choice in the Something Else install option only actually works for BIOS installs. 
You have to turn off esp,boot flags on Windows drive before installing & immediately turn it back on after installing. You can use gparted on live installer when in live mode.
Or:
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 
I just did test install of 21.10 and it still has the same issue as in now very old bug report.

---

### Post by littlezombie on 2021-05-18
I am using a ASUS fx553v notebook, with an Intel i5-7300HQ and a GTX 1050

---

### Post by littlezombie on 2021-05-18
The reason why I want to install ubuntu is, that i want to use the YOLOv5 image detector and I followed a tutorial in which the creator used ubuntu 16.04. On windows I get one error after the other and now I want to follow the steps as exactly as possible

---

### Post by littlezombie on 2021-05-18
when I insert the ubuntu 16.04 iso in Rufus I can only select MBR, but I now downloaded the 20.04 version and there I can choose between gpt and MBR. I will try this later

---

### Post by littlezombie on 2021-05-19
it worked, but I had to manually add my stick to the boot options. Therefor I had to select the stick and go to **\EFI\BOOT\BOOTX64.EFI. **This was not possible with the 16.04 version, i guess it was because of the MBR/gpt thing. Thank you guys, it's now running

---

