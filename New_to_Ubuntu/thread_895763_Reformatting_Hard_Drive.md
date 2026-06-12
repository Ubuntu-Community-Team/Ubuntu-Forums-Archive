---
title: "Reformatting Hard Drive"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Generic Bond on 2008-08-20
I recently got Ubuntu and I absolutely love it. 

Is there any step by step guide to reformat my hard drive so I can completely get rid of Windows forever? I haven't used Linux since I was 13, so it's been a while.

---

### Post by SuperSonic4 on 2008-08-20
When installing from the live CD just select

"Guided, use the entire hard drive"

---

### Post by sandysandy on 2008-08-20
just overwrite windows with ubuntu during installation.

or with gparted delete windows partition and reformat as ext3 for ubuntu.

regards

---

### Post by alecz20 on 2008-08-20
If you don't want to re-install you can boot from live CD and try with qtparted to merge the partitions, or format the windows one and transfer the space from it to the Linux one.

---

### Post by pi.boy.travis on 2008-08-20
Install GParted via synaptic.  GParted is a partition manager.  From there you can remove your Windows partition and grow the Ubuntu partition to fill the space.  To remove Windows from the GRUB menu (the menu you see when you first boot up, open a terminal and type:

```
sudo gedit /boot/grub/menu.lst
```

You can remove the Windows entry this way, or install QGRUBEditor via synaptic if you prefer to work with a GUI.

Hope this helps!!

EDIT:  Sorry, you will need to use the liveCD to edit you partitions, because you can't work with active system partitions.  GParted is still good to have though. . .

---

### Post by M4rotku on 2008-08-20
Or, if ubuntu is already installed.  Use the partition editor on the live cd.  System -> Administration -> Partition Editor.  Using this, you will be able to delete the windows partition and resize you linux partition with the extra space.

However, you should always back up your system before doing so.

Look [here]("http://ubuntuforums.org/showthread.php?t=35087") for a good guide to backing up your system.

---

### Post by Generic Bond on 2008-08-20
Well, the thing is...I want to completely get rid of Windows and reinstall Ubuntu. I don't have a physical copy of Ubuntu.
I basically want to start from scratch.

---

### Post by pi.boy.travis on 2008-08-20
-Backup important files
-I usually make a list of all the packages I have installed since my last clean install, that way I don't for get any
-Pop in an Ubuntu live CD
-You can select install Ubuntu from the menu if you won't need the liveCD desktop
-Proceed to the partitioning portion
-If you ready, select: Guided, use entire disk

Hope this helps!

---

### Post by alecz20 on 2008-08-20
> **Generic Bond said:**
> Well, the thing is...I want to completely get rid of Windows and reinstall Ubuntu. I don't have a physical copy of Ubuntu.
I basically want to start from scratch.

That's EASY!

Do as pi said. (you may skip step 2 to keep it simple)

---

### Post by 4Orbs on 2008-08-20
> I don't have a physical copy of Ubuntu.

Download the Ubuntu iso from Ubuntu's home page or better yet torrents (faster dwnld). Burn to cd iso and then you'll have a live cd with all you will need included. It guides you through the entire process, very friendly.

You'll probably need to set BIOS first, so that your comp will boot from cd as first option. There are lots of good tutorials on installing Ubuntu.

---

### Post by Generic Bond on 2008-08-20
I'm doing that as we speak. Thank you guys! I greatly appreciate it!

---

### Post by pi.boy.travis on 2008-08-20
Welcome to Ubuntu and Linux!

---

