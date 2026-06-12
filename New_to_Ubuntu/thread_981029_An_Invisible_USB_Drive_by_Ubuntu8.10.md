---
title: "An Invisible USB Drive by Ubuntu8.10"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by flutti-tutti on 2008-11-13
Ubuntu 8.10 does not recognize a USB NTFS-drive at all, although virtual (guest) Vista and SUSE on VirtualBox can read/write its files.    

The USB drive is totally invisible in the host Ubuntu. 

What should I do?   I am new to Ubuntu/Linux.
Thanks for your time.

---

### Post by lswest on 2008-11-13
could you please post the output of this command while the device is plugged in: ```
sudo fdisk -l
```

---

### Post by flutti-tutti on 2008-11-13
> **lswest said:**
> could you please post the output of this command while the device is plugged in: ```
sudo fdisk -l
```

the output of the command is --
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2705644f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32873   264046076    7  HPFS/NTFS
/dev/sda2           32874       60801   224331660    5  Extended
/dev/sda5           32874       60093   218644618+  83  Linux
/dev/sda6           60094       60801     5686978+  82  Linux swap/Solaris

--- end of the output

thanks for your response.

---

### Post by lswest on 2008-11-13
It seems the disk isn't recognized at all by Ubuntu.  Have you tried it in another computer (not a virtual machine)?  Also, try removing the device and then re-inserting it and running ```
sudo dmesg|tail
``` and post that output here, to see if any errors are occurring.

---

### Post by prshah on 2008-11-13
> **flutti-tutti said:**
> 
The USB drive is totally invisible in the host Ubuntu. 


Open a terminal (Applications-Accessories-Terminal), unplug your drive, wait 10 seconds, plug it in, then give this command and post the output here```
sleep 10 && dmesg | tail
``` this step is only for more information, it will not (should not) solve the problem.

---

### Post by flutti-tutti on 2008-11-13
> **lswest said:**
> It seems the disk isn't recognized at all by Ubuntu.  Have you tried it in another computer (not a virtual machine)?  Also, try removing the device and then re-inserting it and running ```
sudo dmesg|tail
``` and post that output here, to see if any errors are occurring.

After the device was removed and reinserted, the output of the command is ---

[11835.057884] sd 14:0:0:0: [sdb] Write Protect is off
[11835.057902] sd 14:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11835.057912] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[11835.059635] sd 14:0:0:0: [sdb] 312581809 512-byte hardware sectors (160042 MB)
[11835.060872] sd 14:0:0:0: [sdb] Write Protect is off
[11835.060886] sd 14:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11835.060892] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[11835.060907]  sdb: sdb1
[11835.087673] sd 14:0:0:0: [sdb] Attached SCSI disk
[11835.088042] sd 14:0:0:0: Attached scsi generic sg2 type 0
----- End of Output

There is no problem with Vista, after it automatically downloaded a certain driver.
  
Ubuntu 8.10 still has the same problem, -- the USB drive is not recognized.  (Both Vista and Ubuntu are not on the virtual machine.)

---

### Post by lswest on 2008-11-13
according to this section > [11835.060907] sdb: sdb1 the device should be recognized.  I'm kind of lost as to why it isn't.  The only thing I can suggest is re-running sudo fdisk -l to see if the device is recognized now, otherwise try this: ```
sudo mkdir /media/USB\ Drive/
sudo mount -t ntfs-3g /dev/sdb1 /media/USB\ Drive/
``` it might just work.  If not, we'll have to wait for someone with a fresh set of ideas.

---

### Post by flutti-tutti on 2008-11-13
> **prshah said:**
> Open a terminal (Applications-Accessories-Terminal), unplug your drive, wait 10 seconds, plug it in, then give this command and post the output here```
sleep 10 && dmesg | tail
``` this step is only for more information, it will not (should not) solve the problem.

the output of the above command is ---
[13065.504680] sd 15:0:0:0: [sdb] Sense Key : No Sense [current] 
[13065.504698] sd 15:0:0:0: [sdb] Add. Sense: No additional sense information
[13065.661198] sd 15:0:0:0: [sdb] Sense Key : No Sense [current] 
[13065.661214] sd 15:0:0:0: [sdb] Add. Sense: No additional sense information
[13065.817594] sd 15:0:0:0: [sdb] Sense Key : No Sense [current] 
[13065.817612] sd 15:0:0:0: [sdb] Add. Sense: No additional sense information
[13065.974001] sd 15:0:0:0: [sdb] Sense Key : No Sense [current] 
[13065.974023] sd 15:0:0:0: [sdb] Add. Sense: No additional sense information
[13066.130388] sd 15:0:0:0: [sdb] Sense Key : No Sense [current] 
[13066.130407] sd 15:0:0:0: [sdb] Add. Sense: No additional sense information

---- End of the output

---

### Post by flutti-tutti on 2008-11-13
> **lswest said:**
> according to this section  the device should be recognized.  I'm kind of lost as to why it isn't.  The only thing I can suggest is re-running sudo fdisk -l to see if the device is recognized now, otherwise try this: ```
sudo mkdir /media/USB\ Drive/
sudo mount -t ntfs-3g /dev/sdb1 /media/USB\ Drive/
``` it might just work.  If not, we'll have to wait for someone with a fresh set of ideas.

The command, "sudo fdisk -l", was re-run, and the device is not still recognized.

The commands of mkdir and mount were tried, but did not work unfortunately.
Thanks for your time.

---

### Post by timcredible on 2008-11-13
add the package 'ntfsprogs' via synaptic to be able to work with ntfs drives.

---

### Post by Barlennan on 2008-11-26
It's probably a not-quite-standard USB enclosure.  Intrepid is stricter, but fortunately that can be fixed.  See cansei's posts in [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983")

---

### Post by flutti-tutti on 2008-12-18
Thanks for your responses.

Based on cansei's posts in [https://bugs.launchpad.net/ubuntu/+s...ev/+bug/221983](https://bugs.launchpad.net/ubuntu/+s...ev/+bug/221983), the files of "40-permissions.rules" and "60-persistent-storage.rules" were replaced in the folder /etc/udev/rules.d/.

After that, the external USB drive is recognised, and files can be accessed. [http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

