---
title: "Authentication Required"
date: 2023-01-29
forum: New to Ubuntu
---

### Post by ajnanyc on 2023-01-29
Hello all,

I am new to Ubuntu. I just installed the latest version to rescue data from a crashed Synology drive. One of the folders on the crashed hard drive I'm trying to copy data from has a red cross on it, which I assume is restricted due to user permissions. I need to enter my Ubuntu password to access it. And when I try to copy it's contents, I also need to provide a password. However, when trying to copy the entire contents (4.1TB), I constantly get a prompt to enter the password. I've tried running 'files' as root and opening the restricted folder as administrator, but I still get the password prompt.
And I don't want to change the permissions of the folder, as I may still try to re-build the drive once I get the Synology up and running again. 
 I can't sit in front of it to babysit the entire process, so I was wondering if there is a not too complex solution to this? Thanks!

---

### Post by TheFu on 2023-01-30
Use 'rsync' to copy 1 or 50 or 500,000,000,000,000,000 files., assuming you can mount the source storage and have permissions to read it.  
If you don't understand Unix permissions, life will suck indefinitely until you learn those.  

There are lots of tutorials.  Spend 15 minutes on a tutorial, then spend another 30 minutes trying things in a temporary directory area with 3 users and 3 groups, mix and match directories, files, and permissions.  There is an elegance to Unix permissions. Until something "clicks" inside your brain, you will forever be frustrated.  Spend the 45 minutes now and learn this stuff once and for all.  It is the same for every popular OS, except 1, so this isn't wasted effort.  It applies to all smartphones and tablets phones too.

BTW, running a GUI program with sudo is a good way to break your system.  Doing it has locked people out of their normal userid.

---

### Post by ajnanyc on 2023-01-30
Hi. Thank you for your suggestion. I can mount and read from the source disk. The issue is the constant authentication prompt when copying from restricted folders. 

My goal was to only use Linux to rescue my data, and move on. I have no time or patience to learn a completely new OS for this task alone. I was hoping for a quick fix to my issue, but it seems that I will need to either a) babysit the process for hours on end, or b) start learning complex commands. On a positive note, one thing that Ubuntu has given me is a fonder appreciation of Windows OS haha. Thanks again.

---

### Post by TheFu on 2023-01-30
Use the OS you prefer.  That's always the rule. 

You should see me trying to use Windows or MacOS.  I get so very frustrated since many things that are trivial on Unix systems aren't possible on those other OSes.  So very frustrating.
Or perhaps it is just my ignorance that has me thinking those other OSes are very limiting?  Hard to say.  Definitely not worth installing them just to recover data.

When it comes to data recovery, always use native tools.  There is a help guide for "Ubuntu Data Recovery", but I fear it would be too complex for your skill level, leading to even more frustration. I don't think any of those tools have a GUI.

I take it you didn't try to use rsync?

---

### Post by ajnanyc on 2023-01-30
I don't think there's a perfect OS out there, and I've had my fair share of frustration with Win/OSX. But Ubuntu is on another level. The nice looking GUI gives you a false sense of confidence, until you soon realize it's superficial and there's a really steep learning curve to delve any deeper. It's a pity, cause it seems like a powerful Universal OS to learn.
 
I'm lucky to have gotten this far, after several failed attempts at trying to run on a VM with attached drives/controllers. It wasn't happening, but I was successful installing on a separate partition, dual boot with Windows. 
I'm quite happy now to be able to mount the failed RAID5 volumes and access my data. Ubuntu has saved me there, as Synology's tech support was of no help, and their only solution was to purchase another Synology device. Luckily BTRFS is more robust than their crappy hardware, and my drives are still readable. 

I watched several videos on using rsync and it seemed rather simple, until I attempted to change into the source directory of the folders that need to be copied. I just couldn't do it. The mounted RAID volume using mdadm looks like this; 
admin:///media/s7/1.42.6-24922/Video/-%20TV%20-
But using the command cd \media/s7/1.42.6-24922/Video/-%20TV%20- only takes me to /media/s7/1.42.6-24922/Video 
and I can't figure out how to get into the TV directory.

Anyway, 3hrs remaining until I'm done copying all the contents I need for now. It will probably take me that long (if not longer) to mess around in terminal in angst. But I would still love to know, why Ubuntu prompts for authentication so many times during the copying phase? And why 'Files' doesn't abide by 'Open as Administrator' as Windows would?

---

### Post by TheFu on 2023-01-30
> **ajnanyc said:**
> I don't think there's a perfect OS out there, and I've had my fair share of frustration with Win/OSX. But Ubuntu is on another level. The nice looking GUI gives you a false sense of confidence, until you soon realize it's superficial and there's a really steep learning curve to delve any deeper. It's a pity, cause it seems like a powerful Universal OS to learn.
 
