---
title: "Install Question - Two Internal Hard Drives"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by Sidney232 on 2011-09-27
So I want to do a fresh clean install of 11.04. I have two internal hdd. Can I set things up on install to use one hdd for / and the other for /home and will that set up the fstab properly for me?
Also when it's all installed with an empty /home on the 2nd hdd can I just copy (i.e. overwrite) a previously backed-up /home from an external hdd onto the newly created /home and expect things to work OK?
Perhaps I didn't explain that too well...
Any help greatly appreciated.

---

### Post by TeoBigusGeekus on 2011-09-27
During installation, check manual partitioning (or whatever is called nowadays).
Select your first disk and give as its mount / (root).
Select the second one and give /home as its mount point.

As for your second question: you could try it, but first make a backup of your new home folders.

---

### Post by cgroza on 2011-09-27
The Ubuntu installer will take care of creating an appropriate fstab once you give it the correct data.
The other thing is that you may need to set up the bios to boot from the HDD you installed the Grub on.

And yes, you can just copy stuff over but you have to be careful about the config files, you can't afford to lose them.

---

### Post by Paqman on 2011-09-27
> **Sidney232 said:**
> Can I set things up on install to use one hdd for / and the other for /home and will that set up the fstab properly for me?


You can, but doing so will likely waste a lot of space. The root filesystem (/) only needs about 10GB. If you do anything that makes really big temp files you might need 20GB max. If that drive is any decent size it's likely to be mostly fresh air.

I'd put / and /home on the same drive and use the other one for data personally. Or use it to back up the data in /home.

> 
Also when it's all installed with an empty /home on the 2nd hdd can I just copy (i.e. overwrite) a previously backed-up /home from an external hdd onto the newly created /home and expect things to work OK?


You can, the only problem you might strike is permissions. If the files were owned by someone with a different UID from your current one then you might get problems. You could sor that out with:
```
sudo chown -R username:username ~ 
```
Which would force ownership of all files in your home folder back to your user.

---

