---
title: "Problem swap disk not ready during boot"
date: 2015-03-08
forum: New to Ubuntu
---

### Post by Dedalus1983 on 2015-03-08
Hello to everyone, I have an error during boot process that complains about
/dev/mapper/ubuntu--gnome--vg-swap_1
being not ready. 

Now, my /etc/fstab is

-------------------------------------------------------------------------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--gnome--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=aef16176-ec01-4e97-adfc-98b9475a9f53 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--gnome--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

-------------------------------------------------------------------------------------------------------------------------------------------------
output of sudo blkid:

/dev/sda1: UUID="aef16176-ec01-4e97-adfc-98b9475a9f53" TYPE="ext2" PARTUUID="3b888e95-01" 
/dev/sda5: UUID="U0FSEp-2doA-6Ov6-CisN-66NC-LqiE-Undaj2" TYPE="LVM2_member" PARTUUID="3b888e95-05" 
/dev/mapper/ubuntu--gnome--vg-root: UUID="120322bb-5c64-4bfe-a7ab-ca677bc0a6da" TYPE="ext4" 


-------------------------------------------------------------------------------------------------------------------------------------------------
Strange enough, in /dev/mapper I can find "ubuntu--gnome--vg-swap_1" while I cannot find "cryptswap1"

Can anyone help me?
I would like to remove this problem and use the swap in the best possible way.
Ah running Ubuntu-Gnome 14.10 on new Dell Inspiron Laptop.

Thanks!!


Luca

---

### Post by dino99 on 2015-03-08
you might read that thread, which seems close to your issue (solution done: add a parameter)
[http://ubuntuforums.org/showthread.php?t=2266912](http://ubuntuforums.org/showthread.php?t=2266912)

---

### Post by Dedalus1983 on 2015-03-08
Thanks 9d9, I think that this thread is about a version yet/to/be/released of Ubuntu.
And they are trying the installation process, while I already did it and I do not want to do it again. 
I choosed to have and encrypted home directory, while I do not know which is the need of having an ecrypted swap space.
I need to fix it without installing again.
Thanks

---

