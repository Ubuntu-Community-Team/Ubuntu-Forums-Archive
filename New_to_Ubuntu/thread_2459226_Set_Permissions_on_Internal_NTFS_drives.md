---
title: "Set Permissions on Internal NTFS drives"
date: 2021-03-13
forum: New to Ubuntu
---

### Post by ecronic on 2021-03-13
Hi All,
I'm fairly new to Ubuntu & Linux environment. I have dabbled with the OS(mostly using Ubuntu builds) but am in a fix this time.

OS: Ubuntu Desktop 20.04LTS
Hdd1: 500gb - completely dedicated to Ubuntu
Hdd2: 3TB NTFS - for Media Sharing
Hdd3: 3TB NTFS - for Media Sharing

What I'm trying to achieve: I want to use Ubuntu as a media server. I'm using qbittorrent to save my downloads directly on the internal NTFS drives. I have NVIDIA Shield with Plex Media Server that I will be using to point the media to on the Ubuntu pc. I want to share the drives so the Nvidia Shield can access it. I also want to be able to access the drives via local network through my Windows 10 PC.

Problem: Unable to share folder on the local network. Shows I am not the owner. Shows root as the owner.

Tried so far: 

Method I: I have mounted the drives via Disks. But when I right click to go into properties and enable share, I get the error saying my user is not the owner so cannot change any of it.

Method II: I googled and tried the commands/steps below to mount the drives through terminal:
1. Identify the partition:[INDENT]sudo blkid[/INDENT]
2. Create the directories to mount the drives:[INDENT]sudo mkdir /media/disk1/[/INDENT]
[INDENT]sudo mkdir /media/disk2/ [/INDENT]
3. Mount the NTFS partition to Linux filesystem:[INDENT]sudo mount /dev/sda -t ntfs-3g -o permissions /media/disk1/[/INDENT]
[INDENT]sudo mount /dev/sdc -t ntfs-3g -o permissions /media/disk2/[/INDENT]
4. Permanently mount the partitions. Added these 2 lines at the end:[INDENT]sudo nano /etc/fstab
UUID="disk1ID"  /media/disk1/  ntfs-3g permissions   0     1
UUID="disk2ID"  /media/disk2/  ntfs-3g permissions   0     1[/INDENT]
5. Change the Permission:[INDENT]sudo chmod ugo+wx /media/disk1/
sudo chmod ugo+wx /media/disk2/[/INDENT]
6. Restart OS

After doing these steps, I tried to define the folder in qbittorrent for downloading to these folders. But when I browse for the folders, it doesn't show me the drives in the Nautilus file explorer.

Can someone please guide me as to what am I doing wrong or provide a simpler solution. I remember this being a lot easier in the previous versions of Ubuntu and also I believe all the mount and share operations were done easily via GUI interface.

Thanks in advance
Dev

---

### Post by yancek on 2021-03-13
A default install of windows will not understand Linux permissions (755, 644, etc.) so you need to use umask, dmask.  Countless sites on line explaining this.  The answer to a similar question at the link below should give you a clue.

>  But when I right click to go into properties and enable share, I get the  error saying my user is not the owner so cannot change any of it.

Well, that's because you in the GUI and trying to make the change while logged in as a normal user.  If you want to access the file on a network you will need to use Samba.  Have you configured that?

---

### Post by ActionParsnip on 2021-03-14
Are you dual booting with Windows here? If not then why are you using NTFS?

---

### Post by Impavidus on 2021-03-14
If Windows only accesses the files via the network, there's no need for NTFS. The server (your Ubuntu system) will translate the filesystem as present on the hard drive to some networking protocol. You only need NTFS if Windows is supposed to access the hard drives directly. If there's no Windows installed on this computer, use a Linux filesystem.

When you use fstab to mount partitions, they will not be listed as removable drives in the file manager. You can just navigate to the directory you used as a mountpoint.

