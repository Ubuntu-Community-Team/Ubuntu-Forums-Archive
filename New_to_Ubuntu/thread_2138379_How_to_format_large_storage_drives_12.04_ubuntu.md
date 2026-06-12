---
title: "How to format large storage drives 12.04 ubuntu"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by snuffy47 on 2013-04-23
Hello

I am going to format 2 1TB drives, 2TB drive and 3TB drive

In the disk utility the section at the top format drive: Erase or Partion the drive has the options for Master boot record, GUID, Dont Partition, appl;e partition

Which one do i use?  My operating system is on a separate 500GB drive

I will be Formating the volumes to EXT4 which I know how to do I think :)

---

### Post by papibe on 2013-04-23
Hi nuffy47.

In the case of disks which sizes are 1TB and 2TB, it not that important.

However, MBR (or MSDOS) supports up to 2TB, so to fully take advantage of a 3TB disk you need to create a GPT partition table (GUID).

Does that help? Let us know how it goes.
Regards.

---

### Post by snuffy47 on 2013-04-23
Should I then just do them all with GUID?

---

### Post by papibe on 2013-04-23
> **snuffy47 said:**
> Should I then just do them all with GUID?
Sounds good to me ;)

---

### Post by oldfred on 2013-04-24
I use gpt on all my new drives and first used it on my 160GB drive when installing 10.10. Once configured I have not really noticed any issues.

If you ever would want to install Windows, Windows only boots from gpt drives with UEFI not BIOS. Ubuntu boots from gpt with either UEFI or BIOS.
I do add an efi partition and a bios_grub partition to the start of all my gpt drives. Then I can boot Ubuntu with BIOS or UEFI as I have the needed extra partitions. It is hard to add partitions at the beginning of a drive when you have lots of data.  Both are small efi - 250MB and bios_grub 1MB, so they do not really waste any space.

I also believe every drive should have an operating system. I followed this blogs theories.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by snuffy47 on 2013-04-24
Okay I like the information

The Knoppix Partition Doc makes sense and I will noodle this alittle

---

### Post by oldfred on 2013-04-24
I prefer Ubuntu primarily since I know it, but it needs 10 to 25GB. I normally use 25GB, but even my working install with many apps and .wine with Picasa using 1.5GB, I only  have used  a total of 9GB. All data is in other partitions.
 But with new drives of TB capacities even 25GB is not much.

---

