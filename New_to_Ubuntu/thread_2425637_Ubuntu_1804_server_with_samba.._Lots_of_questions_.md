---
title: "Ubuntu 1804 server with samba.. Lots of questions from &quot;newbie&quot;"
date: 2019-08-28
forum: New to Ubuntu
---

### Post by DeathByDigital on 2019-08-28
Hello everyone.. 

"new" user with a lot of questions...

guess all questions have been asked and replied before and yes, google is my friend. (has been my only friend the last 4 days)
Trouble is with linux, its xxxx distro's and 2000 different ways to do stuff,-and then add versions, where the guide usually is older than the version i try to use today, -the numbers of variables are countless. 
usually I've managed to follow guides to a point, and then it stopped either by version used, differs from guide, or I should have understood some basic commands that for normal users are self explained......
The trouble is finding what actually works on my setup, and often guides are not "dumbed down" enough for newbie like me.
(ive been using windows too long and are stuck in windows thinking) <-- main problem 

Ive finally managed to get a setup running with ubuntu server 18.04.3  and samba server. (after about 12 tries :D in 4 days!
using this guide : [https://www.youtube.com/watch?v=RDwoDj2cW6c](https://www.youtube.com/watch?v=RDwoDj2cW6c) 
System ive got is amd FX8350 with 250gig system disk, 2 x 1tb disks, and a 3tb NTFS disk with my old pictures on. (this is my main question)

during the different tries, i added the 2x1tb under mnt/fdc and /mnt/fdd but struggle to understand privileges and mount points root user and where directories and what not was ending up.

Finally i added the 2 1tb disks as LVM under install of ubuntu server, (have no clue if and how that works, since i think they are added to the total amount of free space ive got)
(they dont show up under fstab, but i found them listed under another command ( lsblk, fdisk, df or one of the others ive googled) (sdc and sdd: LVM2_member) if remember. 

 Question for starters to keep it "simple"

1) how does ubuntu manage the 2 1tb disks? are they all just added to the total amount of space ive got on the server?
if im in home dir and make a directory (mkdir /media) and fill that with all my pictures and media, is the files/space used by them "just spread around my total disk space of the 250gb systemdisk+ the 2 1tb disks"? 

2) how do i mount the NTFS disk without destroying my pictures on it? (ive got over 20 years of pictures on it (have USB backup disk ofc, but ive read linux can read NTFS disks.
Asking for help to a good guide.

3) what is a simple install and forget antivirus suitable for a stand alone file server? 

4) reason i started with this was wife got new phone again, and she had pictures from cells on 5 different cloud services, (i cloud, google pictures, and so on) 
she had lost a few phones, changed phone company, and such, so thought it was time to collect a few thousand pictures spread around and bring them home.

5) is there a easy app for transferring pictures from phones to server? ive just tried X-plore and it works, but too much settings and things you can do, for a lvl 0 user....
(i know there is a own cloud app or something, but its intimidating to try on my lvl.....)  kinda looking for a app connected to the users folder on the server, that syncs when home. 

6) since i used the guide above the user and password for each user/share is the same.. guess kids will go to war when they figure each others genius login/password. name:name for user and password
how do i change that? do i need to change password for both user in ubuntu and samba? if so how?  

Thanx in advice

---

### Post by TheFu on 2019-08-28
Sorry, I don't understand all your abbreviations.  I'm old.  I know LOL, BTW, IMHO, but that's about it.

As a newbie, you will have a huge hill to climb.  Learning Linux is like learning to speak a new language.  4+ hrs a day for 6 weeks and you'll still be an advanced-beginner.  Here's a free, no-hassle download, reference book [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) . If you can, start at the beginning and work through a chapter each week. Linux skills build on prior skills that have been mastered. Google skips all over the place, so you really can't use it until a solid foundation has been learned.  Understanding multi-user OSes is the first step, then permissions, then processes, and that will get you into the beginning stuff.

