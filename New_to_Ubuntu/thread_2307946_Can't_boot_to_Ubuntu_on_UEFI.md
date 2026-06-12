---
title: "Can't boot to Ubuntu on UEFI"
date: 2015-12-29
forum: New to Ubuntu
---

### Post by Vu_Hai_Long_Le on 2015-12-29
Hi, I'm trying to install ubuntu 15.10 on preinstalled win7 (UEFI). But my laptop keeps booting directly to windows instead of showing the Grub menu. Tried every guides i could find. Here is my log after running boot repair. What should I do? 
[http://paste.ubuntu.com/14271052/](http://paste.ubuntu.com/14271052/)

---

### Post by oldfred on 2015-12-29
What model Lenovo?

Boot-Order looks like it was updated to be Ubuntu first, but you have a lot of others before Windows. Best to have ubuntu, then windows in boot order.
       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
sudo efibootmgr -v
sudo efibootmgr -o 0015,0014

Many systems now seem to hard code entry to only boot Windows. That is not per UEFI, but some operating system vendor may be suggesting it to all vendors.

Hard drives can directly boot a drive or fallback entry as /EFI/Boot/bootmgr.efi. You have that entry and it just may be a copy of Windows. We want to backup efi partition and make bootmgr.efi really be shimx64.efi.

More details on copying shimx64.efi to be bootx64.efi in link in my signature below. 

And other Lenovo users who have done similar things:

 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side
Lenovo S20-30 BIOS install only
[http://ubuntuforums.org/showthread.php?t=2277003](http://ubuntuforums.org/showthread.php?t=2277003)
T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.

---

### Post by Vu_Hai_Long_Le on 2015-12-30
Hi oldfred, thanks for your reply. I have an E540 Think Pad. Actually I'm trying to run the efibootmgr command. But somehow I can't mount the efi folder. Did I do wrong or should I make a new folder for as efi ?
the screenshot is too big, so here is the link: [http://imgur.com/t1V6M8T](http://imgur.com/t1V6M8T)
Here is how the Efi folder looks like after i mount it on Windows: [http://imgur.com/0CbANX1](http://imgur.com/0CbANX1) , [http://imgur.com/Vif0nj6](http://imgur.com/Vif0nj6)
I have solved it out after mounting the EFI folder on windows and set the bcedit command to the right folder. 
Thnx for your help. 
Regards

---

