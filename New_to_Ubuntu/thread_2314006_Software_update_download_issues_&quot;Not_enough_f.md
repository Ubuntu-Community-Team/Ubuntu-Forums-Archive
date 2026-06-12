---
title: "Software update download issues &quot;Not enough free disk space on 14.04"
date: 2016-02-17
forum: New to Ubuntu
---

### Post by godlywil on 2016-02-17
I have 250g . When trying to install system/software updates, I receive the following message

The upgrade needs a total of 82.5 M free space on disk '/boot'. Please free at least an additional 20.3 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.   Also saw this info about my HD,  Disk is OK, 8 bad sectors (46° C / 115° F).  How do I put additional space wherever it is downloading the updates and how to I repair the 8 bad sectors.

---

### Post by oldos2er on 2016-02-17
See Alaa Ali's post [here]("http://askubuntu.com/questions/298487/not-enough-free-disk-space-when-upgrading") on how to remove old kernels and free disk space in /boot.

Bad sectors are hardware faults and cannot be repaired. Modern hard drives will automatically mark bad sectors as unusable, up to a point, but it's something to keep an eye on. Backups are your friend.

---

### Post by grahammechanical on 2016-02-17
Have you tried running?

```
sudo apt-get clean
```

Also please run

```
sudo apt-get update
sudo apt-get upgrade
```

You will be asked to give a yes or no after apt-get upgrade. Answer no.

> Do you want to continue? [Y/n] 

What we are looking for is any information that lists packages that are no longer needed. In that list might just be some old kernels. There will be a suggestion that you remove them with 

```
sudo apt autoremove
```

Here is an example from my machine
> 
The following packages were automatically installed and are no longer required:
  gir1.2-javascriptcoregtk-3.0 gir1.2-webkit-3.0 libgee2 libllvm3.6v5
  libqt5xcbqpa5 linux-headers-4.3.0-6 linux-headers-4.3.0-6-generic
  linux-headers-4.4.0-2 linux-headers-4.4.0-2-generic linux-headers-4.4.0-3
  linux-headers-4.4.0-3-generic linux-image-4.3.0-6-generic
  linux-image-4.4.0-2-generic linux-image-4.4.0-3-generic
  linux-image-extra-4.3.0-6-generic linux-image-extra-4.4.0-2-generic
  linux-image-extra-4.4.0-3-generic
Use 'sudo apt autoremove' to remove them.

Notice the references to linux-headers & linux-image. There are 3 kernels that I can safely remove using 'sudo apt autoremove'.

Regards.

---

