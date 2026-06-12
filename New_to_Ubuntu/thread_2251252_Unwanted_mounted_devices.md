---
title: "Unwanted mounted devices"
date: 2014-11-03
forum: New to Ubuntu
---

### Post by AzuObs on 2014-11-03
Fellow users, I have just installed your favorite OS on my laptop. It's a dual boot setup on the same hard drive. Which I've read somewhere; was asking for trouble.

So far, everything seems dandy. My "computer" has the 50go I wanted it to have, my "movies, pictures, etc" is another 60 and I also have 8go just incase my RAM is completely full. That's good - I'm only going to be using Ubuntu for web development and if I need more space I'm sure I'll find a way.

My problem is that some of my other partitions are showing up in "Devices", and when I try to unmount them, they don't want to go away. I have attached a screenshot for your viewing pleasure. I don't want those listed there as it could mess up my windows OS if they were somehow sallied. 

[ATTACH=CONFIG]257718[/ATTACH]

The partitions are called "Acer", "387MB Drive", etc. I think that my Ubuntu my think those partitions of the hard drive are for it. Greedy bastard.

---

### Post by Bucky Ball on 2014-11-03
??

Welcome. That looks like your Ubuntu /home folder or partition. What is 'Push Button R..'?  ... :-k 

You definitely DO want them there. Nothing to do with Windows. Doesn't look like the Win partition is even mounted, and if you haven't installed ntfs-3g or done it manually, they probably aren't.

Open Gparted and take a screenshot of that drive. Also, what release of Ubuntu and flavour are you using? No issue with having them both on same drive.

PS: Click on 'Home' in the left column of the file manager you show. Is it exactly the same?

---

### Post by mcduck on 2014-11-03
Ubuntu doesn't think those partitions (or devices) are "for it". It simply shows them there as it has detected you have those partitions, and it's able to mount & read them if you want to access them. Same thing as when you plug in USB drive or insert a CD, it'll appear under "Devices" so you can access it but that doesn't mean Ubuntu would think it "owns" that device.

Anyway, if you want to hide them, the best way is to actually go and configure them in /etc/fstab, like you'd do for any drive you want mounted automatically on boot, but adding the "noauto" option to stop them from mounting automatically. Once the drives are configured in fstab, the automatic mounting on desktop will ignore them, so they'll only appear under "Devices" in your file manager if you go and mount them manually.

---

### Post by oldfred on 2014-11-03
Some examples of hiding mount:
 # Hide mount examples with noauto,  you have to make the mount points yourself first
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all, UUID is better than this example with device mount
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
#hide windows 7 second hard drive
sudo mkdir /mnt/reserved
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
sudo mkdir /mnt/win7
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

      
 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

### Post by AzuObs on 2014-11-03
Thank you all for your input!

---

