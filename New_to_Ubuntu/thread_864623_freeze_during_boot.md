---
title: "freeze during boot"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by sarah_a on 2008-07-19
I'm trying to help a friend with her computer, but have no idea where to start. Shortly after the Ubuntu spalsh screen, her computer freezes while checking file systems.  This happens on every boot attempt.

Computer = dell desktop demension 8400, intel pentium 4, ubuntu gutsy


I've tried booting in generic and recovery mode, but have the same problem.  What I see on screen when it freezes is the following:

========

fsck 1.40.2 (12-Jul-2007)
/dev/sda1:clean, 133366/30343168 files, 2172830/60659424 blocks
                                                                 [OK]
*Checking file systems...
fsck 1.40.2 (12-Jul-2007)

*Mounting local filesystems...                    [ OK ]
*Activating swapfile swap...                      [ OK ]
$Mounting securityfs on /sys/kernel/security:done
Loading AppArmor profiles: done.
*Checking minimum space in /tmp...                    [ OK ]
*Confiiguring network interfaces...                   [ OK ]
*Setting sensors limits...                            [fail]
*Loading ACPI modules...                              [ OK ]
*Starting system log daemon...                        [ OK ]
*Doing Wacom setup...                                 [ OK ]
*Starting kernel log daemon                           [ OK ]
*Starting system message bus dbus                     [ OK ]
*Starting network connection manager NetworkManager   [ OK ]
*Starting network events dispatcher NetworkManagerDispatcher [ OK ]
*Starting System Tools Backends system-tools-backends [ OK ]
*Starting Hardware abstraction layer hald             [ OK ]
*Starting Avahi mDNS/DNS-SD Daemon avahi-daemon       [ OK ]
*Starting Common Unix Printing System: cupsd              _  

====

I've searched the forums to find out about the sensors limits, and it seems to suggest there shouldn't be a problem if that part fails.  Is there something I could do to find out if cupsd is my problem, or if it's something else entirely?

If anyone could offer any suggestions as to what I could do to trouble-shoot this one I would greatly appreciate it.  I can still gain access to virtual console, but am not sure where to look or what to change to get the computer to boot.  I would ideally like to not have to install ubuntu from scratch...

Any tips????

---

### Post by spiderbatdad on 2008-07-19
It does seem to hang at cupsd...which seems like a strange place to hang...as it isnt a hardware detection problem (presumably.) Have you tried waiting 5 minutes or so for the system to boot? Then you might be able to get a complete dmesg.

or try booting with the F6 option and delete --quiet splash, and replace with noapic

If that solves the boot issue, you will need to edit the kernel line in /boot/grub/menu.lst to make the change permanent.

---

### Post by sarah_a on 2008-07-19
Thanks for getting back to me so quickly- 
We've tried leaving the computer be for a long while and it continues to hang at cupsd.

Also, I'm not sure if I understand about booting with the F6 option unless you're talking about doing this while booting off the Live CD.  I've tried booting her computer using the live CD (with and without adding noapic) and it seems to load to the desktop just fine.

I looked at her /boot/grub/menu.lst using "nano" and noapic is not currently part of her boot option.  I then tried "sudo nano" to edit this line to find out if it would make a difference, but the computer is now hanging at $sudo nano /boot/grub/menu.lst

Any suggestions?

---

### Post by spiderbatdad on 2008-07-19
if you need to edit menu.lst again to remove noapic, you can try booting into recovery mode. If that fails, you can boot off the live cd and mount the user's filesystem:

Open a terminal from the live cd:
```
sudo fdisk -l
```note the location of linux filesystem. If this is the only os, it should be sda.
```
sudo mkdir /media/sda
sudo mount -t ext3 /dev/media/sda
```That should mount the file system on the desktop so that you can navigate into it and edit it with gksu nautilus or sudo nano. I hope I have that all right...been a while since I've tried that...if there is a problem with the commands above for mounting the filesystem from the live cd, just say so, and I can try it myself to get the commands corrected.

---

### Post by sarah_a on 2008-07-20
Hi - thanks again for getting back to us.  We made it through the list of commands up to:

sudo mount -t ext3 /dev/media/sda

but received an error about usage.  Looks like usage for the -t switch says "mount -t type dev dir", so we also tried

sudo mount -t ext3 dev /media/sda

which gave us a "mount: special device dev does not exist".  I'm not sure which command would allow us to mount it, so if you have the chance to figure out the right commands, please do let us know.

---

### Post by spiderbatdad on 2008-07-20
Hi, sorry you had that problem. The command sudo fdisk -l should have listed a # after sda, particularly you are looking for the root partition, denoted by "/" So you should see something like this:
```
sudo fdisk -l
/dev/sda1   *           1        4659    37423386   83  Linux /
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap Solaris


```Yours will likely look a little different.

OK brain cramp on the previous mounting commands. This should wrork from the live cd:

```
sudo -i
mount /dev/sda1 /mnt
cd /mnt
nano /boot/grub/menu.lst
```

Originally I thought you would try the boot option, with f6, noapic, from the grub menu before editing menu.lst, to make the change permanent. If this is the only os, perhaps the grub menu is hidden at startup. You can display it by pressing the esc key after powering on the system and before it boots. menu.lst can also be edited to display the grub menu by default...this is where recovery mode is accessed as well.
Look for the section hiddenmenu. Comment it like so: #hiddenmenu

---

