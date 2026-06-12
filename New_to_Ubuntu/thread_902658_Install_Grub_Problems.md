---
title: "Install Grub Problems"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Foxfire on 2008-08-27
Installed Kubuntu on second hard drive but when the grub list comes up all it has is my Ubuntu and My vista on hard drive 1  

how can I get Kubuntu on here?

---

### Post by swegner on 2008-08-27
The entries for the GRUB menu come from the configuration file /boot/grub/menu.lst .  To get boot options for Kubuntu, you will need to add entries for it into this list.

**Backup this file before you make any changes!**
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Then, you can open the file to edit.  You'll need root access.
```
sudo gedit /boot/grub/menu.lst
```

The file has many examples of the syntax towards the top, and then you will find many of the menu entries, which look something like:
```
title        Ubuntu 8.04.1, kernel 2.6.24-20-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-20-generic root=UUID=33e7410f-e547-4073-9b6a-032e424a7a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-20-generic

```

You will need to add a new entry such as this one for your Kubuntu install.  The title can be anything descriptive, and the second line must have the address of your harddrive partition.  You may find a /boot/grub/menu.lst file on your Kubuntu partition, from which you can copy the first entry.

When you reboot, you should see the new entry in your GRUB menu.  If something went wrong, you may use the recovery boot (or boot from a live CD), and restore the original version of the menu.lst file from backup.

---

