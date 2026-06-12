---
title: "Mount NTFS partition on login (fuseblk?)"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by kelpdip on 2008-04-30
Finally got back to linux with 8.04. It is nice but a few things are different.

I was about to edit fstab to mount as ntfs, but what is type "fuseblk"?

My ntfs partition shows up in gnome filesystem properties and system monitor as type fuseblk. Is this a new gnome thing?

I don't really need it mounted prior to gnome/x login, and it auto mounts when I navigate to it, but i would prefer for it to mount as soon as i login.

Also, a second question: Does anyone know how to enable all the status messages during system shutdown/reboot?

---

### Post by hermes0710 on 2008-04-30
> **kelpdip said:**
> Finally got back to linux with 8.04. It is nice but a few things are different.

I was about to edit fstab to mount as ntfs, but what is type "fuseblk"?

My ntfs partition shows up in gnome filesystem properties and system monitor as type fuseblk. Is this a new gnome thing?

I don't really need it mounted prior to gnome/x login, and it auto mounts when I navigate to it, but i would prefer for it to mount as soon as i login.

I don't know what fuseblk thing is but my ntfs partitions are declared as ntfs in fstab. Since you want the partitions to be mounted after you login in GUI you should remove the line from the fstab file, create a custom script for mounting the device and added to your session startup (System>Preferences>Sessions)

---

### Post by frogitts on 2008-05-01
Here's an easier way to auto-mount that I just found: install "Storage Device Manager" from the add/remove programs dialog, or terminal, or synaptic, or whatever other method you want. It's a gui frontend for mounting all sorts of drives. You need to know what the id of the drive you're looking for is, and it sounds like you already know that, but for posterity's sake, I'll say that you can use "sudo fdisk -l" or the gParted partition editor to figure that out. In the Storage Device Manager, which is pretty self-explanatory, you select the drive you need from the left-hand pane, type the name of the drive in, and click 'mount'. To make it mount at startup, click the Assistant, and make sure the "This filesystem is mounted at boot time" option. Hope this works for you like it did for me!!

As for the whole fuseblk thing, both of my NTFS drives (Windows partition and an external USB) show up as fuseblk in the system monitor, and this still works for me. I'm no techie, but it looks like the fuseblk designation is a reference to a type of interface (FUSE) that ntfs-3g and other programs use to interact with (maybe only?) NTFS filesystems. Someone who knows about this could clear that up.

---

### Post by frogitts on 2008-05-01
Oh, and it may also be important to have the NTFS Configuration tool installed (ntfs-config) and to have write support enabled for both internal and external devices.

---

### Post by harshpshah on 2008-07-02
My NTFS partitions also show up as fuseblk, and read-write from ubuntu works perfectly fine. But I can't change the folder permissions on this partition.

I wanted to create a shared folder that I can access from my other computer that runs windows. But it couldn't set up a folder on ntfs partition as a shared folder saying ubuntu can't change it's permissions. Sure enough, when I right click on the folder properties and check the permissions tab, everything is disabled, I can't modify anything. 

Note that this NTFS partion is not the active windows XP partition, it's just a left over data partition from my windows days. I don't think I ever set any user restrictions on this partition under windows.

---

### Post by stchman on 2008-07-02
> **kelpdip said:**
> Finally got back to linux with 8.04. It is nice but a few things are different.

I was about to edit fstab to mount as ntfs, but what is type "fuseblk"?

My ntfs partition shows up in gnome filesystem properties and system monitor as type fuseblk. Is this a new gnome thing?

I don't really need it mounted prior to gnome/x login, and it auto mounts when I navigate to it, but i would prefer for it to mount as soon as i login.

Also, a second question: Does anyone know how to enable all the status messages during system shutdown/reboot?

It is pretty easy to add an NTFS partition to your fstab.

Create a mount point.
```
sudo mkdir /media/ntfs_disk
```

```
/dev/<partition> /media/ntfs_disk ntfs-3g defaults 0 0
```

If you want read only then substitute ro,defaults for defaults.

When done type this in a terminal:

```
sudo mount -a
```

You will get an icon to appear on your desktop.

If you want to do it the REALLY easy way install ntfs-config.

```
sudo apt-get install ntfs-config
```

This give you a GUI that modifies your fstab file.

---

### Post by andrewdied on 2009-12-06
> **frogitts said:**
> Here's an easier way to auto-mount that I just found: install "Storage Device Manager" from the add/remove programs dialog, or terminal, or synaptic, or whatever other method you want. 

This looks like a better program than comes installed by default.  The real program behind it is PySDM for those who install through the Synaptic Package manager.

---

### Post by pararoly on 2010-09-09
[http://www.mjmwired.net/kernel/Documentation/filesystems/fuse.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/fuse.txt)

I found a bit of info on fuseblk that may prove useful.

Best wishes
roly :-)

---

