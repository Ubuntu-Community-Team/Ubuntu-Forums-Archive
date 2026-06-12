---
title: "My PC only boots to memtest86 instead of Ubuntu"
date: 2024-05-23
forum: New to Ubuntu
---

### Post by lovedlx on 2024-05-23
On my PC I had a SATA SSD with Windows 10 and a few weeks ago I installed another SSD and installed Ubuntu on that SSD
It worked normally until at one point I needed an SSD for a laptop so since I had an unoccupied HDD I decided to clone the Ubuntu SSD to this HDD, I did it through Aomei Partituon Assistant tool in Windows, the disk was cloned
I took out the SSD to Give it the use I wanted and now with Ubuntu I left the HDD as the main disk since before cloning the SSD it was Ubuntu that managed the dual boot of Ubuntu and Windows in Grub.  
Now I started the PC but the grub screen did not appear and it booted directly to Windows, I disconnected the SSD from Windows and left the HDD, and when turned on only a low bar appeared flashing.  
I came to the conclusion that grub had been damaged, so with a live cd I started to reinstall grub but I forgot something crucial and that was that the Windows SSD was disconnected so when installing grub and restarting the hdd the screen appeared grub but there was no option to select windows
Since I had access to Ubuntu again, I tried to add Windows 10 to the grub boot manually but to no avail.  
I tried to reinstall grub again on the live cd but with all the drives connected and that is where the current problem begins, when trying to start the pc after that, instead of showing the grub screen the pc just boots memtest86 and tried to reinstall grub a third time but without success and my pc kept booting memetes86
What can I do to solve this?  and get my pc to boot grub with the option to choose ubuntu or windows

---

### Post by yancek on 2024-05-23
Was your windows 10 install in EFI mode on a GPT drive?
When you installed Ubuntu to the SSD, did you create an EFI partition on that drive and install Grub from Ubuntu to that drive and that drive partition?
When you did the clone, did you clone the entire drive?
If both windows and ubuntu are EFI, do you have entries in the BIOS boot options menu for windows and ubuntu and do both/either boot? 
You should have a file on Ubuntu  /etc/default/grub.  At the very top of the file you will see an entry similar to the one below.

>  GRUB_DEFAULT=0

The 0 means it will boot the first menuentry in the /boot/grub/grub.cfg file.  Did you check that file to see what entries you have and what that line is set to in the /etc/default/grub file?
The entry below is the standard for a windows EFI install.  You will only need to change "90FE-41A5", substitute the actual UUID for the EFI partition on your computer which you can get by using the blid command.  You can either add this line to the /boot/grub/grub.cfg file, save the change and DO NOT update grub or you can put the entry in the /etc.grub.d/40_cutom file and DO update grub.

> menuentry 'Windows Boot Manager '  {
    insmod part_gpt
    insmod fat
    search --no-floppy --fs-uuid --set=root 90FE-41A5
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
} 

If you can't follow these steps, go to the boot repair site at the link below and use the 2nd option described on the page to run it by selecting the option to Create Bootinfo Summary.  Post the link you get when it finishes here as it will answer all the above questions and give members details on your setup.  Make sure you have both the Ubuntu and windows drives attached before running the script.

---

### Post by lovedlx on 2024-05-23
My SSD with Windows 10 is legacy with MBR, that is because I used that Windows 10 on an old motherboard that did not have UEFI so it was installed that way, and some time later I put that SSD on a more modern motherboard and I continued using that Windows 10 to avoid losing data. If I'm not mistaken, grub was installed only when I installed Ubuntu and I didn't make any partitions and when I booted grub it was already there, I didn't do anything, I even managed to customize it without problems and it also detected my Windows 10 installation

---

### Post by lovedlx on 2024-05-23
I made the changes you told me but my pc keeps booting directly to memtest86 instead of showing the grub screen

---

### Post by yancek on 2024-05-23
Which changes?  Did you edit the /etc/default/grub file suggested.  Did you put a windows menuentry in the /boot/grub/grub.cfg file and save the change and NOT update grub or did you make it in /etc/grub.d/40_custom file and update grub? 

If you had Ubuntu on a separate physical drive, it would boot a Legacy windows even if it (ubuntu) was UEFI.  I just noticed I forgot the boot repair link so go to the site at this link and follow the instructions and post the link you get when it finishes here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

