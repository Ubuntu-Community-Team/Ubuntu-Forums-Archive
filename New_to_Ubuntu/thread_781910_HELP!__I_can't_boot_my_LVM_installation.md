---
title: "HELP!  I can't boot my LVM installation"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by skyout on 2008-05-04
I am trying to set up a 8.04 AMD64 desktop installation with LVM and RAID1.  I used the alternate install CD and followed the instructions to get a working installation with two RAID volumes /dev/md0  and /dev/md1.  /dev/md1 became the only physical volume in my volume group, and the location of the only logical volume:  /root.  I then decided to try and set up another RAID array (/dev/md2) and add it to my volume group and extend the logical volume onto it.  This all seemed to work fine, and lvdisplay showed everything just as I would expect.  I then rebooted the computer, and the boot sequence hung after detecting /dev/md0 and /dev/md1.  Finally after a long wait it came back with: "couldn't find device with uuid ...." and "couldn't find all physical volumes for volume group"  and "volume group .... not found" and then  dumped me into a crippled shell prompt.

Anything I have found so far for recovery assumes that you have access to things like /etc/lvm/backup, but I can't get at anything, since I can't boot the filesystem.  If I try the live CD, I can boot and see all three hard drives, but I can't mount them.  My questions are:

1.  Can I do anything to recover this installation?
2.  Is it really stupid to have the system as part of the LVM?
3.  How should I set this up to avoid losing my whole system and all my data should this happen after I have committed to it?

Right now I am very skeptical of LVM and a little skeptical of RAID, so anything that could provide some encouragement would be appreciated.

Thanks!

Dave C.

---

### Post by skyout on 2008-05-07
Wow!  The silence is deafening.

I finally managed to figure out how to mount RAID1 + LVM volumes after booting with the live CD.  In case any other poor soul stumbles into this catacomb looking for salvation, here's what I did:

1. boot from the Ubuntu 8.04 Desktop AMD-64 CD 
2. sudo apt-get install mdadm lvm2
3. sudo mdadm -A -s
4. sudo lvdisplay (to get the lv pathname - needed for the next step)
5. sudo modprobe dm-mod
6. sudo lvchange -a y <put in lv pathname from above>
7. sudo mkdir /media/recover
8. sudo mount <put in lv pathname from above> /media/recover

That's it.  Now the lv is available for tinkering just like as if it were a regular file system in a regular broken Ubuntu installation. 
[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by skyout on 2008-05-08
Hmmm... Is anybody reading this?  Or am I just rambling to myself.  No matter, I'll just keep pooping this out hoping that it will help someone else, or that maybe someone who actually knows what they are doing (not me) will have some insight.

Recap - the original problem:  Performed a RAID1 + LVM install of Ubuntu 8.04 from the Alternate CD, tinkered around a bit, then rebooted and was greeted with a bunch of (to me) mumbo-jumbo and then (initramfs).  I completely destroyed the installation trying to figure out what to do, but eventually I came up with the above way of mounting a RAID1 LVM with the live CD, re-installed and tested everything out - no problems.  Now at least I was confident that if I broke things I could at least mount the FS from a live CD.

The plot thickens - Now I decided to add another RAID1 volume and introduce that as a PV into my VG.  So now I have three RAID1 volumes:  /dev/md0 (as /boot - not in the LVM), and /dev.md1, and /dev/md2 (as PV's in my VG).  I re-boot and voila!  The original problem is back!  This time I was a little more gentle in my poking around, an I discovered that /dev/md0 and /dev/md1 were there, but /dev/md2 was nowhere to be found.  Apparently LVM crashed trying to find this non-existent PV.  I booted from the live cd and verified that everything was still there and OK - yes.  Reboot, and same problem.  This sounds a lot like this bug: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/52740](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/52740) but it seems like it would have been fixed by now.  I was able to continue and successfully boot by doing: 'mdadm -A -v /dev/md2 /dev/sda3 /dev/sdb3'

Note that 'madadm -A -v -s' returned '/dev/sdb3 is not built for host' and '/dev/sda3 is not built for host', so it seems necessary to explicitly call out the relevent volumes, rather than scanning for them.

So now I can boot my system, but it is a little cumbersome to type 'mdadm -A -v /dev/md2 /dev/sda3 /dev/sdb3' in the middle of the boot sequence.  And who knows what will happen if I add more PV's to the VG.  Any suggestions for a clean fix to this?  Is it a bug or am I doing something stupid?  Anybody?

dbc

---

