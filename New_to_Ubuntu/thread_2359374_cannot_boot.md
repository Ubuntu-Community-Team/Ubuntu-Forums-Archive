---
title: "cannot boot"
date: 2017-04-23
forum: New to Ubuntu
---

### Post by shreejan on 2017-04-23
[http://paste2.org/at355A1v](http://paste2.org/at355A1v)

help please.

---

### Post by Autodave on 2017-04-23
A little more info would be a great help.

Did you just install Ubuntu or is this a previous install that just now quit working?

Are you trying to run Ubuntu from a disc or USB device? If USB, is it an actual HD or a memory stick?

---

### Post by oldos2er on 2017-04-23
> **shreejan said:**
> [http://paste2.org/at355A1v](http://paste2.org/at355A1v)

help please.

Please see [https://ubuntuforums.org/showthread.php?t=1422475&p=8920811&viewfull=1#post8920811](https://ubuntuforums.org/showthread.php?t=1422475&p=8920811&viewfull=1#post8920811)

---

### Post by oldfred on 2017-04-23
If in BIOS you choose to boot the USB does grub/Ubuntu boot?
With nVidia you may need nomodeset until you install nVidia driver from Ubuntu repository.

Do not install grub to partitions like sdb1, but partition is not otherwise used, so we leave it.
BIOS can only boot from MBR of a drive, so you you install grub to drive like sdb. And you now show grub in MBR of sdb.
Do set BIOS to boot external drive first.

You do need to restore Windows boot loader to sda. So when you disconnect external drive, Windows still boots.
And Windows 10 will turn fast start up back on with updates and then grub will not boot it. You then have to in BIOS directly boot internal drive to turn off fast start up.
You can use your Windows repair disk or Boot-Repair's advanced mode if it can see the Windows install. If hibernated it may not see it.
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by shreejan on 2017-04-24
Thanks for the reply.
I just install Ubuntu. Trying dual boot with Win10.
After installation pc won't boot, taking me to prompt "grub rescue". Which display "error no such device : UUID".

---

### Post by shreejan on 2017-04-24
Thank you for the link, will follow them for new posts.

---

