---
title: "[solved] GRUB corrupted after accidental boot to Acer recovery Utility"
date: 2016-10-03
forum: New to Ubuntu
---

### Post by huckerj2 on 2016-10-03
Hi,

I believe GRUB was deleted on my computer.  My computer displays the grub rescue prompt.  I had ubuntu and windows 10 installed together.  This was my first ubuntu run since updating to windows 10.  I booted into ubuntu just fine after hibernating my windows session.  After being unable to access my windows partition from ubuntu (due to hibernation?), I rebooted the computer and accidently booted into the Acer recovery utility.  I think it may have been selected as the default boot instead of normal windows boot because all I did was press enter.  Anyway, I exited that utility without making any changes but something was done to GRUB.  I tried the default repair on boot-repair from a live-USB.  The report is at [http://paste2.org/NcABCeKX](http://paste2.org/NcABCeKX)

Request your assistance in restoring GRUB and making windows/ubuntu bootable again.

Thanks!

---

### Post by westie457 on 2016-10-03
Welcome to UF.

The Acer recovery utility has a habit of ruining things, done it several times myself.

Boot Windows.

This part is more of a safety check. Go to Control Panel > Power Options. make sure there is no hibernation set.
Shut down Windows completely.

Start the computer using a Live DVD/USB to Try-mode.
Then go here for the procedure. [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by yancek on 2016-10-03
Simply booting into the Recovery partition is not likely to cause that problem.  Updating your windows 10 is as it will rewrite the partition table and leave the Linux partition off.  This can clearly be see in the output you posted.  Not sure if this can be fixed with boot repair, you might read up on that.  Otherwise, download and run testdisk software and use that.  Make sure you read the detailed instructions on the site first.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by huckerj2 on 2016-10-03
Thanks for the reply.  I am unable to boot into windows.  I tried booting windows with Super GRUB2 disk but it did not work.  I will give it another shot.  I have tried mounting the ubuntu partition per the repair instructions you posted with the command "sudo mount /dev/sdb4 /mnt" but I get the error: "mount: /dev/sdb4 is not a valid block device"

What should I try next?

---

### Post by oldfred on 2016-10-03
yancek has correct answer.

You have same issue as all Windows reinstalls or major upgrades do to Linux partitions in logical partitions. They forget to rewrite a Linux partition in partition table. Partition is still there as you show gap in extended partition start to start of swap partition.

One user recovered incorrect set of partitions from testdisk. Best to backup current incorrect partition table, just so you can start over if needed.
       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT.txt
So you know sectors, you need start of extended and start of swap:
sudo parted /dev/sda unit s print 

            Used parted rescue
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405) 
    
These all are either using testdisk or parted rescue. But different theads may explain process better than others.
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

### Post by huckerj2 on 2016-10-03
Its fixed! :D Thanks for the help.  I used parted rescue as suggested to search for and recover a sector from an extended partition. I found parted rescue easier to use than testdisk due to more documentation in the forums. I rebooted and GRUB is back.  I can now boot to both Windows 10 and Ubuntu just fine. Interestingly, windows recovery is the default choice in GRUB now.  I know how to fix that though.  Thanks again for all your help!

---

### Post by oldfred on 2016-10-03
Glad it worked.

Please change to solved, so others that search forum for solutions can find this thread.

---