For setting up actual file sharing, I can only point you to the guides we have for that: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by Morbius1 on 2021-03-14
> 4. Permanently mount the partitions. Added these 2 lines at the end:[INDENT]sudo nano /etc/fstab
UUID="disk1ID"  /media/disk1/  ntfs-3g permissions   0     1
UUID="disk2ID"  /media/disk2/  ntfs-3g permissions   0     1
[/INDENT]
5. Change the Permission:[INDENT]sudo chmod ugo+wx /media/disk1/
sudo chmod ugo+wx /media/disk2/
[/INDENT]

** You really really ... really ... don't want to use the "permissions" option. It was a popular thing to do back in the day but only by people who read the man pages for ntfs but never had to live with the results.

Run this command to find the correct UUID number for your partitions:
```
sudo blkid -c /dev/null
```
Then change your fstab entries to look something like this:
```
UUID=bunch-of-numbers  /media/disk1 ntfs uid=1000,umask=000,windows_names 0 0
UUID=some-other-bunch-of-numbers  /media/disk2 ntfs uid=1000,umask=000,windows_names 0 0
```

**uid=1000** == changes the owner of the mounted partition to you ( run the [highlight]**id**[/highlight] command to verify your uid number )

**umask=000** will make everything rwx. This will happen by default anyway but keep it there in case you want to change things.

You seem to be using Nautilus to share the partitions which you should be able to do now that you are the owner.

Also remember that WIn10 out of the box will never be able to "discover" your Ubuntu 20 samba server or any other box that relies on NetBIOS. But you can still connect to the box by specifying its location explicitly in Explorer:
```
\\ubuntu-host-name.local
```
Don't forget the ".local" part.

---

### Post by TheFu on 2021-03-14
Morbius1 is correct. 

I'd change the fstab lines 
```
UUID=some-other-bunch-of-numbers  /media/disk2 ntfs uid=1000,umask=**0**00**2**,windows_names,**big_writes** 0 0
```
to improve performance for ntfs and the mask for better security.

If you want more users to have write/delete then the gid will need to be used to avoid completely open access.

chmod/chown/chgrp have no impact on ntfs. Only through mount options, can those be controlled and only at mount time.

---

### Post by Morbius1 on 2021-03-15
Just a follow up since I noticed a few things in your original post:

First: I would keep the umask at 000 ( you can set it to 0000 if you want - it makes no difference ). No need to overthink the plumbing at this point. You can always use Sambas function as a gatekeeper to limit who has access later.

Second: there is this:
> After doing these steps, I tried to define the folder in qbittorrent for  downloading to these folders. But when I browse for the folders, it  doesn't show me the drives in the Nautilus file explorer.
There are 2 qbittirrents in the Ubuntu Software application - one is the  ... um ... real one ... and the other is a snap. The "real" one should have been able to access the mount points whereas the snap version would not unless you allow it in Ubuntu Software. Go back into Ubuntu Software for qbittorent and select the Permissions tab.

Plex has the same issue in that it is also a snap so you will need to do to Plex what you did to qbittorrent[URL="https://forums.plex.tv/t/proper-way-to-run-plex-as-another-user-with-systemd-ubuntu-server-16-04-lts/158853/2"]



[/URL]

---

### Post by TheFu on 2021-03-15
ecronic - Morbius1 is the cook you should be following here. He knows samba. The other posters, including me, are adding information that isn't strictly mandated, but would be worth considering AFTER it works doing what Morbius1 outlines. We are all knowledgeable, just in slightly different ways.  I'll just leave it there.

Morbius1, how do you know those are snap applications from the data provided? I'm not getting that from above. Looks like plex is running on a completely different system - on an nVidia Shield - that would access this storage over Samba.

I'd need to see output from **snap list** to know what is and isn't snaps. Nautilus might be a snap based on the description, but I'm not certain.

---

### Post by Morbius1 on 2021-03-15
> Morbius1, how do you know those are snap applications from the data provided?
It's a guess.

From his post he is using Ubuntu Desktop 20 and he is creating samba shares from Nautilus instead of editing smb.conf. Seems like a GUI kinda user to me and my guess is that he used the "Ubuntu Software" app to install software.

The "Ubuntu Software" application has two qtbittorrents ( one of which is a snap ) and only one Plex which is a snap.

---

