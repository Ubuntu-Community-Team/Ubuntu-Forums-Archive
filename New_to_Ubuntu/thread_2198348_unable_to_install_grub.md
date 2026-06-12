---
title: "unable to install grub"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by FergusMorris on 2014-01-08
I've used kubuntu for a few years. recently i got a new laptop (lenovo thinkpad 335). it came with windows 8 which i hate. i experienced many problems with the wifi with windows 8 - displaying networks but normally only giving me 'limited ' (ie no actual internet connection). having successfully got rid of windows 8 (i don't need dual boot, only linux) I've been trying to install lubuntu or xubuntu on my laptop as i hear it works better than  kubuntu on my model of laptop. i ran live usb installers for these, and they both failed due to the fact that grub failed to install, thus stalling the whole process. i have looked at some instructions on how to fix grub but matters are compounded by the fact that i cannot get any internet access while running xubuntu or lubuntu from a live usb stick. my questions are twofold: have you got any suggestions on how to get a proper wifi connection from live usb sticks; how can i tell if i have a hardware problem regarding my wifi (which might be the case given that wifi doesn't work on windows 8 nor live lubuntu / xubuntu  usb sticks)? secondly, how can i fix grub?
i know relatively little about computers, please assume total ignorance on my part and base your responses accordingly.

---

### Post by sudodus on 2014-01-08
Hi,
 
- Please reply to these questions to make it easier to give relevant advice!

- Can you 'Try' Lubuntu or Xubuntu, running it from the install CD/DVD/USB drive without installing?

- Do you know for sure that the problem is that grub fails?

- Is the computer running in BIOS or UEFI mode? If you do no intend to use a preinstalled Windows, I suggest that you try to run in BIOS (sometimes called CSM mode) instead of UEFI.

There might also be problems with the Radeon graphics. In that case you should try the boot option nomodeset. See this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Impavidus on 2014-01-08
Can you get a wired internet connection? If the only problem with the wifi is a driver problem, a wired connection may be very helpful in solving it. However, the fact it didn't work on Windows suggests differently. You state it does give you limited access. I've no exprience with that, but could it be a problem with the wireless access point or router? Is it your own wifi network, or library/university/office? To change router settings on your own network you may also need a wired connection.

---

### Post by oldfred on 2014-01-08
Always best to have the Wired Ethernet as Impavidus suggests.

And is using BIOS boot as sudodus suggests and drive is still gpt you may need the 1 or 2MB unformatted bios_grub partition for grub to install correctly. I suggest keeping gpt partitioning and even the efi partition in case in the future you want UEFI.

Some other issues like Intel SRT and others can also cause issues on grub install.

Post this:
sudo parted -l

---

### Post by FergusMorris on 2014-01-08
sudodus- i am able to  "try" lubuntu and xubuntu, it works fine except for wifi. the error message i got when the installation process failed was that grub was unable to install and that installations was thus unable to complete. i am not in bios, there was a graphical interface throughout the installation process  . how do i run the computer in bios? as i mentioned i am not that competent at all this, how would running in bios help?

impavidus- i have actually managed to find a ethernet cable and i can get a perfectly fine wired connection! the network is my home network which i share with other housemates who all seem to be able to access the wifi alright. i'm probably going to focus on getting an OS installed before sorting out my wifi issues, but how would i go about altering the router settings?

oldfred - sudo parted -l
Model: ATA HGST HTS725050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  512MB  511MB   fat32                 boot
 2      512MB   494GB  494GB   ext4
 3      494GB   500GB  5961MB  linux-swap(v1)


Model: Multiple Card Reader (scsi)
Disk /dev/sdb: 31.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.8kB  31.3GB  31.3GB  primary  fat32        boot, lba

Thanks everyone for your quick responses!! if getting ubuntu working proves too problematic i may just install windows 7 for the time being, hopefully i won't have to resort to that though!

---

### Post by Impavidus on 2014-01-08
If your housemates have no problem with the wifi, then your router settings are OK. First get your operating system installed.

---

### Post by oldfred on 2014-01-08
With gpt and a fat32 partition with boot flag you are installing in UEFI mode.

Best to see details and this will either install grub-efi or show error messages.
Be sure to boot in UEFI mode not BIOS/Legacy/CSM mode.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by FergusMorris on 2014-01-08
I seem to have managed to install xubuntu properly by using the OEM installer then proceeding from there to set things up properly.... that's weird but i'm not complaining! i still have wifi issues however.... this time it lets me connect to the network and it says it's connected but i can't actually load any pages or have any connectivity whatsoever. do y'all good people have any suggestions as to what i should do? i'm also a bit worried that i may have voided my laptop's warranty by removing windows 8 should there be a hardware problem with the wifi that requires returning to the manufacturer.....

---

### Post by sudodus on 2014-01-08
What wifi chip is it? You can try finding out using the program ***hardinfo*** or the terminal commands

```
sudo -s
lshw > lshw.txt
exit
```

and look at the file [FONT=courier new]**lshw.txt**[/FONT] with a text editor or viewer. We might be able to help, if you tell us about the wifi chip.

---

