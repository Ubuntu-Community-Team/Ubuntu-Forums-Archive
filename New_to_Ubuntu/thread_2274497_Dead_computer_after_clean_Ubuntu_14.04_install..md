---
title: "Dead computer after clean Ubuntu 14.04 install."
date: 2015-04-20
forum: New to Ubuntu
---

### Post by Steve_Croxton on 2015-04-20
I just rebuilt my HTPC with an ASRock AM1H-ITX mobo, an AMD 5350 APU, a stick of Crucial Ballistix 1600 8GB DDR3 RAM and a Crucial BX100 250 GB SSD. I decided to try Ubuntu 14.04 as my stand alone OS. Went through the entire install without a hitch until right before the end, when an error message came up saying that GRUB couldn't be installed in the assigned / partition. I quickly chose another location randomly, and by the time I did this, it said the install was done and to restart. After the reboot, the Ubuntu screen came up telling me to push enter to eject the Ubuntu DVD, which I did. Then the screen went black. Tried rebooting with the LiveCD, nothing. Tried resetting and restarting the computer, but all I can get into is the ASRock bios utility if I react quickly before it turns to black. Essentially, save for the bios utility, I have a dead computer.

Help...

---

### Post by dino99 on 2015-04-20
your grub installation might be compromised; reinstall it from the livecd: open a terminal and run 'sudo grub-install /dev/sda' (without the quotes)
then your new toy should be alive again ):P

question: is that mobo using uefi/bios/gpt ? how have you set them ?

---

### Post by Steve_Croxton on 2015-04-20
As I said, I can't get the LiveCD to run. Apart the UEFI, it is dead. I hsve zero access to Ubuntu. As for the UEFI, I haven't done anything with it yet. It's set to stock.

---

### Post by tripp98 on 2015-04-20
unplug hard drive.  boot from cd see if the computer is working without the hard drive.  if it does then your mb may be booting too fast to select options.  
do some hardware diagnostics then you can get back to the os install.

---

### Post by Vladlenin5000 on 2015-04-21
Do not unplug your SSD nor anything of the sort. You don't need any of that. This is waht you need to understand:

1. Your system is UEFI. Unlike old BIOS it stores booting information and configs. It's _usual_ for a UEFI system to behave differently with or without installed OS regarding other boot options.
2. Most likely you need to press ESC immediately after (or during) POST. Then - and only then - you'll have access to a menu where one of the options should be boot devices, boot order or something. 
3. The way you boot the installation media is how it installs: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) (for a proper UEFI installation you must choose the entry preceded by "UEFI:" of the two listed for your instalation media, DVD or USB).

Now, what you can do: 
1. Boot (in UEFI) a live session ("Try Ubuntu")(instructions above);
2. Search for and open GParted;
3. Make sure you have selected your SSD - You should see at least two partitions; if one is marked as swap then right-click and swapoff; make sure no partition from the SSD is mounted in the live session;
4. Select and remove one by one all the partitions until you have a drive with unallocated space only.

At this point you should run the installer, also from the live session; follow instructions as to use the whole drive.
Ubuntu will install correctly in UEFI mode by automatically creating all the needed partitions including one EFI partition which is from where everything loads. The default layout for the automatic installation is fine but you can do it manually provided that all of the required partitions are there to start with then use "Something Else" and tell the installer which partitions to use.
If you have further issues please comment.

---

