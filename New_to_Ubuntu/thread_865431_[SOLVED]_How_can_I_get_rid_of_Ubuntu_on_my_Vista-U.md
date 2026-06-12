---
title: "[SOLVED] How can I get rid of Ubuntu on my Vista-Ubuntu Dual-Boot?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Seablue on 2008-07-20
Hi all,

After about a month of using a dual-booted Vista-Ubuntu, I decided that I don't use Ubuntu that much and would like to gain my 10GB back. So I am asking you on how to delete Ubuntu and reclaim that space on Vista. To clear things up, I have a Vista Restore Disc, and I have the Ubuntu Live-CD/Installation Disc. I'm not sure if any of this will help, though.

Thanks,
Seablue.

---

### Post by TSS on 2008-07-20
You should be able to do all this within Vista.

Click on the Start Menu, right click Computer, click Manage.  On the left hand side go to the Storage catagory and click Disk Management.  You should see your partitions.  Use the interface to delete your Ubuntu partition and extend your Vista partition into the empty space.

Before you do that, you probably need to repair the Master Boot Record.  Insert your Vista recovery CD and select, Repair an Installation.  That should fix things up.  Do that BEFORE you delete the Ubuntu partition.

---

### Post by The Cog on 2008-07-20
But replace the bootloader first!
Sorry, I don't know how to do that with Vista, but I know you need to before removing the Ubuntu partition or you will render the box un-bootable. GRUB relies on files in the Ubuntu partition.

---

### Post by michael_1234 on 2008-07-20
> **Seablue said:**
> After about a month of using a dual-booted Vista-Ubuntu, I decided that I don't use Ubuntu that much and would like to gain my 10GB back. So I am asking you on how to delete Ubuntu and reclaim that space on Vista. 

Rather than resizing partitions (resizing the windows partition to encompass the linux partition, eg using a gparted boot CD), I'd just reformat that Linux (Ubuntu) partition to NTFS or FAT32 and make it a completely separate drive (eg, a "D" drive ...depending on your setup.)   

(...I've had windows ntfs partitions totally unrecoverable before... quite often, actually... so I tend to separate the files anyway, into (1) files I don't mind loosing -- eg, windows -- and (2) the files I don't want to loose -- eg, my files).

Feel free to wreak havoc on that ubuntu partiton. Erase, re-partition, re-format... But, still, backup your windows before you do anything; it's pretty easy to erase the wrong OS. :-)  ("wrong OS" being relative/subjective, of course :-) )

-michael

---

### Post by Seablue on 2008-07-20
> **TSS said:**
> You should be able to do all this within Vista.

Click on the Start Menu, right click Computer, click Manage.  On the left hand side go to the Storage catagory and click Disk Management.  You should see your partitions.  Use the interface to delete your Ubuntu partition and extend your Vista partition into the empty space.

Before you do that, you probably need to repair the Master Boot Record.  Insert your Vista recovery CD and select, Repair an Installation.  That should fix things up.  Do that BEFORE you delete the Ubuntu partition.

When I do this, do I do anything in the command line, like bottrec.exe /fixmbr
or am i just choosing Vista?

---

### Post by Seablue on 2008-07-21
OK, i did it. Thanks everyone.

---

