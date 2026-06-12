---
title: "GPT image and restore hard disk test, failing to restore (using dd)"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by pursuvant on 2013-05-15
Newb to ubuntu, have a System76 gazp8 laptop, one drive, Intel 520 series SSD 240G. Doing a series of tests to ensure i can backup and restore a complete image of the laptop drive.

Boot from ubuntu live cd...
To image, execute the command (in a batch file):

sudo dd if=/dev/sda conv=sync,noerror bs=$BLOCKSIZE | gzip -c > /media/ubuntu/COOLMAX/$GZIMGDIR/$GZIMGFILE

That successfully creates the image file tar gz on the external usb drive. Size of the compressed .gz file is about 1.4G (reasonable for new laptop, with almost no new software installed yet).

Boot from ubuntu live cd...
To restore, execute the command (in a batch file):

sudo gunzip -c /media/ubuntu/COOLMAX/$GZIMGDIR/$GZIMGFILE | sudo dd of=/dev/sda conv=sync,noerror bs=$BLOCKSIZE

Runs for a few minutes, you can see the USB external drive providing data to dd, and at end it reports success, shows 240G written to /dev/sda laptop hard drive with no errors, no missing bytes.

BUT...

when i start up gparted, and find that the /dev/sda has the correct partitions defined with the right sizes, 
/dev/sda
   /dev/sda1  file system "uknown", flags "bios_grub", and "Used" space is blank !
   /dev/sda2  file system "unknown" , and "Used" space is blank ! (should be File System "ext4" with some space used)
   /dev/sda3  file system "unknown",  and "Used" space is blank ! (should be File System "linux-swap")

I'm totally lost how the restore could report success, 240G restored to /dev/sda, and then find gparted window showing the partitions have no data restored. And of course, if you try to boot the laptop in this state, it hangs at the grub loader.

Anyone know what step i am missing or doing wrong here, that is causing the restore to appear to succeed but produce no meaningful results ?

Thanks in advance

---

### Post by oldfred on 2013-05-16
That bios_grub is shown in gparted as unknown is normal. It is unformatted space.

That swap is unknown may be normal if you specified encryption for /home as then swap is encrypted and gparted cannot read nor see encrypted partitions.

But sda2 being unknown is an issue. 

What does gdisk say?

sudo apt-get install gdisk
       sudo gdisk -l /dev/sda

---

### Post by pursuvant on 2013-05-16
Thx oldfred for assistance.

Found the issue, after GPT is loaded into a new disk from the GPT  backup snapshot taken by perfroming an "sgdisk -b" (example of loading  of GPT from a snapshot backup file is below):

sudo sgdisk -l /media/ubuntu/COOLMAX/_SYS76/GAZP8_Unboxing/20130516.0130.gazp8.sda.sgdisk.backup.gpt /dev/sda

the  backup copy of the GPT on the target disk may be out of synch with this  newly loaded GPT info. To synch the GPT backup on the target disk with  the newly loaded GPT info, and check disk is in good state run (example  below):

sudo sgdisk - v /dev/sda
sudo parted /dev/sda 'print'           (this reports the existing partition info, so we know find the ext4 data partition)
sudo fsck /dev/sda2                    (file system check of only of the ext4 data partition(s) - ignore boot and linux-swap)

If  the backup copy of the GPT was out of synch, it is refreshed to same as  the newly loaded GPT after performing the three checks above, although i can not remember exactly which one of the three checks raised a notice that the backup GPT was out of synch and performed the automatic refresh of the backup GPT info.

Solved

---

### Post by oldfred on 2013-05-16
Good to know how to fix it. :)

---

