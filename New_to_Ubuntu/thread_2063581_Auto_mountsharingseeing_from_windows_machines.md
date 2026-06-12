---
title: "Auto mount/sharing/seeing from windows machines"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by watson524 on 2012-09-27
Hi all,

I'm not new to ubuntu per say but I have very limited experience with fixing things when they don't just "work". I recently went from 10.04 to 12.04 with a clean install from the CD. I have an 80gb and 320gb internal drive as well as a 2Tb external drive plugged in via USB. 80gb drive is the OS drive, 320gb drive is currently blank. 2 Tb drive has a lot of data on it I can't lose.

At a high level, here's what I want to do:
1.) Have all drives mounted on startup
2.) Be able to see 2Tb and 320Gb drive from 2 windows 7 machines that are in the same workgroup (called workgroup)

Doesn't seem too hard but I'm lost

The 2tb drive seems to mount on startup no problem (shows in the bar on the left automatically). I didn't have to do anything to achieve this. Mount point is /media/2tbext

The 320gb drive is an issue. It wasn't mounting on startup so I said ok, I'll put it in fstab. That worked, sort of. When I start up, it looks like it's mounted twice in devices, once with the "eject" symbol next to it, once without. When I click on the one without, it says:
mount: /dev/sdb1 already mounted or /media/320gbint busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/320gbint

when I click on the one in devices with the eject symbol, it seems fine, comes up as a blank drive.

So before I delve into getting the sharing to work, I figure I better get this auto mount sorted out.

any help would be appreciated. As I said, I'm "new" and also, 12.04 looks totally different to be from 10.4 (not bad, just am a bit lost on where things are).

---

### Post by HiImTye on 2012-09-28
go to the mounted drive then right click on it (above the file list), choose 'Properties' and see where the mount point is. this will be a combination of 'Location' and 'Name'
also, can you paste your fstab?

---

### Post by Morbius1 on 2012-09-28
In addition to posting your /etc/fstab file it would also help if you post the output of the following commands:
```
sudo blkid -c /dev/null
``````
mount
```

---

### Post by watson524 on 2012-09-28
On this boot up, I commented out the mount command for this drive and manually mounted it. When I go to devices and right click location = /media and volume says 320gbint

If I unmount, edit fstab and save it, it shows the 2 320gbint drives again and I'd have to mount them manually. I did that for the second one that showed up it says mount point /media/320gbint doesn't exist. if I try to mount the first one (since I didn't reboot) it says error mounting: mount exited with exitcode 1: help filed with: mount /mount point /media/320gbint does not exist.

Below is the fstab file:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e7de6203-2f5b-4fc1-a8cd-e452f7bfa9b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d28ef1b2-0d8b-4f5a-a5d1-f15c3e429783 none            swap    sw              0       0
# /media/320gbint
UUID=06C8-D705 /media/320gbint vfat user 0 0


here's the output from sudo blkid -c /dev/null
/dev/sda1: UUID="e7de6203-2f5b-4fc1-a8cd-e452f7bfa9b9" TYPE="ext4" 
/dev/sda5: UUID="d28ef1b2-0d8b-4f5a-a5d1-f15c3e429783" TYPE="swap" 
/dev/sdb1: LABEL="320gbint" UUID="06C8-D705" TYPE="vfat" 
/dev/sdc1: LABEL="2tbext" UUID="4B790C8E2AFC31F1" TYPE="ntfs"

and here's the output from mount:
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/michele/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michele)
/dev/sdc1 on /media/2tbext type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)


thanks in advance for having a look

---

### Post by Morbius1 on 2012-09-28
By default Ubuntu will mount through Nautilus any non-fstab defined partition to /media/LABEL - if there is a label. This is a mount point that is created on the fly for that mount and then removed when it's unmounted.

[1] Unmount the partition if it's currently mounted:
```
sudo umount /media/320gbint
```[2] Create a permanent mount point for that partition:
```
sudo mkdir /media/320gbint
```[3] Add a line to the end of fstab to have it automount:
```
UUID=06C8-D705 /media/320gbint vfat defaults,utf8,uid=1000,umask=000 0 2
```[4] Run the following command to test for errors and if there are none mount the fat32 partition with it's new fstab entry:
```
sudo mount -a
```

---

### Post by watson524 on 2012-09-28
That did it. sudo mount -a didnt' return anything so I rebooted and it's mounted right from the get go. So was the trick that I needed to do the mkdir to make it a permanent thing? I am going to be adding a few other internal/external drives so I want to make sure I understand.

Also - is it best to open another thread on my sharing issues to win7 machines?

---

### Post by Morbius1 on 2012-09-28
> sudo mount -a didnt' return anything so I rebooted and it's mounted right from the get go."sudo mount -a" will return nothing if everything worked. It's a UNIX thing. All you needed to do is go to the /media mount point to see if it was there. I should have explained that better.
> So was the trick that I needed to do the mkdir to make it a permanent thing?Yes.
>  Also - is it best to open another thread on my sharing issues to win7 machines?     Depends on the nature of the problem. Have you already created shares?

---

### Post by watson524 on 2012-09-28
thank you for the explanation! 

Yep shares are created on 2tbext and 320gbint

Linux box is in the workgroup "workgroups" login IDs on the linux box are michele and will.

Windows 7 laptop - login = michele, in the workgroup "workgroup". No issues. Can map drops to //michele-linux/2tbext and /320gbint. Can also browse to michele-linux in "network" and see both drives on linux tho sometimes it seems fluky where it'll drop and prompt me for a password again but the network itself is fine.

Windows 7 laptop - work laptop, in a domain but I know I've had this work before where I could still map and all. Doesn't seem to want to let me do anything there. Can't even see it in network so it doesn't even give me the chance to put in an ID and passowrd (since my work login is different than linux). Don't care to have linux see work laptop but would like work laptop to get to linux since that's where all the personal data is.

