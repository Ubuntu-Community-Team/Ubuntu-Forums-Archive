---
title: "Having trouble with my filesystem"
date: 2016-07-24
forum: New to Ubuntu
---

### Post by chris331 on 2016-07-24
Hello all, I've had great success using these forums for fixing problems I've had in the past, so I'm giving it another go.
I have a logical volume filesystem.
I need to enlarge one of my partitions/LVs to make room.. it's 30g capacity is now full.  When I first installed the my OS, I had it partitioned so that my /etc, /usr, and /root directory trees were on a smaller partition, and my /home was on the biggest partition.

I foolishly tried copying my /etc and /usr directory trees over to my /home directory.. but I don't need help with the cleanup of that disaster.. that's already taken care of.

I need help enlarging my volume/partition that only has 30G on it.

Here is some info on my filesystem:

at the terminal:

```

root@KandA:/etc# vgdisplay
  --- Volume group ---
  VG Name               KandA-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               3
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               465.52 GiB
  PE Size               4.00 MiB
  Total PE              119173
  Alloc PE / Size       119173 / 465.52 GiB
  Free  PE / Size       0 / 0   
  VG UUID               epV82A-6It2-kfKs-uJ1q-HEsn-3j4L-b8VB2N


```

and

```

root@KandA:/etc# lvdisplay
  --- Logical volume ---
  LV Path                /dev/KandA-vg/root
  LV Name                root
  VG Name                KandA-vg
  LV UUID                87EScU-sFY9-3utM-mOeR-RnzL-9X5Y-9vVabt
  LV Write Access        read/write
  LV Creation host, time KandA, 2016-07-12 19:50:34 -0600
  LV Status              available
  # open                 1
  LV Size                27.94 GiB
  Current LE             7152
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:0
   
  --- Logical volume ---
  LV Path                /dev/KandA-vg/swap_1
  LV Name                swap_1
  VG Name                KandA-vg
  LV UUID                vO6Hk8-cAoG-1o6w-2V2k-wD8d-3bmo-UJI5mM
  LV Write Access        read/write
  LV Creation host, time KandA, 2016-07-12 19:50:34 -0600
  LV Status              available
  # open                 2
  LV Size                11.64 GiB
  Current LE             2979
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:1
   
  --- Logical volume ---
  LV Path                /dev/KandA-vg/home
  LV Name                home
  VG Name                KandA-vg
  LV UUID                F9aKJO-KNds-R2Nd-9weh-Lkgw-9HNV-fNU9jm
  LV Write Access        read/write
  LV Creation host, time KandA, 2016-07-12 19:50:34 -0600
  LV Status              available
  # open                 1
  LV Size                425.95 GiB
  Current LE             109042
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:2


```


Still at the terminal:

```

root@KandA:/etc# blkid
/dev/sda1: UUID="371b8f2f-ccef-40d8-80ca-df20139f123b" TYPE="ext2" PARTUUID="b1ae3941-01"
/dev/sda5: UUID="GfTMEG-NPCe-Vkw3-cbqp-nXOs-Bcrm-zcnqzF" TYPE="LVM2_member" PARTUUID="b1ae3941-05"
/dev/mapper/KandA--vg-root: UUID="2c26bd85-0f96-4800-a09d-a81cda07d35c" TYPE="ext4"
/dev/mapper/KandA--vg-swap_1: UUID="ccc5dfea-29eb-468a-ae4b-9e4b6c6f9e85" TYPE="swap"
/dev/mapper/KandA--vg-home: UUID="f7928f21-5453-4cbf-a215-2cd4c3783e76" TYPE="ext4"


```

My /etc/fstab file contains this:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/KandA--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=371b8f2f-ccef-40d8-80ca-df20139f123b /boot           ext2    defaults        0       2
/dev/mapper/KandA--vg-home /home           ext4    defaults        0       2
/dev/mapper/KandA--vg-swap_1 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0

