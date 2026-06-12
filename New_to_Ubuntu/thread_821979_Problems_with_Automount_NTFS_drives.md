---
title: "Problems with Automount NTFS drives"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by dashmesh on 2008-06-07
Hi,

I am not sure of the mechanism for auto-mounting NTFS volumes in Hardy but I need your help to resolve an issue I am facing.

The default behavior of ubuntu install was that it recognized my windows partition on installation. This volume automatically appears in the file-browser as a link in the sidebar. On clicking this link, the volume is automounted. 

I tried to change the parameters for the automount to point to a specific directory within the install by right clicking on the link and choosing properties for the link that appears on the desktop once the volume is successfully automounted. 

problem: I cannot automount when I click on this link. I get the following error message.
 "Cannot mount the volume"
mount point cannot contain the following characters newline, G_DIR_SEPARATOR (usually /)


Can somebody point me to the configuration file that needs to be fixed in order to get this issue resolved.

Thanks in advance

---

### Post by jbrown96 on 2008-06-07
you need to edit /etc/fstab
Since it is automounting already, there is probably already an entry for it. Make sure you back this up ```
sudo cp /etc/fstab /etc/fstab.back
```
Create the directory in which you want to mount it ```
sudo mkdir /location/of/new/folder
``` Then edit your fstab ```
sudo gedit /etc/fstab
```
Here is an entry from mine (sorry I don't have any ntfs) that automounts
> # /dev/sda2
UUID=b0a84c25-11e7-431a-81cb-16026f43d230 /media/multimedia xfs     relatime        0       2

The /media/multimedia is where it currently mounts, so you would simply change that part

---

### Post by mikewhatever on 2008-06-07
Here is a good guide [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by dashmesh on 2008-06-11
Hi, 

Thanks for the help. Your method would mount the ntfs volumes on bootup. I have a slightly different problem here and it would be kind of you to lend me your expertize to fix it.

In nautilus as well as on main panel on the desktop,there is a group of shortcuts called "Places".  This menu lists a number of shortcuts and among them are the shortcuts or mounting the drives using gnome-mount.

I need to get one of these shortcuts fixed to mount my ntfs partition corectly. It used to get mounted before I altered the settings for it by right clicking on the icon that appears on the desktop once the volume is mounted and selecting properties>volume>settings.

Thanks

---

