---
title: "grub rescue"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2013-03-04
Hi friends.

I have a dell inspiron with windows 8 preinstalled. I tried to install Ubuntu 12.10 and then used boot-repair with hope that it would configure boot process in such way that both windows and Ubuntu 12.10 will be available. Now I have lost access to both OS and also boot menu and BIOS. The only option available to me is grub rescue prompt. Here is boot-repair report.

**[http://paste.ubuntu.com/5574288/](http://paste.ubuntu.com/5574288/)**


Please help me with necessary commands to config grub properly so that at least one OS is accessible.

---

### Post by oldfred on 2013-03-04
From Boot-Repair, you need to change from BIOS/Legacy/CSM mode to UEFI.
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
This should just be ubuntu in UEFI menu.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!

You also have labeled two partitions the same, that may cause issues later.

    /dev/sda7: LABEL="New Volume" UUID="B224E78C24E75241" TYPE="ntfs"
/dev/sda8: LABEL="New Volume" UUID="A46AEF0D6AEEDB56" TYPE="ntfs"


 I learned a while back to stop using spaces. Use CamelCase or under_score or just onelongname. Windows will work without the spaces and it makes things a lot simpler in Linux.

---

### Post by sujitrjadhav on 2013-03-04
But how do I do that? I can not boot in to DVD/USB flash drive or no other device. BIOS is inaccessible( i.e. F2 and F12 is not working). When I start laptop I get grub rescue menu with error 
error file 'boot/grub/i386-pc/normal.mod' not found.

Now with what grub rescue commands I may solve this?

---

### Post by oldfred on 2013-03-04
Did you turn off fast boot before installing. Some systems only let you back into UEFI menu from Windows and lock out keys unless you turn off fast boot.

Most Dell systems have worked.
  HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache) - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

Did you create a Windows 8 repair flash?

 Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx](http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx)

HP has these instructions, does Dell have something similar on their web site?

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

Microsoft info on boot keys:

 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by Lisiano on 2013-03-04
A trick I have learned when I can't be bothered to disable Fast Boot is to simply kill the PC while it is attempting to boot. After 1 or 2 tries the system might try to do a "slow boot".

---

### Post by sujitrjadhav on 2013-03-07
Thanks to all those who replied and tried to help me. Special thanks to oldfred for offering info in such details. Here is what worked for me


with 


ls (hd0,gpt6)/boot/ 


I found a folder grub.bkp folder in /boot folder; then I used following  commands at grub rescue prompts
 
set prefix=(hd0,gpt6)/boot/grub.bkp
set root =(hd0,gpt6)
insmod linux
linux /vmlinuz root=/dev/sda6 ro
initrd /initrd.img
boot


With these commands I managed to boot in linux installation. Then I again used boot repair and in the advanced option selected windows as default boot OS. With that my Windows installation started working but Ubuntu became unavailable.  With windows 8 Shift+restart I booted in a bootable pendrive created with "multisytem" software. I selected Super Grub 2 option which searched for all available OS. Again booted in ubuntu and used boot-repair again and this time selected ubuntu 12.10 as default OS. Now When I turn on laptop grub offer me choice to select Ubuntu or Windows 8- exactly what I was trying to do.


The only problem that still exists is that BIOS / Boot Menu /Change Boot Mode is still not available - even not with shift+restart options in windows. System is working perfectly in both ubuntu 12.10 and windows 8 except for the fact that Ethernet connection not working in ubuntu. I am trying to solve ethernet problem and if I fail I will create a new thread. 


I expect help to solve" BIOS (F2) / Boot Menu (F12) options not working problems", if possible to mark this thread solved

---

### Post by oldfred on 2013-03-07
Is that still the fastboot setting in Windows/UEFI? You should be able to get to it from Windows and grub has added a new entry that they say works but I have not seen any post that it does work. And your pastebin does not show it, but that may be because you installed in BIOS mode.

 Grub provided with Ubuntu installed as UEFI includes a "setup" option at the bottom of the GRUB menu. This launches your motherboard's UEFI setup, and can be used to get into UEFI setup on "fastboot" systems which skip the setup screen entirely when a valid OS is installed.

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

If you do a this, does it add the above entry at the bottom of the grub menu? And then does it get you into UEFI?
sudo update-grub

---

### Post by sujitrjadhav on 2013-03-09
I did not know anything about fast boot. I thought that it was an option available in BIOS setup screen of latest systems which I did not ever notice. As BIOS was not accessible I did not try to find any info on fastboot thinking that I could not change the setting as BIOS was not accessible to me. From your reply I found that setting could be change from Windows 8. So I did little google and found that fastboot was on my system. But before this Dell technician had already visited and replaced system motherboard and that had already solved the problem. 

Fast boot setting for my laptop is still on but now I have access to BIOS Setup as motherboard has been replaced now. And system is also working perfectly.

And most important part is that now I have Windows 8 and Ubuntu 12.10 dual boot working perfectly. When I turn on laptop Grub offers me choice to select Ubuntu or Windows. 

Thanks anyway as I learned a new thing -fastboot from your previous reply.

---

### Post by sujitrjadhav on 2013-03-09
How do I mark this thread solved? Previously I could do this through Thread tool. But now thread tool dose not show that option ( I am logged in ).

---

### Post by fiodev on 2013-03-09
download "Super Grub Disk" make a cd or usb and keep it on a shelf somewhere for when you need it.
boot your computer into super grub disk and you can boot into your kernel with it.
apt-get install grub or remove grub and re-install
that should work

or you can reinstall grub with a live cd of the some distro you are using

---

### Post by fiodev on 2013-03-09
or you can use the recovery option on the ubuntu minimal cd

---

### Post by oldfred on 2013-03-09
I do not know if Supergrub now works with UEFI installs or not. 

There is a temporary work around for SOLVED, see my signature.

---

