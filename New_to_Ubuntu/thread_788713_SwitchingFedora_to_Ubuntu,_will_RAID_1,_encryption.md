---
title: "Switching:Fedora to Ubuntu, will RAID 1, encryption work ?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by sudo_sk0 on 2008-05-10
**Switching: Fedora to Ubuntu, will RAID 1, encryption work ?**

Greetings Earthlings !

I would like to **switch from Fedora to Ubuntu**,
But there's currently no simple way to set up

[B][LIST=1]
[*]RAID 1, mirroring
[*]Encryption
[*]LVM(2?)
[/LIST][/B]

RAID is software (as I** do not trust the H/W raid controller**)

I need a walkthrough of how to set up these things under Ubuntu
(because there isn't much documentation available)

In windows, setting up RAID 1 is just a matter of **right-clicking**,
though encryption takes time.
Also Under Redhat(Fedora) this process is **very well documented**.

Can Ubuntu 8.04's Grub version boot from LVM ?

If you have setup such a system from alternate-cd with success,
**please help** the rest of us.

---

### Post by sudo_sk0 on 2008-05-10
Found a bug against RAID 1 in ubuntu here
**"cannot boot raid1 with only one disk"**
https://bugs.launchpad.net/ubuntu/+bug/120375
(This bug is a year old !)

Is this for real ?

Ubuntu Release team, really released an LTS version,
without proper RAID support ?

---

### Post by finite9 on 2008-05-11
I read your reply to my post in another thread, but we're talking two different things here.  You want to do raid/dmcrypt/lvm2 during install, maybe even on / and /boot partition.

I want to do this manually on two external eSATA drives, that are not part of the root file system, so I do not need to do a lot of configuring with the boot loader.  By the way, you can only use LILO if you do this, as Grub has no support for dmcrypt/lvm root in the 0.9x branch.  If you do this with the alternate cd then it will automatically use and install LILO

My thread here:

[http://ubuntuforums.org/showthread.php?t=787931](http://ubuntuforums.org/showthread.php?t=787931)

I have successfully dmcrypted/lvm'd my /home, swap and /var mount points with a hardy heron alternate cd fresh install.  This is not documented and there is no guide during the partition process, but I did it myself during the partition stage by choosing manual partition.

I did not setup raid suring install as i cannot use both my laptops internal discs because Vista is on the other disc, but I assume that it is a similar process to what I accomplished:

Create a raid container then create a dmcrypt container then create an lvm partition within both of these.  I admit that it is a bit convoluted and would be nice if there was a auto-guide that let you configure certain aspects, rather than the current partitioner guide that just wants to wipe the whole of the first disc, but it is 'do-able'.

I have manahed to raid1 and dmcrypt my 2 eSATA discs, but am unsure how to correctly LVM then as pvcreate will wipe the partition table.  this is my last hurdle.

this is what I did:

I created software raid1 with mdadm on two eSATA 500GB MyBooks:

1. ran badblocks random on both (took 48 hours)
2. created partitions on each disk with gparted (cfdisk complained, probably about no label and I didn't dare using fdisk). did not put any filesystem on the partitions.
3. used fdisk to change partition types to fd.
4. mdadm &#8211;-create --verbose /dev/md0 &#8211;-metadata=1.0 &#8211;-raid-devices=2 &#8211;-level=raid1 &#8211;-name=backupArray /dev/sd[bc]1
5. mdadm --examine --scan | tee /etc/mdadm.conf
6. did not need to assemble it here...it was done automagically.
7. used your dmcrypt howto and ran cryptsetup on the /dev/md0 device
8. opened dmcrypt and created mkfs.ext3 and mounted it. I know I don't need to do this but I just wanted to test it so far and it seems ok.

How do i now put lvm on top of this to use the whole dmcrypt device?? Doesn't pvcreate overwrite the partition table?

I posted this on Uwe Hermann's site as he is quite good at doing this sort of thing, but have not yet got a reply from him:

[http://www.hermann-uwe.de/blog/raid5-dm-crypt-lvm-ext3-debian-install-and-benchmarks](http://www.hermann-uwe.de/blog/raid5-dm-crypt-lvm-ext3-debian-install-and-benchmarks)

---

### Post by sudo_sk0 on 2008-05-11
Here are a few resources that were useful for some people,
While they might not help us, still lets list them out.

[https://help.ubuntu.com/community/Installation/RAID1](https://help.ubuntu.com/community/Installation/RAID1)
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)
[http://howtoforge.com/set-up-raid1-on-a-running-lvm-system-fedora8](http://howtoforge.com/set-up-raid1-on-a-running-lvm-system-fedora8)
[http://howtoforge.com/setting-up-lvm-on-top-of-software-raid1-rhel-fedora](http://howtoforge.com/setting-up-lvm-on-top-of-software-raid1-rhel-fedora)
[http://dev.jerryweb.org/raid/](http://dev.jerryweb.org/raid/)
[http://www.damtek.com/](http://www.damtek.com/)
[http://songshu.org/doku/doku.php?id=host.cipar.net](http://songshu.org/doku/doku.php?id=host.cipar.net)
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)
[http://www.hermann-uwe.de/blog/raid5-dm-crypt-lvm-ext3-debian-install-and-benchmarks](http://www.hermann-uwe.de/blog/raid5-dm-crypt-lvm-ext3-debian-install-and-benchmarks)

Yes some people will say why encrypt all partitions/volumes,
I say its possible to **switch a binary** with a carefully crafted binary hack,
that will easily **compromise your encryption security**.

---

### Post by finite9 on 2008-05-12
What you want to do is already detailed in the wiki:

[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)

It does not detail dmcrypt, but this is quite easy to add in the middle of raid and lvm.  instead of using /dev/md0 as your physical volume in lvm setup, just use the /dev/mapper/<name> of your dmcrypt device instead.

---

### Post by AlexanderDGreat on 2009-11-07
> **sudo_sk0 said:**
> Found a bug against RAID 1 in ubuntu here
**"cannot boot raid1 with only one disk"**
[https://bugs.launchpad.net/ubuntu/+bug/120375](https://bugs.launchpad.net/ubuntu/+bug/120375)
(This bug is a year old !)

Is this for real ?

Ubuntu Release team, really released an LTS version,
without proper RAID support ?

Yeah, it's a shame. I don't want to whine and complain, but is there any EASY solution to this?

---

