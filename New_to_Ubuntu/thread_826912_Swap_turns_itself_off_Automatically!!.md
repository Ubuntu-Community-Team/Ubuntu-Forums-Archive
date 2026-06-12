---
title: "Swap turns itself off Automatically!!"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Jackfrost123 on 2008-06-12
Whenever I shut down my laptop swap turns itself off. When i restart is swap is alternatively either off, or when I run gparted the space used for swap (on the same physical disk as data but own partition of course) is not even recognized (more seldomly). I have to manually set it again via gparted as swapon. Of course being a newbie I wasn't aware of that and would get my pc into infinite loops hitting the memory overload...d:guitar:

---

### Post by ukripper on 2008-06-12
> **Jackfrost123 said:**
> Whenever I shut down my laptop swap turns itself off. When i restart is swap is alternatively either off, or when I run gparted the space used for swap (on the same physical disk as data but own partition of course) is not even recognized (more seldomly). I have to manually set it again via gparted as swapon. Of course being a newbie I wasn't aware of that and would get my pc into infinite loops hitting the memory overload...d:guitar:

I am not sure what is causing your swap to turn off. you can check /var/log/messages.

First test if this command ```
sudo swapon -a
``` turn the swap on manually then

Easy way to turn on  swap everytime after boot you can add > /sbin/swapon -a  to /etc/rc.local just before exit 0

---

### Post by rogier.de.groot on 2008-06-12
Is your swap partition listed (and not commented out) in /etc/fstab?
Is it using a UUID to find your swap partition?

---

### Post by tyler_roach on 2008-06-12
Look at your /etc/fstab file. It should have something like this:

# /dev/sda3
UUID=e02a6e92-ba89-4354-a261-053651348672 none            swap    sw  

Backup your fstab file ( sudo cp /etc/fstab /etc/fstab.bak ),

and change the UUID part to the device name. For example, I would delete the whole UUID=e02a6e92-ba89-4354-a261-053651348672 thing, and put /dev/sda3 in its stead. Reboot, run top, and see if your swap is activated.

Sometimes when you fiddle around with gparted, it changes the UUID of your partitions and they're not mounted correctly.

---

### Post by Jackfrost123 on 2008-06-12
Thanks guys for the great and quick responses. Is this an issue you have come across before? Is it common?

"Sometimes when you fiddle around with gparted, it changes the UUID of your partitions and they're not mounted correctly."

I suppose this is what happened because I swaped off with gparted a few weeks ago to sort out issues with my partitions. 

I am looking into your replies and putting them to good use and I ll get back to you.

Again thanks a bundle.

---

