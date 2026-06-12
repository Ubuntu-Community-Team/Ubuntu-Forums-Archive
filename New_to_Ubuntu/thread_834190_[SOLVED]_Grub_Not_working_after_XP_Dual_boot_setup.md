---
title: "[SOLVED] Grub Not working after XP Dual boot setup"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by sifon187 on 2008-06-19
Not really a newb to Linux, but I figured this would be a good place to post. I recently setup my Acer 5100 laptop for a XP Ubuntu dual boot. I already had Ubuntu 8.04 installed with my 120 GB Sata drive with a 60GB Partition for storage. I formatted the 60GB Partition in ext3, then decided to use it as the XP Partition and formatted it to NTFS. I installed XP Pro Corp on the Parition, and XP made the parition the Active drive. XP now starts automatically at start up. I used a Knoppix Live CD and changed the Linux Partition as the active drive. When I reboot the computer, Grub does not load, I only get a blinking cursor. Any ideas?

---

### Post by ettercap on 2008-06-19
hey
the installation procedure should always be
1.windows
2.linux

if u want xp back
insert xp cd
go into command line mode and type

fix mbr

this will get ur boot loader back

other wise reinstall grub boot loader ..this time make sure that it detects ur windows os.
\\note installing grub should replace windows bootloader

if grub doesn't work use lilo boot loader in the setup menu

---

### Post by kansasnoob on 2008-06-19
I have a multi-boot that gets hosed frequently due to almost constant changes and fiddling so I created a dedicated GRUB partition.

I used these two tutorials:

[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

---

### Post by kansasnoob on 2008-06-19
> hey
the installation procedure should always be
1.windows
2.linux

That's always the easiest way in so far as dealing with GRUB but not the only way. I used this APC guide for my first dual boot and it worked fine:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by sifon187 on 2008-06-19
> **kansasnoob said:**
> That's always the easiest way in so far as dealing with GRUB but not the only way. I used this APC guide for my first dual boot and it worked fine:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)


I tried the APC way of reinstalling the Grub Boot Loader, but when I get to the Setup command, I get "cannot mount the partition"? Any ideas?

---

### Post by Dedoimedo on 2008-06-19
Hello,

First, restore the MBR so Windows can cope:

Boot from Windows CD, go to Recovery console

fixmbr /r

Then, boot from Linux live CD and then:

Enter terminal
type grub

find /boot/grub/stage1

>> This will give the partition where grub configuration files can be found, most likely the same partition where Linux is installed. It will be something (hdX,Y)

Then:

root (hdX,Y)
setup (hd0)
quit


More info here:

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

[http://www.dedoimedo.com/computers/grub.html#common_problems](http://www.dedoimedo.com/computers/grub.html#common_problems)

Cheers,
Dedoimedo

---

### Post by sifon187 on 2008-06-19
I will give it a try when I get home from work.

---

### Post by sifon187 on 2008-06-19
Dedoimedo, thanks for the info, helped alot. The problem was, I was using the wrong parition to load the grub on. Everything works now, can boot to Ubuntu and Xp now.

---

### Post by Dedoimedo on 2008-06-20
Excellent!

Cheers,
Dedoimedo

---

