---
title: "swap partition and other problems"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by dnns123 on 2008-06-15
I used the live CD
I discovered that I had 2 swap partitions in my HD and I tried to delete one and added the empty space to the Ubuntu partition. Everything went well until I logged back into the install Ubuntu.

Problem number 1. The boot splash is missing. All I see now is the text version of booting.

Problem number 2. The swap partition is not automatically mounted. I mount it by using Gparted and choosing the option, swap on.
How do I solve these?:(

---

### Post by forestpixie on 2008-06-15
Make sure that swap is in your fstab

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by prshah on 2008-06-15
> **dnns123 said:**
> 
Problem number 1. The boot splash is missing. All I see now is the text version of booting.

Problem number 2. The swap partition is not automatically mounted. 

give the command```
sudo fdisk -l
``` and locate the device related to your swap partition (will be something like /dev/sda5, etc).

Now give the command ```
sudo vol_id /dev/sdX9
``` where sdX9 is to be replaced by your swap partition device. From the output shown, locate your swap partitions UUID. (Something like this:)```
ID_FS_UUID=[color=red]75c121b0-faf2-42a6-931d-a94634ddb87b[/color]
``` The part in red is your UUID.

Now give the commands ```
cp /etc/fstab ~
sudo gedit /etc/fstab
``` and remove any lines _related to swap_, then add the lines as below to the end of the file:
```

# /dev/sdx9
UUID=[color=red]75c121b0-faf2-42a6-931d-a94634ddb87b[/color] none            swap    sw              0       0

```

(Replace the part in red with the UUID you got before)

These basic steps are so that the system recognizes the correct swap partition on the next boot. Now, you need to activate the swap partition with the command```
sudo swapon -a
```, if it comes back with an error, restart the system before trying again.

After this your boot splash problems should also be automatically cleared up. 

To check if your swap is active, give the command```
swapon -s
``` and it should show your swap partition (/dev/sdx9)

Note that in some cases you may also need to regenerate the initramfs (not to be done if everything is fine after a restart)```

sudo update-initramfs -u
```

Also, once everything is working fine, check if hibernate (if you ever used that feature) is working. If it is not, post back here for more steps.

---

### Post by dnns123 on 2008-06-15
Thanks a lot! That fixed the swap problem and I learned something new! :P
Now my only prob is the bootsplash. It shows only the part where the leading bar moves left and right. After that, it turns to text starting with "Reading files needed to boot...             [OK]"

---

### Post by prshah on 2008-06-15
> **dnns123 said:**
> 
Now my only prob is the bootsplash. It shows only the part where the leading bar moves left and right. After that, it turns to text starting with "Reading files needed to boot...             [OK]"

Check your "/boot/grub/menu.lst" file. Find the entry that you select when booting. Make sure that at the end of the "kernel" line you have the entries "quiet splash" Eg:> 
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4bce0fa6-bf3b-43dc-bd3c-9aac9b0d4eed ro [color=red]quiet splash[/color]
initrd		/boot/initrd.img-2.6.24-18-generic


(Be careful here. There are a number of lines, and you don't want to disturb the lines that have "ro single" on them. And don't copy and paste this line.)

If it's not there, then add it. (sudo gedit)

Then run this command```
sudo update-grub
``` You should do this irrelevant of whether the words were already there or added by you now.

On the next reboot your splash screen should be normal.

If it still isn't maybe you need to run the initramfs command as mentioned previously. I'd avoid it though; in any case I prefer the detailed look at the innards of linux when starting up.

---

### Post by dnns123 on 2008-06-15
I tried them all, the boot splash still won't show.
Any other ideas? :confused:
I'll continue tomorrow...

---

