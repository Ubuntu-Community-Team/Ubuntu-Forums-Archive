---
title: "Shell Script To Auto-Mount Samba Shares"
date: 2009-09-16
forum: Programming Talk
---

### Post by angel120 on 2009-09-16
On my home network, I have a Windows Home Server.  I wrote a shell script for my laptop that runs at startup which checks my IP, and mounts the Samba shares if they match my home network's internal IP addresses (LAN and/or WLAN).  However, I'd like to improve upon it.

Problems with my current script:
[list]
[*]My server is set to a timer (WOL (Magic Packet) @ 10am, and hibernate at 11:59pm).  So, if my server hibernates while the shares are still mounted, Nautilus will crash just by opening it (without even attempting to access the shares).  (This also happened when I added the shares to **/etc/fstab**) 
[*]I added the script to Startup Applications (command: **gksudo ./sambaMount.sh**), but this slows down my startup, since the gksudo prompt seems to pause the system until the password is entered.
[*]If my laptop hasn't finished connecting to the network before the script runs, the script will not mount the shares (because my IP won't match the ones in the script).
[*]The script checks my IP addresses.  If I'm on a different network (away from home), but my IP address happens to match either one in the script, I'm not quite sure what would happen.. (This may be a million-to-one shot, but I like to cover all bases.)
[/list]

What I'd like to do (for now) is: 
[list]
[*]Check which SSID my laptop is connected to, as opposed to my IP address(es), and then mount the shares if the SSID=="Home".
[*]Mount the shares without prompting for the root password (so it would be fully automated).
[*]Mount only if the server is online.
[*]Run the script when booting from a full shutdown, sleep, or hibernate. (Though I often use sleep)
[/list]

Future plans (if possible):
[list]
[*]Get rid of the server's timer, and have all my home computers wake the server as soon as they connect to the network.
[*]Hibernate the server once all of my home computers are offline. (I don't like the idea of having my server run 24/7 if it's not needed, for the electric bill & security reasons.)
[/list]

So, how would I go about doing these things?

Here is the source code:
```

#!/bin/sh
#Reads the current IP address.  If it's on the Home network, it will mount
#AngelWHS shares.  Otherwise, it will exit.

IP=`ifconfig | grep 'inet addr:' | grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'`;

if [ "$IP" = "192.168.1.126" ] || [ "$IP" = "192.168.1.134" ]; 
then
	echo "\nHoney, I'm home!\n"
	
	smbmount //angelwhs/users/angel /media/DocumentsWHS -o credentials=/home/angel/.smbpasswd
	echo "Mounted Documents"
	
	smbmount //angelwhs/public /media/PublicWHS -o credentials=/home/angel/.smbpasswd
	echo "Mounted Public"
	
	smbmount //angelwhs/music/angel /media/MusicWHS -o credentials=/home/angel/.smbpasswd
	echo "Mounted Music"
	
	smbmount //angelwhs/photos/angel /media/PhotosWHS -o credentials=/home/angel/.smbpasswd
	echo "Mounted Photos"
	
	smbmount //angelwhs/videos /media/VideosWHS -o credentials=/home/angel/.smbpasswd
	echo "Mounted Videos"
	
	smbmount //angelwhs/software /media/SoftwareWHS -o credentials=/home/angel/.smbpasswd
	echo "Mounted Software"
	
	smbmount //angelwhs/torrents /media/TorrentsWHS -o credentials=/home/angel/.smbpasswd
	echo "Mounted Torrents"
fi

```

As a side note, this is my first shell script, and I'm fairly new to Linux (I've been a Windows user all my life).  I know a lot about computer hardware, but very little about networking.  I'm also a 4th-year computer science student, and a fairly decent programmer.

Any and all help is appreciated.  I wish I had a better understanding of Linux commands, but I'm sure I'll be able to do better over time.

-Angel.

---

### Post by lensman3 on 2009-09-16
I don't know if this will help, but my copy of "autofs"  (it mounts filesystems automatically when you access a file on the mount point) has a script that might do what you want.  See /etc/auto.smb.  

This script will mount a smb file system.  The autofs will umount a remote file system if it has been idle for a set time.  

Hope this helps.

---

### Post by angel120 on 2009-09-17
Thanks for your input, but unfortunately, I can't seem to find either "autofs" or "auto.smb" on my laptop..  Were there any packages that I needed to install?

Small update: Was able to fix the problem of the script running before I was able to connect to a network.  I simply put a delay on the execution (sleep 1m).

---

### Post by lensman3 on 2009-09-17
autofs is an added package.  I think, it was originally written by SUN (in the '80s) to mount NFS file systems but to only keep them mounted while the file system was in use.

I think autofs is going the way of "not invented here" for Ubuntu and Red Hat.

You might take a look at cron.  Have cron setup a time for mounting and umount.  Cron works best if the machine is left on 24/7.  

Another solution is to pop each of your mounts into background with a 1 minute sleep.  That way you could continue, but the mounts are "running" silently in background.  It would also allow all the mounts to start simultaneously and all finish 1 minute later.  Not 7 minutes later if you are doing 7 mounts.

---

