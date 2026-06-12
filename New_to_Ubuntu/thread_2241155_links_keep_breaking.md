---
title: "links keep breaking"
date: 2014-08-24
forum: New to Ubuntu
---

### Post by Saffo on 2014-08-24
hey so i am new to ubuntu. i got a system76 computer with two drives--- a smaller fasters one to run my system on and a larger one for storage.

when i make links between one drive and another they keep breaking--- i guess because the second drive is unmounted by default? but even once i mount it the links remain broken.

is there any way to fix this? i would very much like to be able to have links between directories on the two drives.

thanks!

---

### Post by ajgreeny on 2014-08-24
I'm not sure why the links do not reappear after mounting the second drive though it may be because the mountpoint changes sometimes when you mount it, presumably simply by clicking on the drive icon.

You need to edit /etc/fstab to get the disk to automount at boot time, but the edit will depend on the filesystem on the drive, and its UUID.  For that information show us the output of ```
sudo blkid -c /dev/null
```and we can tell you how to proceed further.

---

### Post by Saffo on 2014-08-24
okay, thank you

the output is:

> /dev/sda1: LABEL="Extra Drive 1" UUID="f198f987-6a25-4d4f-aee0-cb5375d4ade1" TYPE="ext4" 
/dev/sdb1: LABEL="Ubuntu" UUID="5028c8d1-940d-43b0-b074-2eee9a9a8a34" TYPE="ext4" 

---

### Post by ajgreeny on 2014-08-24
First you need to make a mountpoint folder for the drive, and you can choose wherever you want but normally it would be in /media or /mnt.  If in /media it will always show in Places in the left hand pane of your filemanager; if in /mnt it will not show there by default, but you could add it. Use commnd sudo mkdir /mnt/data.  You can call the mountpont what you want as long as you use that same name in the fstab edit.

You now need to add two lines to /etc/fstab, the first just being a line of information, the second being the system's mount instructions.
```
# Automount Extra Drive 1 data partition.
UUID=f198f987-6a25-4d4f-aee0-cb5375d4ade1 /mnt/data ext4 defaults, relatime 0 1
```
I'm almost sure the *relatime* mount option is not needed any more but it will not hurt if it's there.

After the edit, run command ```
sudo mount -a
``` and if there is no output from that (no error) all is well and you can reboot and then delete and remake all those links again and they will then always be available after you boot.

---

### Post by Saffo on 2014-08-24
hmm---- i believe there already *is* a mount point on my computer, as it does always show up on the left column. it's just not mounted until i click it.

will this make the drive always mounted?

---

### Post by oldfred on 2014-08-24
The left panel shows what can be mounted and until you click on it, it is not mounted, so that is why your links keep breaking. You need a permanent mount. It will show default mounts and uses label, size or UUIDs as default. With Linux is is best not to use spaces as you have to escape them or put quotes around them.
I use CamelCase, under_score, or justaname as labels and mount points to avoid spaces. Note in Linux case does matter where in Windows it did not. So /mnt/Data is not /mnt/data. Those would be two different mount points.

I prefer /mnt/data over /media/data since  a /mnt will not show in left panel where a /media will show in left panel. But if linking everything then you do not want another mount in left panel as it cannot mount it twice and you can get confused on why it does not work.

---

### Post by Saffo on 2014-09-12
hm, okay. 

so how do i do this? i do not see any file called fstab in my etc folder. i do see a folder called fstab.d and it's empty.

---

### Post by oldfred on 2014-09-12
You just about have to have an fstab or system will not boot.

 sudo mkdir /mnt/data

 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

Then check there are no typos, unmount if you manually mounted with Nautilus before 
      
 sudo mount -a

---

### Post by Saffo on 2014-09-12
i have no idea what you just said :/

---

### Post by oldfred on 2014-09-13
I thought you wanted the commands to edit fstab?

---

### Post by Saffo on 2014-09-13
i have no idea what "add the template with the correct UUID and mount point to fstab" means. i am new to ubuntu.

---

### Post by oldfred on 2014-09-13
See post #4 from ajgreeny. 

That is an example template of an fstab entry. I believe he changed the UUID to your UUID for your data partition as you had posted previously, so you should just copy that and paste into fstab. No other changes then would be required. 

Normally posts just show examples and you have to edit to correct UUID or mount point.

---

