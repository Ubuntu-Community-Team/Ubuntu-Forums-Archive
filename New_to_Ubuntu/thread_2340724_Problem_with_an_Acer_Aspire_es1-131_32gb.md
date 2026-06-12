---
title: "Problem with an Acer Aspire es1-131 32gb"
date: 2016-10-21
forum: New to Ubuntu
---

### Post by lunarskiit on 2016-10-21
Hello! 
First of all I should mention that my technical expertise is lacking to say the least. But anyhow... I've been trying to install both Ubuntu and lubuntu without success. The installation proccess seem to go trough without any problems. However when I restart it to finalize the installation. I get a boot error which ends with the message "pxe-e61 media test failure check cable".

A friend of mine has said that this kind of computer isn't compatible with ANY version of ubuntu becuse it doesn't have a "real" harddrive, it has something called EMMC. 

Any sugesstions? Is it true that this type of computer can't run ubuntu?
Thanks for your time.

---

### Post by oldfred on 2016-10-21
Some other Acer

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot) 
      
 Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10) 
           
 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)

---

### Post by lunarskiit on 2016-10-21
Feeling very foolish, I had tried to install ubuntu using legacy bios... I'm trying again having disabled the security option.

---

### Post by lunarskiit on 2016-10-21
Ok so there seem to be some progress, but sofar no success... 

I have followed the steps in the above guides to turn UEFI on, make a security code and then disabling the secure boot. First time I tried installing I ran into a problem where "Grub installation failed". Impatient as I am, I simply tried to reinstall ubuntu and suprisingly this time it went all the way to restart...

Now when I restart it I get a message saying "Checking media" then after a few seconds it says "failed".

In the boot manager I have 3 options
1. Network Boot-IPV4: 54-AB-3A-00-3C-F6
2. Network Boot-IPV6: 54-AB-3A-00-3c-F6
3. Yes.

I'm atm downlading boot-repair-disk. Might this help?
Sorry for being all over the place...

---

### Post by lunarskiit on 2016-10-21
So I ran boot-repair and "Boot successfully repaired." However I still get the "Checking media... failed" message.
Also got this following url [http://paste2.org/3GwWexhJ](http://paste2.org/3GwWexhJ)

Any clue of what I'm doing wrong??

---

### Post by oldfred on 2016-10-21
One of the real issues with grub and UEFI, is that it only installs to the drive seen as sda.
Not sure if your UEFI boots from your flash card, but expect it can.
But with Acer you also have to set password & enable trust on ubuntu/grub .efi boot files from UEFI. But in your case that may now be the files on the flash drive?

If grub did install, then it overwrote the installer's version of grub as flash drive was seen as sda or did it add a new folder /EFI/ubuntu next to installers' normal /EFI/Boot folder?
I have similar type issues whenever I do a full install to any drive other than sda, as I have my main working install on sda, but any other install overwrites my /EFI/ubuntu folder in the ESP - efi system partition. If internal drive, I just reset, but to get an external drive to work, I have to manually copy all the files in ESP in sda to  ESP on flash drive.
You may need something like the reverse. Or copy /ESP/ubuntu from sda to ESP on your mmcblk0boot device. Not sure if then you boot from /EFI/ubuntu.
External devices like flash drives only boot from /EFI/Boot/bootx64.efi. For may flash drives I have to copy twice, once to /EFI/ubuntu and once to /EFI/Boot and then rename shimx64.efi to bootx64.efi. That version of grub/shim is hard coded to find the rest of grub in /EFI/ubuntu so both copies are required. The installer has a different version of shim & grub as bootx64.efi which only has the minimum features to boot installer.

But I cannot tell you whether grub install created a new folder /EFI/ubuntu on flash drive or not. You should manually check. If there then we can copy.

This user posted more details on how he did it. But his was a standard flash drive copy.
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836)

---