Windows 7 laptop - my husband's. His login on his laptop is will and I have created that account on linux. In his network, he doesn't see the linux box and when you try to map the drive, it says \\michele-linux can't be found (mapping as \\michele-linux\2tbext)

I don't have "guest access" checked off on my shares but I would image that should onnly impact my work laptop if anything because the login from my laptop and his laptop have accounts created on the linux box.

---

### Post by Morbius1 on 2012-09-29
I'm probably not going yo be able to help you with the work computer because the IT staff has no doubt loaded it up will a whole layer of authentication and firewall software. All of that is beyond my pay grade.

Will's Win7 laptop is another matter. Let's start with some basics. Please post the output of the following commands from the Ubuntu machine:
```
smbtree
```
```
testparm -s
```
```
net usershare info --long
```
[COLOR=Blue]*Don't be concerned if you did not get an output from the last command. There are 2 ways to create Samba shares and I don't know which one you used.*[/COLOR]

---

### Post by watson524 on 2012-09-29
On the work one, I figure you're right as far as all the extra crap. No wonder it takes almost 10 minutes to boot up. But in theory, you don't need to be in the same workgroup to see another computer right?

As for will's, here's the output you asked for. Thanks!

Interesting, my windows laptop (michele-windows) doesn't show up in the smbtree command. Wonder if that's causing the inconsistent connection.

michele@michele-linux:~$ smbtree
Enter michele's password: 
WORKGROUP
	\\WILL-PC        		
	\\MICHELE-LINUX  		michele-linux server (Samba, Ubuntu)
		\\MICHELE-LINUX\2tbext         	
		\\MICHELE-LINUX\320gbint       	
		\\MICHELE-LINUX\CraftPrinter   	HP Officejet Pro 8500 A910
		\\MICHELE-LINUX\IPC$           	IPC Service (michele-linux server (Samba, Ubuntu))
		\\MICHELE-LINUX\print$         	Printer Drivers
IRI_CORP
===============================================================

michele@michele-linux:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

===============================================================
michele@michele-linux:~$ net usershare info --long
[2tbext]
path=/media/2tbext
comment=
usershare_acl=Everyone:F,
guest_ok=n

[320gbint]
path=/media/320gbint
comment=
usershare_acl=Everyone:F,

---

### Post by Morbius1 on 2012-09-29
>  But in theory, you don't need to be in the same workgroup to see another computer right?You are correct. In a normal home network where everyone is in the same subnet ( all connected to the same router ) it doesn't matter how many workgroups exist ( I have 4 at the moment ). As I recall Win7 unlike earlier Windows doesn't even let the user know what workgroup he's in when browsing the network.
> Windows 7 laptop - my husband's. His login on his laptop is will and I  have created that account on linux. In his network, he doesn't see the  linux box and when you try to map the drive, it says \\michele-linux  can't be found (mapping as \\michele-linux\2tbext)\\michelle-linux\2tbext is a bad example. It's an external usb NTFS partition and as such it will mount with michelle as owner and with access permitted only to you. 

It's odd that one Win7 machine can see the shares and one cannot. Here's my suggestion:

Edit smb.conf as root:
```
 gksu gedit /etc/samba/smb.conf
```Add 2 lines to the [global] section under the workgroup line:
```
name resolve order = bcast host lmhosts wins
force user = michelle
```Then restart samba:
```
sudo service smbd restart
```Wait about 5 minutes after the samba restart and try to access the Linux shares again.

** The name resolve order is a change to the default samba settings and places bcast first since it's the only one that will work by default. 

** The force user to your username happens after authentication. For example Will will be prompted for authentication and if successful will then be converted to michelle for these samba shares. At that point he will have Linux permissions to access /media/2tbext since he will be you.

If Will still cannot access or even see the Linux box find out if the samba connection is working at all between these 2 machines by accessing the Linux box by ip address not by name. Maybe there's an overactive firewall on Will's machine preventing access.

---

### Post by watson524 on 2012-09-29
I have to dig into this further tonite when I get back. The above commands didn't change Will's situation but I just got on his laptop and he said he just uninstalled AVG and ran ccleaner and now when I go to a browser search, I found out he has some virus that is forwarding his search to an allsearch webpage. In reading about this, it also changes DNS settings and such which very well may be an issue. I'm wondering if AVG suppressed the issue for the browser but the underlying settings were there causing this overall issue. Have to dig into getting that off and cleaned up first before I go any further and have folks trying to solve an issue for me. I did try mapping a drive to \\michele-linnux\320gbint and also \\10.233.38.1\320gbint and no go on either.

---

### Post by watson524 on 2012-10-02
Took me some time to get back to this. It appears that I have his computer cleaned up now but still no go on the networking issue. I actually was able to get my work laptop connected to my windows laptop and the linux server using the IP address vs the name which makes me think my work machine has a DNS "issue" but I'm fine using the IP address as I keep static on the linux server and won't connect to the windows laptop much.

On Will's laptop, I can ping both 10.233.38.10 (linux) and 10.233.38.27 (michele windows non work laptop) with no issues but I'll be darned no matter what I do, I can't get his laptop to see the machines in "network" or even by mapping a drive using \\10.233.38.10\2tbext for example.

I did notice that his machine is part of a homegroup allegedly and when I try to get out of it, it says windows can't remove your computer from the homegroup. I don't know if that's causing an issue or not.

thanks!

---

### Post by watson524 on 2012-10-03
Something else I just noticed while I was testing something entirely different, when I'm logged in on the linux machine as another account but "michele" (admin), I don't see my 2tbext drive mapped automatically. Not sure if that has anything to do with anything?

---

