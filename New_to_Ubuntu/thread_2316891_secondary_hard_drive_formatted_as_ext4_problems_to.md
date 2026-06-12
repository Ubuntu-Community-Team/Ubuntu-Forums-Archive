---
title: "secondary hard drive formatted as ext4 problems to run scripts"
date: 2016-03-11
forum: New to Ubuntu
---

### Post by elico2 on 2016-03-11
Hi,

I have ubuntu running on an SSD drive and I have another larger drive which is mounted in fstab as follows:
/dev/sdb1       /home/elico/data      ext4    rw,auto,user    0       1

I have installed android studio on this drive but for some reason I can't get to run the sh ./android-studio/bin/studio.sh and I get permission denied.

I tried to chown to /home/elico/data and also add permission (chmod a+x) but nothing seems to help.

If I run 
sh ./android-studio/bin/studio.sh
then it works, but I can't create a desktop entry since it says no valid executable script.

Please help me to understand what I am doing wrong.

Thanks,
Eli

---

### Post by oldfred on 2016-03-12
I am not the expert on mount options.
But suggest using defaults or relatime.

 Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async 

I use this for my /mnt/data

 sudo chmod -R a+rwX,o-w /mnt/data 
sudo chown -R $USER:$USER /mnt/data 
      
 # Note that the -R is recursion and everything is changed, do NOT run on any system partitions.

Seems like a better way as you have more control over what is executable. See post #8 & 10 by morbius1.
[URL="http://ubuntuforums.org/showthread.php?t=1795369"]http://ubuntuforums.org/showthread.php?t=1795369
[/URL]
Or:
chmod -R a+rwX,go-w /path/to/folder
sudo chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

---

### Post by elico2 on 2016-03-12
Hi,

Thank you.

For reference to others that might experience that problem, I fixed it by changing fstab with the following:

/dev/sdb1       /home/[COLOR=#000000]elico[/COLOR]/data      ext4    defaults        0       1

I changed the options to defaults (which includes *exec* I was missing).

Thanks,
Elic

---

### Post by oldfred on 2016-03-13
Better to use UUID rather than device.

With both my old BIOS system and new UEFI system, device numbers have changed on me,  just by plugging in flash drive.
I think it was because I skipped a SATA port and on UEFI system DVD was in SATA1.
BIOS system had several drives and flash drive as sdf when plugged in. On reboot flash drive became sdb and every other drive went up a letter.
If you use UUID then device changes do not matter, system will find correct partition.

---

