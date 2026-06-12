---
title: "How do I uninstall Windows XP"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by soupowl on 2008-11-14
I'm sorry if the answer to this is somewhere obvious.  I have installed Ubuntu in addition to windows, and I love it.  What do I now do if I want to have it as my only OS?  I have Windows XP on the computer as well at the moment.  I installed from a CD which I burnt myself, and I still have.  Should I put it in again, or is there an easier way.
Many thanks, I have found the information on this site to be amazingly helpful and polite.

---

### Post by Titan8990 on 2008-11-14
Get gparted:

sudo apt-get install gparted


Use gparted to reformat your Windows partition (all data will be lost). Then there will be no more Windows.

---

### Post by taurus on 2008-11-14
You have a few options here.  You can use gparted from Ubuntu (install it with synaptic if you don't have it) and format your windows partition to ext3 filesystem and use that space as a backup or storage.  Or you can expand your current / filesystem to take up that empty space.  However, it depends on your layout of your harddrive and you must do that with the gparted from the LiveCD since you cannot shrink or expand a partition while it is being used.

---

### Post by flaggh on 2008-11-14
Open your partition editor.  Select the windows partition.  Press delete.

---

### Post by EvilRobotDrew on 2008-11-14
Before you remove windows, we need to remove the option to boot into windows on startup, in terminal type:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.cya
[this makes a "Cover Your @&^" copy of your GRUB menu]

sudo gedit /boot/grub/menu.lst
[this opens your menu.lst in gedit so we can modify it]

scroll down to "## ## End Default Options ##"

locate your windows option, and before each line insert a "#" this "comments" out the line, and removes it as an option

I don't have windows, but as an example: 

title        Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=2b3789de-6121-42c3-9df8-2fe0eec75a10 ro  single
initrd        /boot/initrd.img-2.6.24-16-generic

becomes:

#title        Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
#root        (hd0,0)
#kernel        /boot/vmlinuz-2.6.24-16-generic #root=UUID=2b3789de-6121-42c3-9df8-2fe0eec75a10 ro  single
#initrd        /boot/initrd.img-2.6.24-16-generic

save the changes! reboot if you want to make sure that this worked.

Now to actually remove windows, and expand your ubuntu partition onto this new space you will have to do the following:

1. insert the LiveCD into your CD tray

2. Reboot the Computer

3. select boot from CD if given the option

4. select "try Ubuntu" (i can't remember the exact wordage)

5. select System -> Administration -> Partition Editor

6. select the Windows Partition on your computer (it should be NTFS, i would go through Places -> Computer to ensure that you don't wipe out Ubuntu instead)

7. Make sure the Windows Partition is unmounted (just right click)

8. right click the Windows Partition and select "Delete"

9. what was you windows partition should now be labeled "Unallocated Space"

10. select you Ubuntu Partition (NOT the one labeled as swap) it should be formatted as ext3

11. right click, select "Resize/Move" and expand the partition as much as you can (you can also drag the partition to take up the now Unallocated space)
[COLOR=Red]
UP TO NOW, NO PERMANENT CHANGES HAVE BEEN MADE, BE SURE THAT YOU HAVE A BACKUP OF EVERYTHING FOR BOTH WINDOWS AND UBUNTU, IF SOMETHING GOES HORRIBLY WRONG YOU DON'T WANT TO HAVE TO WORRY ABOUT FAMILY PICTURES OR SCHOOLWORK! IF THIS BREAKS YOUR COMPUTER YOU WANT TO BE ABLE TO SIMPLY WIPE THE HARDDRIVE AND RE-INSTALL UBUNTU WITHOUT LOSING DATA[/COLOR]

12. select Apply and wait, this step will probably take a while (by a while i mean, go smoke a cigarette, grab a cup of coffee and don't freak out if you harddrive is still whirring after 20 mins)

13. when Gparted (the Partition Editor) is done, reboot the computer, remove the CD and you should be done!


if, after you are done with everything else (i.e. windows is gone and Grub doesn't mention it) you want to autohide the grub menu, so it automatically boots into Ubuntu unless you press [ESC] then find the

## hiddenmenu

line in menu.lst, and make sure it looks like this:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

---

### Post by Keen101 on 2008-11-14
There are a couple of ways.

[B]The easiest would be to just reinstall ubuntu from your cd, and select "use entire disk" option.
[/B]

but you could delete the win partition, and expand your linux one to take it's space, then edit GRUB so you don't have windows in boot menu.

---

### Post by EvilRobotDrew on 2008-11-17
Did our suggestions work?

---

