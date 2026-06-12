---
title: "Very new - can't install Ubuntu on my Dell Inspiron 15-3567"
date: 2017-11-06
forum: New to Ubuntu
---

### Post by follie on 2017-11-06
Hi all! (Mods, if this belongs in the Installation forum, please move. I couldn't decide which was more relevant). 

I have a Dell Inspiron laptop 15- 3567 that was working fine when I bought it. I bought the store display model, which didn't come with recovery media. But after a quick password reset, I had no problems with it and it was running great.

When Windows 10 did a recent update, my laptop only booted to the BSOD. I tried all the repairs I could find online with no luck. I followed Dell's instructions to reset to factory settings with no luck- the computer wouldn't leave the BSOD. I tried to do a complete clean sweep and remove the OS entirely. No dice. So, I can't do anything except boot to the HD and the horrible BSOD. Annoying. 


I've been wanting to change to Linux anyway, and was planning to create a partition on my machine to do that, but never got around to it. Well, it seems like now is the perfect time, right? 

So, I followed all the instructions on the Ubuntu site, downloading Rufus and then the Ubunto 17 install into a bootable USB. I change the BIOS settings to Legacy and told it to install from the USB first. 

It's not working. When it boots, it says there is no bootable device found. I know the system can access the USB- it allowed me to choose a specific file to boot to from the USB on one of my many attempts to figure it out- but it still wouldn't boot with the USB. 

I have played with everything I can think of, done everything I could find on google, here and on other forums. 

Adding to the frustration is my Dell is my only Windows machine. The other computers in the house are Macs, which means all of the downloads are done from the Mac. Now, since it goes to a USB drive, I don't think it matters too much, but I just wanted to mention it. But it also means I don't have a Windows machine to download any kind of fixes, because it scans my Mac and says it's not compatible.  While I like using my Mac, I bought the stupid Dell and I want to be able to use it! I can't return it, and I don't want to try to do the repair over the phone because my hearing isn't great, and I would only get more frustrated. 

I will need a ELI5 (explain like I'm 5 years old), though. I am completely new to these kind of problems. Years ago I installed Puppy Linux on my old Sony Vaio, but Windows was still working on that one and it booted from the USB with no problems. I am way over my head with this!

I am at a loss right now. Any help would be appreciated. It's a very expensive nightlight and paperweight right now. 

If there's any other pics I can take, just let me know. I attached the 2 main errors. 

Thanks!

---

### Post by Geoffrey_Arndt on 2017-11-06
Well, this is kind of a long shot - - but what do you have to lose?

You can use the Mac for all the below till you've created the bootable usb stick.

So - - firstly get the best usb boot creation tool I've used - - it's called "Etcher" . . get it at [https://etcher.io/](https://etcher.io/)  

Then, get a fresh download of the ubuntu 16.04 (not 17) from the Ubuntu site.   A torrent download will work fastest.   

Then, fire up Etcher and follow the basic instructions on the screen.    When the Etcher program finishes validating the usb write operation, then you're ready to test it on the Windows machine.

If all goes well, the you'll boot up into Ubuntu.   Many PC's also have a "one time boot menu" than can be invoked via F12 or sometimes another key like F10 or F7.   Check the owners manual for the exact method to display the boot menu.

Let the installer (assuming a successful bootup) find the free space you created on the HDD (right?) and tell it to use the whole disk.    Good luck.

---

### Post by Topsiho on 2017-11-07
I agree basically with the above advise. I also think you want to install Ubuntu on your expensive paperweight.
Except: I doubt that Ubuntu will run well on your very old computer!
I think a lighter version, such as Lubuntu. Xubuntu or Ubuntu Mate will run much better on it. There is also Budgie Linux, which I don't know and possibly even do not spell correctly, but which you might investigate and try.
Running any of these from a USB-stick or from a liveDVD is much slower than when it is installed on a hard disk or SSD, so it's very difficult to judge the speed of each.
Installing is not difficult, especially if you install it using all diskspace, so you need not be afraid doing so. And: you have nothing to loose!
You can see how to do that here: [https://askubuntu.com/questions/6328/how-do-i-install-ubuntu](https://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
I'm not sure that this meets ELI5, but as always instructions like these are really not so daunting as they seem (after install you'l think: "is that all?")
Only be prepared to answer some questions, such as:
your name
your user name
your computer name.
the password you'll use (it requires a good password, at least 8 characters, Upper- and lower case letters, numbers, other characters such as #@&!, but no spaces. Better think of one before installing.
You should also provide your location on earth (for the time zone), and what keyboard you have on your computer.

Reading through the instructions in the link you'l find what I forgot (type of install: using all disk, or next to Windows) and such.

And remember: you can repeat this process for an other distro afterwards, if you are disappointed with the reult.

Succes,
Topsiho

---

### Post by leunam12 on 2017-11-07
It looks like the hard drive failed. Boot the USB live session (try Ubuntu without installing) and open the Disks utility and check the SMART section for errors, seek error rate, read error rate, unrecoverable error in data, reallocated sectors and sectors pending reallocation. If the values on those fields are something other than 0 it (most likely) means that the disk has surface problems; it needs to be replaced. If you cannot boot from the USB drive chances are that the RAM is bad. Another possibility could be that the hard drive got disconnected from the socket, this usually happens if there is no caddy holding the drive and the computer receives some impact (even a minor one), but I have seen it happen even with a caddy. It would not be a bad idea to open the hard drive door and disconnect the drive and connect it again and make sure that it is firmly seated in its socket.

---

### Post by Autodave on 2017-11-07
+1 w/leunam12: sounds like the HD died.

---

### Post by oldfred on 2017-11-07
This looks like a very new computer?

Did you change UEFI setting for drives from RAID to AHCI?
Linux desktop installer does not see RAID correctly.

You Mac is UEFI, and if new Dell, it is UEFI, you should not use BIOS/MBR or Legacy.

 Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 


       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

