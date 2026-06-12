---
title: "Dual boot, cant access windows."
date: 2021-07-25
forum: New to Ubuntu
---

### Post by oldnew1786 on 2021-07-25
So I got a new case for my pc. I unplugged everything but when I plugged everything back in (the same way) I can't get into windows. I get this message saying something like "no disk present press any button to return" or something like that. I can get into ubuntu which is on the same drive. Is there a way to recover windows?

I'm booting into both from grub.

---

### Post by tea for one on 2021-07-25
Probably a good time to run [Boot-Repair 2nd Option](https://help.ubuntu.com/community/Boot-Repair)

Please do not run the repair but paste the link to the report in this thread.

---

### Post by oldnew1786 on 2021-07-25
Thanks. I will try this when I get to my PC.

I know there is a way to reset your password for Ubuntu from your computer. How do you do that again? I haven't been using Ubuntu because i forgot my Ubuntu password.

---

### Post by tea for one on 2021-07-25
> **oldnew1786 said:**
> I know there is a way to reset your password for Ubuntu from your computer. How do you do that again? I haven't been using Ubuntu because i forgot my Ubuntu password.

I've never had to do this but I'm sure an internet search will help you.

Try this one [https://itsfoss.com/how-to-hack-ubuntu-password/](https://itsfoss.com/how-to-hack-ubuntu-password/)

---

### Post by oldnew1786 on 2021-07-25
Okay, I am now at my pc.

I reset my password.

I'm having difficulty with Boot-repair. When I enter this in a command line (from the link) ubuntu tells me it doesn't recognize the command. I have a USB boot device in case I need one.

IDK what to do next.

---

### Post by oldnew1786 on 2021-07-25
I have another problem.

My ethernet isnt working. The lights are on but I can't connect to the internet. Getting a message saying cable unplugged but its plugged in and the ethernet lights are on.

Also, my boot USB drive is not asking me to try ubuntu but is just logging me into my main account for some reason. I have the USB as the first boot priority and my bios says it's bootable but with no internet, I cant download a new ISO.

---

### Post by oldnew1786 on 2021-07-25
I recall at one point I tried to use samba to share some disks. I tried to purge samba using this command:

sudo apt-get purge samba samba-common

I still have no internet. If I can get internet on this machine, I think I'll be fine to search for solutions. As it is, this is frustrating. I have a lot of data on windows.

I'll try the boot USB again and look through the link to see if I missed something.

[Edit] when I try this command:

sudo add-apt-repository ppa:[username or] yannubuntu/boot-repair

I get this message:

ERROR'~[username or]yannubuntu' user or team does not exist.

---

### Post by oldfred on 2021-07-25
Boot-repair is downloaded  using Internet.
So you have to first fix Internet issue.
Changing case would not have changed anything. What else did you change?

Can you directly boot Windows from UEFI boot menu?
Grub only boots working Windows. 
That also means Windows cannot be hibernated or fast start up must be off. Windows updates also turn fast start up back on.

---

### Post by oldnew1786 on 2021-07-26
It would be better to show you what happens when I try and boot windows.

[https://imgur.com/gallery/Wz2gTEC](https://imgur.com/gallery/Wz2gTEC)

And yes, I am in UEFI. I can't find fast boot in my bios but I don't have secure boot on.

---

### Post by grahammechanical on 2021-07-26
When you rebuilt the computer did you need to reset the date and time? If you did that it could indicate that the UEFI settings were somehow reset to factory defaults. It could explain why the motherboard is making a guess as to the type of disk.

If you haven't used Ubuntu for some time then it is also likely that Ubuntu no longer knows about the presence of Windows. When you used the machine before you replaced the case did you access Windows from the Grub boot menu?

When you originally installed Ubuntu did the installation succeed? Could you load both Ubuntu and Windows from the Grub boot menu? I am wondering if you are in a situation where Windows is installed in UEFI mode and Ubuntu is installed in BIOS/Legacy mode.

Regards

---

### Post by oldnew1786 on 2021-07-26
Hi.

No I did not need to reset the time, but I did try and flash the bios from the last bios I had for the mobo from January.

Yes, I always booted into windows from grub boot menu. I hadn't used ubuntu in quite a while (118 days). I don't know my keyring password.

Yes, as far as I know, I have always been able to boot into both until now and I can't access windows for some reason.

Also, I just found out people have trouble with ubuntu and b550 boards, which is what I am using (tomahawk from msi). It might need a bios setting changed. From recovery mode in ubuntu, it says I have no internet. That was not a problem before iirc.

---

### Post by oldnew1786 on 2021-07-26
I think the problem with the internet is that my ethernet uses realtek r8169 which is not compatible with ubuntu. There is a way to roll back to realtek r8168 but I cant figure it out. Its confusing- all these different things to try and dont know what applies to me and my situation.

Also, I need to disable wake on lan. The problem is that I need to get into windows to do that. And with no internet I can't get into windows. I've been at this for 10 hours. I need a break at some point.

[Edit] Also, I just bought a nice bluetooth dongle which I'm trying to use for internet, but can't catch a break.

Any help would be appreciated on any of this.

---

### Post by tea for one on 2021-07-26
Do you have an Android smartphone?

Power on phone and connect to PC using USB cable
Open phone settings > Network & Internet > Hotspot and Tethering > Activate USB Tethering

Check connection on Ubuntu PC via Network icon (top right on gnome panel)

---

### Post by yancek on 2021-07-26
The image in post 9 shows invalid EFI file path so you need to check what your file path is in /boot/grub/grub.cfg.  You should see the line below at the end of the windows menuentry in grub.cfg.

>  chainloader /EFI/Microsoft/Boot/bootmgfw.efi 


You should also verify that this file exists running this command with sudo:

> ls /boot/efi/EFI/Microsoft/Boot

THe bootmgfw.efi file should be there. If it is not, that may be the problem.  The file you are looking for is bootmgfw.efi so if it is in some other location, you need to change the path in grub.cfg to show it.

You indicate in one of your posts that you are using UEFI.  You should be able to boot windows from the Boot Options in your BIOS firmware.

---

### Post by oldfred on 2021-07-26
Have you updated UEFI? That would need Internet also.

Many with AMD 450, 550 & similar boards need IOMMU settings changed.
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0 uses this boot parameter: amd_iommu=on iommu=pt  & UEFI settings
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Asus Rog Strix B550 Disable IOMMU
[https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397](https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397)
 MSI B450M Pro-Vdh Max Unable to install Ubuntu (Black Screen)  UEFI update required
[https://askubuntu.com/questions/1340556/unable-to-install-ubuntu-black-screen-uefi?noredirect=1#comment2290153_1340556](https://askubuntu.com/questions/1340556/unable-to-install-ubuntu-black-screen-uefi?noredirect=1#comment2290153_1340556)

---

### Post by oldnew1786 on 2021-07-29
Hi.

I decided I'm just going to reinstall windows. I forgot that most of my data in windows is actually on an external HDD, so I'm good.

I just want a link to how to install windows from grub. Then I'll be good I think. I tried searching but all the options are how to install ubuntu from windows.

---

### Post by oldfred on 2021-07-29
You typically have to boot the Windows install ISO from UEFI boot menu.
You have to have a bootable version of the ISO. Most of the directions on the Internet are for older versions of Windows. They assume you can just extract ISO onto a FAT32 formatted flash drive using gpt partitioning. 

New Windows has a .win file that is larger than 4GB, and as such cannot fit on a FAT32 partition. But you have to use FAT32 to boot Windows in UEFI mode.
Windows tools to create installer from ISO, split the .win file into two parts so it fits on a FAT32 partition. 

For Windows ISO with .wim > 4GB
[https://ubuntuforums.org/showthread.php?t=2444665](https://ubuntuforums.org/showthread.php?t=2444665) & 
[https://github.com/ValdikSS/windows2usb](https://github.com/ValdikSS/windows2usb)
Latest Windows made .wim file smaller so extraction works again, depending on version. Check size of .wim file.

---

### Post by oldnew1786 on 2021-07-31
> **oldfred said:**
> You typically have to boot the Windows install ISO from UEFI boot menu.
You have to have a bootable version of the ISO. Most of the directions on the Internet are for older versions of Windows. They assume you can just extract ISO onto a FAT32 formatted flash drive using gpt partitioning. 

New Windows has a .win file that is larger than 4GB, and as such cannot fit on a FAT32 partition. But you have to use FAT32 to boot Windows in UEFI mode.
Windows tools to create installer from ISO, split the .win file into two parts so it fits on a FAT32 partition. 

For Windows ISO with .wim > 4GB
[https://ubuntuforums.org/showthread.php?t=2444665](https://ubuntuforums.org/showthread.php?t=2444665) & 
[https://github.com/ValdikSS/windows2usb](https://github.com/ValdikSS/windows2usb)
Latest Windows made .wim file smaller so extraction works again, depending on version. Check size of .wim file.

I now have access to the internet from a computer in my apartment complex. I've downloaded the ISO for windows and the update. These files are small, MediaCreationTool21H1 is 18.5 MB and the Windows10Upgrade9252 is 5.93 MB. I also downloaded Rufus and the AppImage on a flash drive. IDK what to do next though. I saw some stuff where I can install windows from inside Ubuntu, but IDK if I have GPart, but I think I do.

What should I do next? I looked at the article and it's greek to me. Creating a partition is something I can't do on this computer (because IDK the admin password), but I think I can do it on mine with Ubuntu?

---

### Post by oldnew1786 on 2021-08-01
This is what happens when I try and open the windows ISO image:

[http://imgur.com/gallery/r4mDO9O](http://imgur.com/gallery/r4mDO9O)

---

### Post by mustang700 on 2021-08-06
well if you cannot login to Windows-10  (this is not for Win-11)
 install with usb stick/DVD Windows-10,
and choose "Repair"
there you should have promt: X:
Type: **cd system32**
Type: [B]bootsect  /nt60 c:  /mbr     (do not forget spaces!)
[/B]then just reboot

---

