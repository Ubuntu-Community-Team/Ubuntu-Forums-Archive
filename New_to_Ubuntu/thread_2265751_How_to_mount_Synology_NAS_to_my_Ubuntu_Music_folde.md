---
title: "How to mount Synology NAS to my Ubuntu Music folder"
date: 2015-02-17
forum: New to Ubuntu
---

### Post by bonedancr on 2015-02-17
So last weekend I finally had my last straw with Windows.  Formatted my computer, looked for a Unix distribution I wanted to learn (choose You, U).  I've always been a dive headfirst type of guy and now am enjoying the fun of figuring out things I took for second nature in Windows.

A couple questions for the veterans/helpful folk out there

1) I used to point my Music library at a NAS on windows (Synology DS1515+).  Can I 'point' my Music library at the NAS in a similar way here in Ubuntu.  Mainly I want music players and UI elements to 'see' my big storage natively rather then going through import processes/copying; i.e. a network share that looks local.  (I choose to encrypt my home folder and saw there are some issues with that)

2) I downloaded this cool bottom taskbar (Cairo) and would like to use it instead of the switcher on the left; is that possible?

3) Are there any good online tutorials on the command line stuff?  I'm already picking up things but would appreciate any helpful tips.

Thanks guys and have a great week!

---

### Post by sandyd on 2015-02-17
> **bonedancr said:**
> So last weekend I finally had my last straw with Windows.  Formatted my computer, looked for a Unix distribution I wanted to learn (choose You, U).  I've always been a dive headfirst type of guy and now am enjoying the fun of figuring out things I took for second nature in Windows.

A couple questions for the veterans/helpful folk out there

1) I used to point my Music library at a NAS on windows (Synology DS1515+).  Can I 'point' my Music library at the NAS in a similar way here in Ubuntu.  Mainly I want music players and UI elements to 'see' my big storage natively rather then going through import processes/copying; i.e. a network share that looks local.  (I choose to encrypt my home folder and saw there are some issues with that)

2) I downloaded this cool bottom taskbar (Cairo) and would like to use it instead of the switcher on the left; is that possible?

3) Are there any good online tutorials on the command line stuff?  I'm already picking up things but would appreciate any helpful tips.

Thanks guys and have a great week!
1) That NAS supports CIFS (Samba) and NFS. Can be mounted either way. I reccomend NFS if you want faster transfer speeds.
2) Two ways:
For hackyness, you can autohide it in System Settings > Appearance > Behavior
Else, you can change your desktop environment. Ubuntu has a ton of them which are fully customizable. Some of the main ones are Unity (the one your using right now), KDE, XFCE, LXDE just to name a few

3) [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) may be a bit useful. For more obscure tasks, asking here may be faster.

---

### Post by bonedancr on 2015-02-17
Don't suppose you'd be so kind as to help me with the commands to enable #1.  My goal is to make the Music folder actually show the contents of a share on the Synology.

---

### Post by sandyd on 2015-02-17
> **bonedancr said:**
> Don't suppose you'd be so kind as to help me with the commands to enable #1.  My goal is to make the Music folder actually show the contents of a share on the Synology.

Synology has a nice guide actually [https://www.synology.com/en-us/knowledgebase/tutorials/566#t4](https://www.synology.com/en-us/knowledgebase/tutorials/566#t4)

What you will want to do is follow the guide up to the last step, then use this as the mount command (see below for correct "username")

Go to the console (Unity Dash, Type in 'Terminal')

First, we find your "username" (replace $username in the mount command with this one)```
whoami
```
Second, we mount the folder
```

mount [DiskStation IP address] : [mount path of shared folder] / /home/$username/Music

```

---

### Post by bonedancr on 2015-02-17
Tried that got the first error message below

sudo mount 192.168.1.250:/volume1/music /home/dmoore/Music


mount: wrong fs type, bad option, bad superblock on 192.168.1.250:/volume1/music,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)


       In some cases useful info is found in syslog - try
       dmesg | tail or so.

---

### Post by sandyd on 2015-02-17
Hmm

Lets try telling mount that its NFS.
```

mount -t nfs 192.168.1.250:/volume1/music /home/dmoore/Music
```

---

### Post by steeldriver on 2015-02-17
Did you install the nfs-common package on your computer? it provides the mount.nfs program but it's not installed by default afaik. You can use Software Center or 

```

sudo apt-get install nfs-common

```

from a terminal.

---

### Post by bonedancr on 2015-02-17
same error;

if I open Nautilus, I can see the Nas and traverse the folders (after i supply credentials)

---

### Post by bonedancr on 2015-02-17
Installing the nfs stuff fixed the mount; now it says I don't have permission to view the folder in Nautilus.  Is there someway to pass credentials in a mount command?

---

### Post by steeldriver on 2015-02-17
The old-fashioned way would be to modify your numeric user and primary group IDs (uid and gid) on either the NAS or the Ubuntu system so that they match

Alternatively, the NAS probably allows you to export the share as 'public' so that authentication isn't required - for a music folder, that may be a simpler solution

---

### Post by sandyd on 2015-02-18
Few things i can think of:
Are folder privileges correct?
Does
```
sudo sh -c "ls -la /home/dmoore/Music"
``` produce the contents of the Music folder or does it error out as well? If it produces the contents of the folder properly, stop here and we can fix that


In NFS, userid and gid have to match. Luckily, Synnology supports Root Squash. [https://www.synology.com/en-us/knowledgebase/tutorials/566#t3](https://www.synology.com/en-us/knowledgebase/tutorials/566#t3) . Just set the Root Squash to map to guest.

If that does not work, we can force downgrade to NFS3, and if that still does not work, and worse comes to worse, we can just mount CIFS using /etc/fstab since we already know it works (In Naitulus, you have already managed to access it using CIFS)

How to force downgrade to NFS3:
```

sudo umount /home/dmoore/Music
sudo mount -t nfs -o nfsvers=3 192.168.1.250:/volume1/music /home/dmoore/Music
```

---