I'm lucky to have gotten this far, after several failed attempts at trying to run on a VM with attached drives/controllers. It wasn't happening, but I was successful installing on a separate partition, dual boot with Windows. 
I'm quite happy now to be able to mount the failed RAID5 volumes and access my data. Ubuntu has saved me there, as Synology's tech support was of no help, and their only solution was to purchase another Synology device. Luckily BTRFS is more robust than their crappy hardware, and my drives are still readable. 

I watched several videos on using rsync and it seemed rather simple, until I attempted to change into the source directory of the folders that need to be copied. I just couldn't do it. The mounted RAID volume using mdadm looks like this; 
admin:///media/s7/1.42.6-24922/Video/-%20TV%20-
But using the command cd \media/s7/1.42.6-24922/Video/-%20TV%20- only takes me to /media/s7/1.42.6-24922/Video 
and I can't figure out how to get into the TV directory.

Anyway, 3hrs remaining until I'm done copying all the contents I need for now. It will probably take me that long (if not longer) to mess around in terminal in angst. But I would still love to know, why Ubuntu prompts for authentication so many times during the copying phase? And why 'Files' doesn't abide by 'Open as Administrator' as Windows would?

a) I didn't realize you hasn't pulled the drives and connected them directly to an Ubuntu system.  

b) btrfs has some significant failure modes when more than 1 disk is involved. [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)  

c) File paths and network paths are different from MS-Windows.  Pretty much anywhere you see a \, in every other OS, you should be using a / instead.  In fact, you can use a / on MS-Windows too.  It has been that way since at least 1993 - I worked as a cross-platform C++ developer then. We supported 12 platforms, including MacOS and Windows-whatever (all 32-bit versions), along with 10 Unixen.

d) Rsync doesn't know anything about samba, so you'll never get that working.  If you setup a CIFS mount to make the remote files appear as local storage on Ubuntu, then you can use rsync ... though only 1 userid would likely work. BTW, sudo doesn't work across network file mounts. The local Unix/Linux 'root' userid gets dropped to a 'nobody' account on any remote storage. It's a security thing. I bet it could be overridden, but since I've never wanted/needed that in 30 yrs as an admin, I don't know how.

OTOH, if your NAS supports NFS or rsync natively, either can be used.  Some NAS systems have an rsync server built-in.  I think Synology supports NFS. Yep.  It appears that rsync is also a service that can be enabled: [https://kb.synology.com/en-us/DSM/help/DSM/AdminCenter/file_rsync](https://kb.synology.com/en-us/DSM/help/DSM/AdminCenter/file_rsync)  I didn't read that link. It is empty when I follow it and I'm not going to enable javascript.  I'd also enable sshd on the NAS. Then you can use normal ssh authentication.

rsync -avz {SOURCE} {TARGET}
The {SOURCE} and  {TARGET} parameters can be local or remote.  They would take the form of
userid@IP:{directory}/

So, to pull files off the a remote system, I'd use something like
```
rsync -avz admin@192.168.23.67/path/to/files/  /mnt/backup/files/
```
Rsync has a specific meaning with the trailing / in the source and target.  The files written to /mnt/back/files/ would be owned by the local userid. That directory needs to pre-exist and the local userid needs to have write permissions to it.  The -avz options say to keep timestamps, groups, owners and permissions (as much as allowed), be 1st level verbose and use compression for the file transfers.  The group, owners and permissions will be limited if a regular userid is used.  Normal Unix permissions control that and there's no way around it, except to run as root/sudo.  For someone new, sudo can be a curse and more dangerous than they understand.

If you use rsync and don't want to read the manpage for it (which is quite excellent), then there must be 500 websites with "Top 10 Rsync Examples" to make it easy, if my trivial example doesn't help.

---

### Post by ajnanyc on 2023-01-31
Thank you for your assistance. I am officially done with transferring and onto restoring my NAS. I have also learned something new from all this. Hopefully your knowledge will help others that stumble with this issue as I did. Thanks again!

---

### Post by ActionParsnip on 2023-02-01
Is there no backup of the data? If not, why not?

---

### Post by ajnanyc on 2023-02-01
There was a backup of essential files. The remaining files that I  restored were videos, totaling 30TB. Quite a large sum to be backing up  for non critical data. Synology hardware is really sensitive to power  outages, as I've experienced several incidences of RAID failures in the  past. I learned from my previous mistakes and run a PSU to mitigate such  problems. But as Murphy's law would have it, the one time I needed the  PSU to work, the battery needed replacement and failed.

---

