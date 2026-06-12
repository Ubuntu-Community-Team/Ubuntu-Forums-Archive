---
title: "mount external HDD in Fluxbuntu"
date: 2008-01-05
forum: Other OS Talk
---

### Post by fast eddie on 2008-01-05
OK, can someone please let me know how I mount an external HDD in Fluxbuntu so that when I switch my laptop and HDD on it will find it automatically. I would like to try to see if I can use it to run Slimserver and use the HDD to store my music on.

I am new to Linux so will probably need pointing in the direction of an idiots guide.

---

### Post by K.Mandla on 2008-01-06
Off the top of my head, you should be able to do that rather easily without too much of a guide.

Plug in your external drive after you start up a computer, and then see what the results of this command are:

```
sudo fdisk -l
```
Try to find your external drive in there; you should be able to find it by its size. Then make a note of the drive assignment -- something like /dev/sda1.

Now edit the /etc/fstab file with this command.

```
sudo nano -w /etc/fstab
```
At the bottom, add this line.

```
/dev/sda1 /media/external vfat defaults,users,auto 0 0
```
Save that file with CTRL+O (that's an O, not a zero), and CTRL+X to exit.

Two more steps and you're done: Make the directory where the drive should be mounted.

```
sudo mkdir /media/external
```
And finally, create a graceful way to access that folder from your home directory.

```
ln -s /media/external ~/external
```
Reboot and see what happens.

If I'm right (and sometimes I actually am ;) ), this should mount the external any time you turn on the computer. If it's not available you'll probably see an error message spit out, but it shouldn't be a showstopper.

I might have made a mistake in there, since I haven't actually tried this. And there might be a better way to do it, so someone speak up if you can help ... :???:

---

### Post by Sonsum on 2009-01-25
Thanks for the guide, it worked great for me (once I realized my drive was sdb1, not sdb.)

A huge flaw in the current fluxbuntu release is the lack of a drive mounting tool.

---

### Post by snowpine on 2009-01-26
Fluxbuntu does include a drive mounter called ivman, but there is a well-known bug that keeps it from working properly. Here's the fix:

```
mkdir ~/.ivman
```

---

### Post by jack2k9 on 2009-01-28
Thanks for the fix

---

### Post by Neural oD on 2009-01-28
Thanks for that - will need to check ivman out - but then again cli is always the best :)

---

