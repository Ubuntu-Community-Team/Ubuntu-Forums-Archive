---
title: "boot problems on multiple hard drives"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by edgarbr on 2013-08-10
I have three hard drives all with different OS win7, winxp, and ubuntu13.04. After installing ver 13.04 the GRUB boot up was installed on all drives. [COLOR="#A52A2A"]I would like the windows drives to boot normally without GRUB[/COLOR]. I change to the drive with bios depending which OS I want to use. Thank you in advance for the help. edgarbr

---

### Post by Linux90s on 2013-08-10
make a note of the sata/ide location of each drive on the motherboard

unplug all drives.
connect your win7 drive ... boot into windows, download win7 repair disc (x86 or x64) depending on your os
boot from cd, perform startup repair and reboot. the win7 loader should be back.
download easy bcd edit (neosmart technologies) and install it if you want to add the other systems to the list later.

unplug all drives.
connect your xp drive ... boot with an xp cd, choose the recovery console, logon to the installed system, run:

fixboot
fixmbr

reboot ... xp loader should be restored, you can also use "easy bcd edit" in xp.

if fixboot/fixmbr does not work, you may need to find a file called zap.com which erases the starting sectors on the drive so that grub can be removed properly (sometimes it sticks around), you may need to create a bootable dos cd for this.

ps. grub should only have installed itself to one of the drives, i've never come across such a situation where it modified the mbr of all drives...

what you may be experiencing is that the selection of the hard drive in the bios is skipping your selected drive because the partition is not marked as "active" for booting and then finds the ubuntu drive which has the boot flag set.

hope that helps

---

### Post by edgarbr on 2013-08-10
Thanks for the reply on the install only win7 had the grub start-up. but i tried to fix the problem with a thing called boot repair hoping to rid the grub from the win 7 but it grubized the xp disc as well. that's when I yelled for help. BTW I really like Ubuntu I may use it alot if I can get my dell printer to work. 
EdgarBr

---

### Post by Linux90s on 2013-08-10
Safest bet when modifying the boot record is to unplug other drives efore starting as the system will detect and present the others on a reboot.

It's always eaasy to make a small mistake somewhere which targets the wrong drive and you only find out after you reboot!

Boot-repair puts grub back on :) ... great when you've used the windows repair to fix the windows install but it doesn't add linux back.

---

### Post by edgarbr on 2013-08-10
I tried to boot from the win7 repair disc with the other two drives unplugged and got the message Error: no such device d578e18c-a466-461e-900f-bc94fe0de3e4 grub rescue> _ I downloaded the bcd edit and after killing the virus in it went to another site and got easy bcd 2.1.2 (not so easy) did nothing with it. any ideas?

---

### Post by oldfred on 2013-08-11
You can install a Windows work alike boot loader to both of the Windows drives. The MBR is the same for Windows as it just searches partition table for boot flag (active partition) and jumps to that partition to continue to boot.
But Windows normally combines all boot files into one active partition on the drive set as boot drive in BIOS. So you may not have boot files on both drives. Then full repairs would be required.

If Windows are sda & sdb, but run this twice, once for each drive. Then in BIOS test to see if both or one works to boot Windows.

 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

If that does not work post link to bootinfo report from Boot-Repair. Do not rerun Boot-Repair with defaults as that restores grub.
But If in Boot-Repair you uncheck reinstall grub and check restore MBR, then under MBR options it should show the option to reinstall a Windows type boot loader.

---

