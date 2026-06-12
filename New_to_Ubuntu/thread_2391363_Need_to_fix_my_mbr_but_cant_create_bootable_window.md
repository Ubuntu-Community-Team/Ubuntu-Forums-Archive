---
title: "Need to fix my mbr but cant create bootable windows 10 from ubuntu."
date: 2018-05-08
forum: New to Ubuntu
---

### Post by borhilian on 2018-05-08
So at some point Windows 10 disappeared off my grub list now I need to create a windows 10 boot-able usb to fix it. Unfortunately every of the 100 or so results on google pointed me to WoeUSB which seems to be defunked. I have the win 10 iso in my downloads folder and moved the files onto my usb but it does not appear to be bootable. (Thanks microsoft for claiming we ca just drag the files onto the usb and it will work :\)

Im using Ubuntu 18.04 to clarify!

A speedy solution would be much appreciated.

---

### Post by yancek on 2018-05-08
The method described at the link below worked for me to boot windows 10 from usb.  If you have a windows install DVD or a recovery disk you should be able to use the Repair option.  Of course, you would then need to reinstall Grub to boot Ubuntu and windows. 

l [URL="http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.htm"]http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html
[/URL]
Not knowing what you were doing which may have caused windows to disappear makes it difficult to suggest any recovery methods.  Do you see your windows partitions when running:

> sudo parted -l

---

### Post by borhilian on 2018-05-08
Nice 404 i just copy and pasted this here without checking it link. I've tried all to recommended and its still there only thing i haven't tried is fixing mbr. So i just need to write a windows 10 installer to a usb and even if that fails ill just delete the whole thing and start again with Windows 10. Also I dont have any physical windows 10 disks originally installed it from a USB. Also that command is also not found in Ubuntu 18.04 which im using, so uh yeah nice.

Can you atleast tell me how to write a iso to a disc thats bootable in ubuntu it liks my blank dvd-rs as read only and unselectable from the default image burner.

---

### Post by oldfred on 2018-05-08
I saved same link and it works. (missing last l from html maybe?)

[https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html](https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html)

I changed long time ago from DVDs to flash drives. Then I can reuse them.
I burned so many coasters. And as soon as i burned another program like gparted a new one came out.

---

### Post by borhilian on 2018-05-08
Thanks for the reply oldfred looks like what I'm looking for, gave a go at gpart once already but something mucked up, will give this guide a go.

Step 2 cant mount the usb so it wont work, losing alot of time to this, need a quick fix.

error mounting system managed device message.

Switched to ntfs instead of fat32, guide said either was fine but i guess not really...

Okay now i get a grub command line when i boot to the usb instead of it launching windows installation, why is this so difficult!

Gunna borrow a laptop and use it to make windows 10 installer usb and hope that it launches if not then i guess ill throw my ssd in the trash.

Ofcourse this meens ill be up all night since im all stressed out and waiting to get this fixed, because ubuntu is a problem to be fixed at this point.

I also burned a windows 10 iso to disc and that didnt work either jsut had blinknig cursor

How can i bypass grub cause apparently it gets run when i run a windows 10 installer usb i dont want this!!!

---

### Post by Impavidus on 2018-05-09
Bios or uefi? Most Windows 10 systems are uefi, in which case it's probably not very hard to solve this.

If uefi, use the uefi menu to use the Windows boot loader and boot your installed Windows 10 directly (not the repair usb). My guess at what happened is that some update on Windows enabled the fast startup (or was it fast boot?) or always on hibernation setting. This means Ubuntu can no longer access the Windows partition. Windows made itself invisible. After an update on Ubuntu, the grub menu was regenerated, but as os-prober couldn't detect Windows, it disappeared from the menu.

You can try this: Boot Windows using the uefi menu, bypassing grub. Make sure the fast startup option is disabled. Reboot and use the uefi menu to boot using grub, starting Ubuntu. Update grub (sudo update-grub), and with some luck it detects Windows and adds it back to the menu.

---

### Post by yancek on 2018-05-09
> Also that command is also not found in Ubuntu 18.04 which im using

If you are referring to the parted command I posted earlier, that is a lower case Letter L in the command and it most certainly is available on a default install of Ubuntu 18.04.  If you run that command, you should see an EFI partition and it should have a folder in it named Microsoft and if it should contain at least the bootmgfw.efi file with a couple of folders, worth checking as is you can repair the windows boot there is no need to reinstall it.

I left the last 'l' off the link I posted earlier so I changed it.

If you follow the instructions at the site I linked earlier, you can skip the part about installing Grub to the usb and simply boot it from the installed Grub on your Ubuntu.  Of course, if you can't mount the usb, you won't be able to do anything.  The instructions suggest using Disk Image Mounter to mount the windows iso which failed for me saying the image was too large so I had to loop mount the windows iso in order to access those files and copy to the usb.

Once the copying is finished you just put an entry for the windows usb in your Ubuntu grub.cfg file.  After doing this, do NOT run update-grub but save the change.  If you follow the other instructions, this should work.  You will need to run sudo blkid to get the UUID for your partition for windows on the usb and insert it in place of the one shown in my example menuentry shown below.

> menuentry "Start Windows Installation" {
 insmod ntfs
 search --no-floppy --fs-uuid 459532DE5D8D5C3A --set root 
 chainloader +1 
 boot
}

If this works, when you finish you can just boot Ubuntu again and delete that entry from grub.cfg or run sudo update-grub.

---

