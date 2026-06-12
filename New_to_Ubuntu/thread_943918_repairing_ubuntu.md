---
title: "repairing ubuntu"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Navane on 2008-10-10
Hi,

so on the way of trying to fix some errors, i decided to uninstall libstdc++6. It said are you sure? And I said yes. Bad move.

Is there any way I can reinstall ubuntu while keeping my personal files? (documents, music etc.)

---

### Post by phidia on 2008-10-10
I think the safest advice is to back everything up-if you are going to reinstall.
And maybe consider having a seperate home partition on a new install.

But if you can boot into your system at all (recovery mode)
Try > sudo apt-get update && sudo apt-get upgrade
That might get you running again.

---

### Post by Absorbed on 2008-10-10
> **Navane said:**
> Hi,

so on the way of trying to fix some errors, i decided to uninstall libstdc++6. It said are you sure? And I said yes. Bad move.

Is there any way I can reinstall ubuntu while keeping my personal files? (documents, music etc.)

You could use an Ubuntu livecd to backup your files to a USB pen drive or burn to cd/dvd, and then reform, if you don't manage to solve this some other way.

---

### Post by jemate18 on 2008-10-10
after back up...


It is recommended to separate your /home partition so that when similar things happen, you can reinstall and select not to format your HOME directory.......

---

### Post by bodhi.zazen on 2008-10-10
You can boot the desktop CD and restore your system from there.

lets assueme Ubuntu is installed on /dev/sda1

Then , from a live CD :

```
# Become root
sudo -i

# Mount your ubuntu partition
mount /dev/sda1 /mnt

# Chroot
chroot /mnt

# Install libstdc++6
apt-get install libstdc++6

# Exit
exit
```

Change "/dev/sda1" to your ubuntu root partition.

Reboot and all should be well :twisted:

---

### Post by Nxion on 2008-10-10
> **bodhi.zazen said:**
> You can boot the desktop CD and restore your system from there.

lets assueme Ubuntu is installed on /dev/sda1

Then , from a live CD :

```
# Become root
sudo -i

# Mount your ubuntu partition
mount /dev/sda1 /mnt

# Chroot
chroot /mnt

# Install libstdc++6
apt-get install libstdc++6

# Exit
exit
```Change "/dev/sda1" to your ubuntu root partition.

Reboot and all should be well :twisted:

/me stalks bodhi.zazen .... again :twisted:

---

### Post by bodhi.zazen on 2008-10-10
> **Nxion said:**
> /me stalks bodhi.zazen .... again :twisted:

LOL, Hi Nxion, good to see you ;)

---

