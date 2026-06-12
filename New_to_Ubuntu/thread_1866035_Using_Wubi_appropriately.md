---
title: "Using Wubi appropriately"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by djk21108 on 2011-10-20
Hello everyone,

I'm looking for the most efficient way to dual boot Ubuntu on my new laptop.

Is using wubi just as effective as using a live cd? Is there any chance of corruption or trouble with using wubi?

What kind of partition setup should I go with if I decide to use it?

---

### Post by Foxheadz on 2011-10-20
Not sure about corruption or effectiveness, but from what I know if your planning on installing it on the same harddrive as windows your gonna have to partition it which tends to mean loss of data... But if thats not a problem then all you really need is a ext4 partition for everything ubuntu and maybe a small (2gb) swap partition.

Edit: My bad that has to do with normal Ubuntu not Wubi

---

### Post by wolfen69 on 2011-10-20
> **Foxheadz said:**
> I know if your planning on installing it on the same harddrive as windows your gonna have to partition it

You don't need to partition if using wubi. It does it automatically. Basically, you are installing ubuntu inside of windows. Wubi is OK to check out ubuntu, but I suggest doing a real dual boot if you like it. 

During ubuntu (dual boot) setup, you will be given the choice of how you want it installed. Just select "install along side windows" (or something similar) and use the slider bar to allocate how much disk space you want for it. Just make sure to defragment windows first before installing.

---

### Post by waynefoutz on 2011-10-20
I wouldn't use Wubi as a permanent install, and I certainly wouldn't save any critical data inside a Wubi install. What Wubi does is create a big file in your Windows partition, and Ubuntu is fooled into thinking that file is a physical drive. If and when that file gets damaged, your Ubuntu install is probably gone. 

Wubi is great for trying Ubuntu out, because it's totally safe to your Windows installation, it's easily removed in Windows add/remove software application in the control panel, and you don't have to make the commitment of partitioning your drive. It's a damn good way to get your feet wet, but I wouldn't use it forever.

---

### Post by nerdy_kid on 2011-10-20
> **djk21108 said:**
> Hello everyone,

I'm looking for the most efficient way to dual boot Ubuntu on my new laptop.

Is using wubi just as effective as using a live cd? Is there any chance of corruption or trouble with using wubi?

What kind of partition setup should I go with if I decide to use it?

Wubi installs Ubuntu inside Windows.  You don't have to partition anything, which is quite nice.  However, Ubuntu will be installed on NTFS (Windows' file system) which is slower then ext4 (Ubuntu's default file system), and thus will run slightly slower for disk intensive tasks.  Also, when I last tried wubi out, Ubuntu's NTFS drivers used a bit of CPU, slowing the system down more.  Perhaps that has been fixed recently.

For chances of corruption, do you mean corruption of your Windows filesystem or of Ubuntu?

If I remember right, A wubi installation of Ubuntu is trapped inside itself, meaning it can't access your Windows files at all.  I could be wrong, as it has been a while since I played with wubi; someone correct me if I'm wrong on that.

A wubi installed Ubuntu is theoretically at risk from Windows viruses, because it is a file in the Windows' file system.  I virus could theoretically destroy it.  That probably won't happen though.

In short, wubi is a good method to give Ubuntu a much more thorough trial then with a LiveCD.  Just defragment your Windows drive, and then install it.  If you want Ubuntu's top performance and security, then do a true dual boot; Ubuntu's installer is very easy anyway.

---

### Post by waynefoutz on 2011-10-20
> **nerdy_kid said:**
> 

A wubi installed Ubuntu is theoretically at risk from Windows viruses, because it is a file in the Windows' file system.  I virus could theoretically destroy it.  That probably won't happen though.



A hard shutdown will destroy a Wubi install faster than a virus. I've had that happen before. It doesn't take much to corrupt a file that size.

---

### Post by lovinglinux on 2011-10-20
> **nerdy_kid said:**
> If I remember right, A wubi installation of Ubuntu is trapped inside itself, meaning it can't access your Windows files at all.  I could be wrong, as it has been a while since I played with wubi; someone correct me if I'm wrong on that.

You can access your Windows files through the /host directory. Works like a charm.

---

### Post by Mark Phelps on 2011-10-21
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

