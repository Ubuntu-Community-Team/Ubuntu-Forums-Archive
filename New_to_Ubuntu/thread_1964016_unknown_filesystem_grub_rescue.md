---
title: "unknown filesystem grub rescue"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by franmf on 2012-04-23
Hi. I have a problem with my grub loading. I had w7 and ubuntu 11.10 installed in my pc, one in each own partition.
I had a swap partition of 2gb space. When I used to try to.hibernate ubuntu an error messagge came up about "no enought swap space". Then I delete the 2 gb swap partition and created a new one of 4.(I'm sure I only modified that partition). After that, when powering on my pc, after bios loaded, an error says "error: unkown filesystem. Grub rescue>".
What can i do? I cant boot neither.windows or ubuntu. Thank you

---

### Post by LU][or on 2012-04-23
Hi there, are you sure you deleted your swap partition? What you describe usually happens if some deletes his /boot partition... If that isn't your case, try to boot from a live cd...

```

sudo su
mount /dev/sda1 /mnt        #make sure to replace sda1 with your part mounted as /
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt
update-grub

```let me know if it worked...

---

### Post by anewguy on 2012-04-23
Did you have any free space on the disk when you decided to expand the swap partition?

---

### Post by gustavod on 2013-02-01
Hi,

I deleted windows partition and resize Ubuntu partition with GParted from Ubuntu liveCD.

Now I have:
"error: unknown filesystem.
grub rescue>"

I tried the code above with a live-cd, plus one line:

sudo su 
mount /dev/sda5 /mnt        
mount -o bind /proc /mnt/proc 
mount -o bind /dev /mnt/dev 
mount -o bind /sys /mnt/sys
chroot /mnt update-grub

Then rebooted and get exactly the same error. Any help?

---

### Post by srekcahrai on 2013-02-01
At the Grub Rescue command  prompt, type "ls" and press "Enter." This will display all partitions on  your PC. Identify the "boot" partition and note the name: for example,  "(hd0,1)."

Type "set prefix=(hdX,Y)/boot/grub," where "(hdX,Y)" is the name of the boot partition you identified in Step 1. Press "Enter."

Type "set root=(hdX,Y)," where "(hdX,Y)" is the name of the boot partition you identified in Step 1, and press "Enter."

Enter "insmod normal," followed by "normal." Grub Rescue will load the main GRUB menu.

---

### Post by gustavod on 2013-02-04
Solved!

At grub rescue prompt:

set prefix=(hd0,msdos5)/boot/grub
insmod normal
normal

(System booted)

At terminal:

sudo grub-install --root-directory=/ /dev/sda

---

### Post by sricharanch on 2013-02-16
Hi!
I am using Ubuntu 12.04 as a dual boot along with windows7 with Ubuntu on a separate partition. I have tried increasing swap size using Gparted in live cd mode using the Ubuntu 10.04 disc. In the process I have come across resizing Ubuntu partition and deleting the swap file and creating a new one. After that I was left out with a problem of unknown file system Grub rescue problem at boot and I was unable to boot my system into either OS.  Also I tried some thing looking into the forums and I can make it to a lime editing mode. But when I tried command boot there, I got a problem called kernel not loaded. Can any one please help me with this issue?

---

