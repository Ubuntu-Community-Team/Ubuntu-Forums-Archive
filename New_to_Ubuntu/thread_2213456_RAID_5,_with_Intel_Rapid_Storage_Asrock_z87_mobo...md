---
title: "RAID 5, with Intel Rapid Storage? Asrock z87 mobo..."
date: 2014-03-26
forum: New to Ubuntu
---

### Post by gnl.weirdness on 2014-03-26
So I set up RAID 5 in the bios, that all went well and such, I have 4 drives total. 2 of which are currently showing in disk util as Not Partitioned, with no partition type, and the other 2 are showing as Unknown Scheme with partition type being Linux LVM...

I am curious if the raid controller needs a while to run and set this all up and I should just leave it over night, or is there some driver I need?

I have no way of telling how the set up is going progress wise, and when I go back into the Bios it just says status "normal".

Anyone have any thoughts?

Cheers

---

### Post by gnl.weirdness on 2014-03-27
anyone? have googled a ton, it seems that raid 5 is typical set up on the software end. I just find it so hard to believe no one else is running this board with raid 5 in ubuntu using the on board chip... Unless I am missing something grand, which I very well might be.

---

### Post by oldfred on 2014-03-27
I do not know about RAID, but thought Intel SRT was mostly to speed Windows boot.

 [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

If you have BIOS RAID, that is also called FakeRaid. Most Linux user use Linux software RAID.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

If UEFI you still need an efi partition outside of the RAID as it does not have RAID drivers. Some have /boot partition also outside RAID as that is a bit easier I think, but grub had RAID driver to load kernels from a /boot folder in / inside the RAID.

---

### Post by gnl.weirdness on 2014-03-28
ahhh ok so I guess I do just have BIOS raid then, so I guess I will follow the steps in that link you shared and see how that works out.

Cheers

---

### Post by arias2 on 2014-03-29
I don't really understand what you mean 'setup'. If you do a bios raid, you really don't need to set anything up in the software. It should be visible in /dev/mapper for dmraid or /dev/md for mdadm, whichever raid utility you choose to make your primary.

For instance, in dmraid to activate your raid just do a 'dmraid -ay'.

Raid 5 is supported in the latest kernels. It's not supported on the 13.10 install images though, but it will be in the upcoming trusty release.

---