Also, the Ubuntu Server Guide: [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

LVM brings enterprise storage capabilities to Linux.  It is not beginner friendly.  I was a Linux admin for about 4 yrs before I touched LVM.  I wouldn't suggest a beginner use LVM unless they planned a professional career in storage management or as a Linux admin.  Home users tend to shy away from LVM because of the added complexity.  That complexity provides fantastic flexibility in the hands of an expert.  Only you can decide if LVM is for you. I can help with or without LVM.

If you don't learn Unix file and directory permissions ASAP, you will be frustrated daily.  Learning them now will save you hours, days, weeks, months of frustration.  "Unix permissions tutor" is the search.  Basically, every popular OS in the world, except 1, uses this same permissions model, so it isn't a waste of your time. I bet you can guess the 1 that doesn't. ;)

On Unix/Linux servers, no SATA connected storage is automatically mounted if you don't take specific action.  As the system admin, it is your responsibility to setup, create file systems, and mount the storage with the file permissions you want.  Desktops might automatically mount some USB/SDHC storage using gvfs to some restricted areas. These areas aren't available except to 1 userid.  How you would setup, format, mount any storage would depend on lots of things, but mainly whether you use LVM or not.  I use LVM on all my physical server installs.

So, first things first, we need some facts.  DO NOT post images. Copy/paste text here and use the Advanced Editor to wrap the exact command and output in *code tags*.  That's Adv Reply (#)
The commands that will show us information we need - connect all the storage devices up and run these:

```
$ lsblk  # this shows an overview of the storage, including LVM parts
$ df -hT -x squashfs -x tmpfs -x devtmpfs   # this shows what is already mounted, file systems, and excludes uninteresting types
$ sudo parted -l   # please,please cut all the "loop" devices. They aren't really storage and just clutter up the output

```
That's an example of proper code tags.  An article about this stuff ... 
[https://www.networkworld.com/article/3297916/examining-partitions-on-linux-systems.html](https://www.networkworld.com/article/3297916/examining-partitions-on-linux-systems.html)

When it comes to accessing and file transfers to/from any Unix system, there is 1 tool everyone uses all-the-time.  It is the family of ssh, sftp, scp, rsync tools.  These all work over encrypted channels, using key-based authentication.  Every OS that is networked has a nice ssh and sftp client.  Install the ssh-server and you get ssh, sftp, scp included for free. They all use the same port, which is very firewall friendly.
```
$ sudo apt install openssh-server fail2ban
```
The fail2ban package will dynamically block brute force attacks against the system if the ssh port is ever available over the internet. No extra configuration is needed, for now.

**WinSCP** is a nice Windows sftp/scp client program.
Every Linux file manager supports either the ssh:// or sftp:// URL to access a remote sftp connection. Nautilus, nemo, caja, thunar ... it is now drag-n-drop.  If you setup ssh-keys between the ssh client and server, then all ssh-based tools will use those.  ssh-keys are 1,000,000x more secure than any passwords AND more convenient. Actually keys are probably exponentially more secure, so 1,000,000,000,000x more secure.  Setting up keys and pushing the "public" part to remote systems is trivial on Unix systems. Perhaps 3 minutes of effort.  On the client machine, run these:
```
$ ssh-keygen -t ed25519
$ ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```
replace your userid and remote for the DNS resolvable server-name or server-IP.  If the userid on both systems is the same, you can leave out that part.  From the client, test by running 
```
$ ssh userid@remote
```
You know have a connection that the NSA, Russia, China and Israel govts cannot break.  AND your client-side file manager will use this key to authenticate to the "remote" server.

Ah ... NTFS ... while Linux can read and often write to NTFS, it uses a slow driver and doesn't support Unix permissions, so there will always be "issues" trying to use it as storage on Linux.  If that disk doesn't need to be physically connected to MS-Windows computers, I'd backup all the files and reformat it to use ext4 as the file system.  Then I'd copy all the files over to the ext4 file system from the backups.  If this isn't possible, just say that and say the type of connection the NTFS storage has to the computer so the best solution (fstab or autofs) might be suggested.

3) In general, nobody uses antivirus software on Linux.  Nothing will replace a smart user and all the AV products just scan for Windows viruses anyways, so what's the point?  "Basic Ubuntu Security" is the search for more on how to secure an Ubuntu system.

4) I use **sftp** and **rsync**  and **nextcloud** to manage which files are on my android devices. Nextcloud replaces most of the cloudy services on the internet, but you host it yourself on your hardware. It is a complicated web-app.  Probably not for a beginner to setup.  I don't use samba for phone/tablet file access.  BTW, if you allow 1 inbound port through your router, then your devices can access any files you have at home through sftp/ssh/scp and you can even setup a remote desktop all using highly-secure ssh key-based authentication and tunnels.  You can also securely use an ssh-tunnel and access a nextcloud server from any device on the internet.

ssh is how unix systems connect to each other.  There are at least 200 different, amazing, things that ssh can do.

I'll leave the samba stuff for others.

---

### Post by DeathByDigital on 2019-08-28
thank you for your reply. -really appritiate it... 


first. the server is up and running in the basement :)
as for SSH: the installation/commands where done over ssh from a windows laptop upstairs.


as from what i understand below the LVM is not "active". I can do a new install without LVM.. its ok to do this several times. ( i only learn more from it)
And if i reinstall the server, i would like to have sdc and sdd drives running mirrored.... 

I have no trouble going the route with copying my pictures from the 3gb drive, format it to EXT4 and put the pictures back on it...
AS for antivirus,  this server is pretty much only thought of as file server and to try to set one up. 

I have been lookng at owncloud/nextloud... i kinda want such setup, but never figured out how to manage 4 users into it.. (wife kids and me)
I dont want my kids to see all my pictures, so i started with this go at ubuntu stand alone server with samba... but own/next cloud would be great...


as for disks it looks like this:
~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda2      ext4  229G   15G  202G   7% /
:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0    91M  1 loop /snap/core/6350
loop1    7:1    0  88.7M  1 loop /snap/core/7396
sda      8:0    0 232.9G  0 disk
&#9500;&#9472;sda1   8:1    0     1M  0 part
&#9492;&#9472;sda2   8:2    0 232.9G  0 part /
sdb      8:16   0   2.7T  0 disk
&#9500;&#9472;sdb1   8:17   0   1.4T  0 part
&#9492;&#9472;sdb2   8:18   0   1.3T  0 part
sdc      8:32   0 931.5G  0 disk
sdd      8:48   0 931.5G  0 disk

---

### Post by TheFu on 2019-08-28
code tag, please. Can't read the output without it.

RAID is good for 1 reason, HA.  If you don't have excellent backups, please don't do RAID.  Backups are 1000x more important than RAID.  RAID1 == mirrored.  I don't think you really want that today.

Nexcloud has multiple users and groups. These are application-only accounts, nothing to do with system logins.
Each user and share or not directories with other users. Nextcloud has about 100 addons that might be interesting.  I use the video conferencing and voice chat one when the family wants to make plans to meet on vacation somewhere.  BTW, you should put nextcloud either in a virtual machine or a container. Don't mix and match it with your other installed services. This is for security and to make upgrades on each part easier.  The fewer dependencies there are, the easier the maintenance is, usually.

---

