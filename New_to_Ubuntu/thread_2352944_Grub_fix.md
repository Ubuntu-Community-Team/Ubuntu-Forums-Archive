---
title: "Grub fix"
date: 2017-02-17
forum: New to Ubuntu
---

### Post by jendra on 2017-02-17
Hello i have any issue with my grub on pc 
i was trying too fix it with boot-repair but it failed 
here is pastebin [http://paste2.org/xsV2gMjP](http://paste2.org/xsV2gMjP)
any idea what i can do to fix it ?

---

### Post by yancek on 2017-02-17
the only sign of any possibly Linux on your drives is the 8GB flash drive which is your installation media.  You do have two partitions on drive sdc which is the 149GB drive where the installer may have tried to install Ubuntu.  Your output shows windows code in the MBR of the 465GB drive and Ubuntu Grub code in the MBR of the 1TB drive.  There is no sign of Grub on that drive.  The sdc drive shows the 'System' type as SFS which would be a windows Dynamic partition and you won't be able to install Linux on them.  None of your other drives have SFS Systems so you might try installing to the 1TB drive.  I don't use windows so I'm not sure if there is a way to change the Dynamic (SDS) partition type without losing data.

---

### Post by jendra on 2017-02-17
ok, so is there any other way to maybe just uinstall grub and stay only with windows? cause every single time as i power pc on i got grub rescue mode :/

---

### Post by Impavidus on 2017-02-17
As yancek says.

There's no Ubuntu installed on that computer. There is, somewhat strange, an unused 24GB extended partition (sda4). If you set boot order to sda first, as far as I can tell, Windows should boot fine.

For any more advice, we have to know what was supposed to be on that computer.

---

### Post by jendra on 2017-02-17
yeah and this 24 GB is ubuntu but gpart didint see there linux as you cen see in pastebin.
Also i tryied using this grub rescu mode with part's of comands but also it failed

---

### Post by jendra on 2017-02-17
and i forgot when i change boot order it's still pending me with grub rescue mode

---

### Post by oldfred on 2017-02-17
You show Windows boot loader in sda. 
So if you select sda to boot from does it not boot Windows?

You also show an extended partition sda4, with no logical partitions.
Did you do a major upgrade of Windows? It often "forgets" to include the Linux partitions when it rewrites the partition table.

       Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

