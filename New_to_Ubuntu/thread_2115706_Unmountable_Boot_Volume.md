---
title: "Unmountable Boot Volume"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by bootvolume on 2013-02-13
Hi I got the umnountable boot volume on my laptop and it won't boot up  which led me here. I didn't backup my files and need to get them backed  up. I called best buy geek squad they said it would be over $100 to fix  which led me to searching for other ways to fix it myself. How hard is  the process of recovering my data using unbuntu for a newbie? Should I  let best buy do it? I downloaded unbuntu's latest version and went to  burn it to a cd but unbuntu is 734mb ND THE CD ONLY HOLDS 700MB'S what  is the problem here?

---

### Post by oldfred on 2013-02-13
Welcome to the forums.

The new versions are oversize. You have to use DVD, but most are using flash drives now as then they are reusable.
       [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
    
What is the format of the partition(s) you have issue with.

Post this from liveCD/DVD/Flash once you get it going.
       sudo parted /dev/sda unit s print
    

It may be as simple as a fsck if ext3 or ext4 formatted. Or you may need testdisk which you can download into the live installer.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by bootvolume on 2013-02-15
I downloaded unbuntu 12.0 and burned it on a dvd put it in my laptop and unbuntu started loading right away. But it's stuck on the waiting for network configuration screen. Does anyone know whay this is happening and what I can do?

---