```


Thanks in advance.

---

### Post by chris331 on 2016-07-24
Postscript:
I don't know much about logical volumes and groups... they're not used much in the Windows arena, where I spent most of my time until just recently.  If someone could help me with the step of enlarging the correct partition, or if that's not possible, tell me me what my options are.  Because right now, the partition that has my /etc. /usr, /root, and other important directory trees is filled, and I don't know what to do next.

---

### Post by Bucky Ball on 2016-07-24
If you have a separate /home and you're needing more than 30Gb for your / partition, something is not right. 

Are you sure you cleaned up nicely? You haven't junk still on the / partition? Did you empty trash? Have you created a heap of partitions for various things, like /var, /etc, /boot? (You don't need to for a standard install). 

If you have Gparted, please take a screenshot of that so we can see what you've got and attach to a post, thanks ('Go Advanced'> paperclip icon). Gparted can be installed from the repos, but you might not have much luck if you're getting disk full. You can also download a Gparted ISO and create bootable media to use it.

---

### Post by chris331 on 2016-07-25
Hm, well I took some screenshots of my system as analyzed by Gparted, as well as screenshots of my directory tree from Krusader, showing that in / I have used almost all of my 30G of space, and in /home I have the rest of my HDD space.

---

### Post by chris331 on 2016-07-25
.. I don't know if the Ubuntu forums have a problem with my handshake, but I keep getting this error: 
[h=1]Forbidden[/h] You don't have permission to access /editpost.php on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443


When I try to attach the screenshots to the post.

---

### Post by Bucky Ball on 2016-07-25
We are having issues. Bear with us. :)

[QUOTE=Bucky Ball]Did you empty trash? Have you created a heap of partitions for various things, like /var, /etc, /boot?[/QUOTE] 

Please confirm. Empty trash and please run these commands:

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

That last command will *not* upgrade your current OS to a newer one (are you using 16.04? If so, you can use 'sudo apt update' without the '-get'). After these commands, reboot.

---

### Post by chris331 on 2016-07-25
> **Bucky Ball said:**
> We are having issues. Bear with us.    Please confirm. Empty trash and please run these commands:  ```
sudo apt-get autoremove sudo apt-get autoclean sudo apt-get clean sudo apt-get update sudo apt-get dist-upgrade
```  That last command will not upgrade your current OS to a newer one (are you using 16.04? If so, you can use 'sudo apt update' without the '-get'). After these commands, reboot.  Emptied trash, and ran the commands in the terminal as requested, then rebooted. I'll add the screenshots as attachments as soon as I'm able to. The board right now is hardly letting me post replies right now. Krusader says I have 3G out of 27G available in '/' and 380G free on '/home.'

---

### Post by Bucky Ball on 2016-07-25
How did you create /home? Are you positive there is not a /home directory inside / and then a /home partition named /home which is mounted somewhere like /media/<username>/home? Did you create /home as part of the install and is this a reasonably recent install?

I'm wondering if your data is going into a /home directory in / rather than to the /home partition. Is the /home partition growing at all when you put stuff in /home? These is just a thought, but have a look around.

You might also like to look in /var/log and see if one of the folders in there has gotten overly large for some reason.

This one seems to be getting under the radar so I will ask it again. Have you created a heap of partitions for various things, like /var, /etc, /boot?

---

### Post by chris331 on 2016-07-25
I have fixed the issue.  I feel this may become a problem for future linux users in the future so I'm going to both change this thread property to "Solved" and then post how I fixed the problem.. Fingers crossed that Ubuntu Forums will allow me to do this.
Thanks goes to Bucky Ball for all his help. =)

---

### Post by chris331 on 2016-07-25
Ok so my issue was that when I created my OS, the installation USB I was using asked me if I wanted to partition my drive with logical volumes as an option. I chose yes.  It then asked me if how I would like to partition my drive, and I chose for it to be partitioned into two major partitions, which also happened to include a third, small, swap partition.
So I had a 30G "root" partition, a 350G "home" partition, and a small swap.
I began installing a LOT of stuff onto my machine, not just packages using apt-get on the command line, but also downloading source code for fairly large programs that I would build and make.
So eventually I ran out of space in my 30G root partition.
The simple fix for this, that I found, is to use a live USB to boot from, download a logical volume management program:

```

sudo apt-get install system-config-lvm

```

Then run it:

```

sudo system-config-lvm

```

It has a gui, so it's very easy to use.  You click on the logical volume that has the bulk of your HDD, and/or the volume you can spare some space to give to the volume that is running out.  This volume you have to decrease in space.  I decreased mine by 50gigs.  Then I clicked on the logical volume that needed to be increased, my 'root' labelled volume.  I increased that by the difference.
So my new 'root' partition is now 90G, my 'home' partition is now 300G, and my swap is exactly the same because I didn't mess with it.
Please keep in mind that if you're going to resize your partitions/volumes, they must be currently unmounted and unused, thus you must be doing this from a utility disk or a live USB.
After I resized those 2 partitions, I rebooted, and everything is fine.
Buckyball if you want to weigh in on this if I'm giving bad advice, or else not making myself clear to others, please do.
And thank you once again for your help.

Cheers. 
Chris

---

### Post by Bucky Ball on 2016-07-26
Thanks for that. Yes, if you solve something, chuck the fix up here to help others. Appreciated. :)

---

