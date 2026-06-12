---
title: "Formatting drive for dual boot system"
date: 2016-01-21
forum: New to Ubuntu
---

### Post by Kim_Holder on 2016-01-21
I got into a bind trying to install Windows and Ubuntu 14. I installed windows and then I used Ubuntu as a live CD and it couldn't see the Windows partition. I had some trouble but I was able to reinstall windows after formatting the drive, or that is,  after Windows redid the file system. This time Ubuntu could see the partitions. Because of some other stuff someone advised me to use a command line to delete the first 10 megabytes of the disk. I did that and then he wasn't sure what for me to do next. Gparted no longer sees the partitions but the disk utility does. Once I removed the live CD  the system now won't boot at all. So I'm annoyed and now I'm not sure how to format the drive and start over again.

mkfs -t ntfs 
Maybe that is what I need to do using the LiveCD again but I'm not sure. Please advise and thanks very much.

---

### Post by grahammechanical on 2016-01-21
> I was able to reinstall windows after formatting the drive, or that is,  after Windows redid the file system.

What is stopping you doing that again? You might need to create a new partition table and then use the Windows install disk to format the drive and then install Windows.

What version of Windows is this? 7 or 8 or 10. It makes a difference to how we install Ubuntu.

Regards

---

### Post by Kim_Holder on 2016-01-21
The system no longer sees the windows I had installed already so yes I think I need to make the partition table again and I don't know how to do that. I was told the command I entered erased completely the first 10 mb of the drive.

The thing is from within Windows install disk it doesn't actually format the drive it just creates a new file system. Considering what I've already done that may be insufficient.

I'm trying to install 64 bit Windows 7, alongside Ubuntu 14.04 64 bit.

I just tried using the Windows installation disk to reinstall and it tells me windows cannot be installed to this disk. The error message says ' windows cannot be installed to this disk. This computer's hardware may not support booting to this disk. Ensure that the disks controller is enabled in the computers BIOS menu.'

dd if=/dev/zero of=/dev/sda bs=1M count=10.

That's the command that was used

---

### Post by oldfred on 2016-01-21
Do not run the dd command, that is just to corrupt your system. While some systems may need part of drive erased, you never do that after an install and only to MBR or first sector.

Is system UEFI or BIOS? 
Drive gpt or MBR(msdos)? 
But either way you erased essential partition table and boot from MBR or gpt primary partition table.

If drive was partially erased, Windows should be seeing it as a blank drive. 

Does gparted from Ubuntu live installer now show drive as blank. It should.
Only if gpt, you may still have backup gpt partition data which is at end of drive.
Post this:
sudo gdisk -l /dev/sda

---

### Post by Kim_Holder on 2016-01-21
After asking around more i was advised that since the Windows installer saw the whole disk, i could tell it to create a new partition and it would set that up and it would be fine. I was waiting on answers here and on Ask Ubuntu so i saw no harm in trying. Windows installed fine on a partition i made for it of 100 Gb. I had checked Gparted before that and it was showing the whole disk unallocated, while the disk utility saw partitions. 

After that i ran Ubuntu 14 as a LiveCD and it could see the partitions Windows created. So i went ahead and installed 14.04, choosing the option to run a loader alongside the Windows loader. That also went fine.

I've been without my computer for a couple of days now because of this and related stuff, so i couldn't wait. Fortunately it worked out.

I have been advised by the same people (in a chat room with a pretty geeky population, though i sort of think if i'd stayed out of it today and just asked for advice here it would have been better) not to update Windows to the more recent versions. They think Windows might mess up grub. That's fine by me, i only wanted Windows because of one program i just can't get on Ubuntu and need.

---

### Post by oldfred on 2016-01-22
Windows updates often mess up grub.
You should always have a working Ubuntu live installer to make repairs.
But Windows also needs repairs, sometimes, so you need the Windows repairCd or flash drive.

If a BIOS install, Windows may erase partition table and not restore Linux logical partitions in the extended partition. All versions have done this, but now the Windows 7 to 10 update does it also. Best to backup partition table with sfdisk if updating Windows.

If a UEFI/gpt update, there is no partition issue, and grub is not overwritten, but Windows regularly resets itself as first in UEFI boot order.

---

