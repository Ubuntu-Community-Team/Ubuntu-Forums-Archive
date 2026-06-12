---
title: "New Idea o Nueva Idea"
date: 2024-04-14
forum: New to Ubuntu
---

### Post by isaacsantaella on 2024-04-14
Sería fantástico que incorporarán si un usuario va a formatear la PC y este haya eliminado todas las particiones, tener un botón que genere las particiones principales para formatear la PC y que no deje dar siguiente si no tiene particiones ya que se puede avanzar y eliminar todo y esto genera un bug el cual si avanzas eliminaste todo el disco duro.

---

### Post by MAFoElffen on 2024-04-15
Welcome to Ubuntu Forums.

Since this is an English speaking Forum, I took the liberty of translating the first post... (Please post in English so that Members can answer you.)
> **isaacsantaella said:**
> It would be fantastic if they incorporated, if a user is going to format the PC and he or she has deleted all the partitions, to have a button that generates the main partitions to format the PC and that does not allow you to click next if it does not have partitions since you can go ahead and delete everything and this generates a bug which if you continue you deleted the entire hard drive.

Are you talking about the "Erase All and Install" Options? Of which release ISO? And how does that create a bug?

"Erase All" does means and imply that it will erase everything on that hard drive, yes. I don't see where that is a bug though. Maybe you would explain where the possible bug might be?

---

### Post by TheFu on 2024-04-15
The Unix Philosophy asks only if what the user requests CAN be done, not if it is **smart **or **stupid**.  Sometimes there are times when doing something that is usually stupid is pure genius.  That's my story, and I'm sticking with it.

Sometimes we need to wipe an entire drive or partition.  The OS shouldn't guess, so most CLI tools will require a "--force" option to be used.  Just a few days ago, I wanted to clone an entire HDD.  The command I used was
```
sudo ddrescue /dev/sda    /dev/sdf   /tmp/8tb.log
```
That failed. The error told me to add "--force" if I really wanted to wipe everything on sdf, which I did.
```
sudo ddrescue --force   /dev/sda    /dev/sdf   /tmp/8tb.log
```

If ran overnight and didn't finish.  sda is a disk that is failing, so I didn't think it would finish. 

If I got the order of the command arguments wrong, it would be a really bad day.  I would have done something stupid. Not the first time ... er ... today. ;)

But I want the computer to do what I ask, not hold my hand as I try to cross the street.
Inside the installer, doing disk setup, I've been frustrated more than a few times, when I'd setup all the storage I wanted and the installer refused to continue because I hadn't created a BIOS partition that wasn't going to be used anyway.  In the end, I didn't have a choice but to create a 1MB partition that has never been used. It was required to get the installer to do anything farther.
```
nvme0n1               disk                    931.5G                               
&#9500;&#9472;[COLOR="#FF0000"]nvme0n1p1           part  ext2                  1M[/COLOR]                               
&#9500;&#9472;nvme0n1p2           part  vfat                 50M   43.9M    12%                /boot/efi
&#9500;&#9472;nvme0n1p3           part  ext4                700M  339.8M    42%                /boot
&#9492;&#9472;nvme0n1p4           part  LVM2_member       930.8G                               
  &#9500;&#9472;vg01-swap01       lvm   swap                4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01       lvm   ext4                 35G   24.8G    22%                /
  &#9500;&#9472;vg01-var01        lvm   ext4                 20G     14G    23%                /var
  &#9500;&#9472;vg01-home01       lvm   ext4                 20G   10.1G    44% home01         /home
...

```
nvme0n1p1 is useless. Completely unnecessary.

---

