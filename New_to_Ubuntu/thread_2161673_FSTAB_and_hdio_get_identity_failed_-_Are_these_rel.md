---
title: "FSTAB and hdio_get_identity failed - Are these related or am I just assuming ??"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by VarunKishnani on 2013-07-11
I used Gparted to make changes to my External HDD on which Ubuntu 12.04 is Installed. Now, I understand that the FSTAB file contains details about partitions that Ubuntu uses to mount partitions.

What I want to understand is

If I make changes to my External HDD using Gparted or other software or even from the command line, do I need to Update the FSTAB file or Ubuntu updates it automatically ? 
 
I have partitioned my 150GB hard drive into a 50GB partition (ext3) that houses Ubuntu and a 100GB partition (NTFS) fot storage. During install I had marked that 100GB partition entirely as Swap (without realizing that such a large swap space is not required- i didn't know then what swap is, I don't even need swap space. ) and on startup,  it wont mount. So I reformatted it to NTFS using GParted

I recently got an **hdio_get_identity failed for '/dev/sdb' invalid argument** error. On the Ubuntu load page (when you have alternatively highlighting dots) I get the message giving me options to skip mounting, manually recover or wait. The problem resolved after I rebooted a couple of times. I think it was because of making changes using Gparted (Imade a week ago) and has something to with an un-updated FSTAB, mayb. 

Can someone through light on what could have caused that error (**hdio_get_identity failed **), At least what it means ? As for other discussions on the HDIO error, I cant understand a damn thing, sounds like rocket science to me though I am not all that dumb. 
 
By the way, the hard drive inside my machine is fully encrypted including blank space, whole drive encryption employed by the company I work for (I am an accountant). Not possible to read or mount it. That's sda. I use Ubuntu on a HDD for coding in PHP . The EHDD is sdb. 

Thanks

---

### Post by dannyboy79 on 2013-07-11
This error is produced by hdparm when using the -i switch on some SCSI and SATA disk drives. hdparm was not designed to be used with SCSI or SATA drives. No tweaks that hdparm can provide are needed for SCSI or SATA drives.

Fix: Disable any Cpanel IDE hard drive tweaks and remove any hdparm settings in local startup files.

---

### Post by hlyh1230 on 2013-11-23
hi, may i know how to do the fix?

Fix: Disable any Cpanel IDE hard drive tweaks and remove any hdparm settings in local startup files.

---

