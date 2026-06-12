---
title: "How to make backups"
date: 2019-01-31
forum: New to Ubuntu
---

### Post by matuskm on 2019-01-31
Hi,
how to make backups on the Ubuntu but in to NAS over the network? I have more HDD for backup and backup automatically start over the night. 

How on the this ???

Thanks

---

### Post by NM5TF on 2019-01-31
you might try Deja Dup......

go here  [https://wiki.gnome.org/Apps/DejaDup](https://wiki.gnome.org/Apps/DejaDup)

go here for a tutorial on usage to get you started  [https://www.linux.com/learn/total-system-backup-and-recall-deja-dup%20](https://www.linux.com/learn/total-system-backup-and-recall-deja-dup%20)

tommy

---

### Post by TheFu on 2019-01-31
I have a few questions.

Which file system does the NAS have?  
Why?  NTFS storage requires that the file permissions be stored inside separate metadata files. Many backup tools expect this data to be stored as part of the backup files.

Does it support Unix permissions or not?  
Why?  For Linux/Unix, the owner, group, permissions, ACLs are about 50% of the backup information needed. Without those, restoring a system backup is impossible.

Do you want image-based backups or file-based?  
Why?  Images are harder to make, but easier to restore to an identical HDD.  If the replacement HDD is smaller, then the image-based backups won't work. Generally, image-based backups require downtime and booting from alternate media. There is an exception, but on if the system was setup with LVM and room for snapshots was reserved at install time.
File-based backups will use differential data changes, differential storage, and are generally much faster. Depending on the services running, this type of backup can be taken while the server keeps running.  With LVM, zero downtime.  But restores are a little harder until you get good at it.

Do you want versioned backups?  
Why? File corruption, crypto-locker, ... sometimes we don't see issues for months.  With versioned backups, we can figure out when the attack happened, perhaps. 

Do you need 3 backups or 180?  
Why?  This is about risk factors and risk mitigation.  Once a week backup is probably fine for a home, but totally unacceptable for a business.  If a system is constantly under attack or at risk of many attacks, like an email gateway, then having 6 months of backups would be smart.

How much storage is available for these backups?
Why?  If you only have storage for 1 backup, then anything which uses more is a waste of time.

Which OS does the NAS run? Do you have access to run Unix programs on it?
Why?  Using networked storage mounted directly to the systems being attacked for backups is a terrible idea since malware and cyptolocker programs will also target any connected storage. Samba/CIFS/NFS/DFS and other networked file mount methods should be avoided for backups.
Using a backup tool with client-server architecture is a way to mitigate the crypto-locker problem - something that works over ssh is best.  However, these can be "push" or "pull" connections.  "Push" requires that the client have credentials into the NAS/Server, so if the client machine has been hacked, it is possible to gain access to the server/NAS and corrupt all files on it.  With "Pull" backups, only the backup server/NAS needs credentials into each client to perform the backups.  Of course, if the NAS has access to the internet, then that adds risks.  If the NAS is on a backup network, separate from most public interfaces, the risks are greatly reduced.  If the NAS is behind a firewall that only allows outbound access to the client machines, all the better for security.

Do you need a GUI?
Why?  The scheduling system for Unix, cron, generally cannot run GUI programs. Depending on the OS release, **aptik** might be the GUI you seek. Just depends on if the system is a typical, single-user, desktop or not. It isn't very efficient, but it is easy to use.

What is the plan for off-site backups?
Why?  Backups need to be local + remote. If you don't have 3 copies of the files, then you don't have a backup.

TL;DR
* **duplicity**
* **rdiff-backup**
* **Back-In-Time**
* **fsarchiver**
* **clonezilla**

There are at least 50 different threads in these forums about doing backup. Best to do a little reading, see what makes sense.

---

### Post by matuskm on 2019-01-31
Thank you for answer but what do you recommend if my data is about 2TB and it will grow. The Internet that I have is LTE with 400GB per month.

thank you very nice and sorry for my english

---

### Post by SeijiSensei on 2019-01-31
I use rsync and write backups to a 4 TB USB external disk.

---

### Post by matuskm on 2019-01-31
Use external disk and e.g. NAS at once? And some security? I have on the linux server only ESET this all security... Have you some more best idea?

Thanks for all ideas and answers :).

---

### Post by mastablasta on 2019-02-01
Adding Duplicati and Areca to the backup programs list. both are easy to use and to setup for automatic backup to remote destination or local folder.

data on LAN is not transfered via internet. if you do not have a NAS external drive will do the job. 

if you have your own nas/server and would like to backup over internet you need to harden it.

if you want to backup only the changes, search for those with partial/delta backup options.

---

### Post by TheFu on 2019-02-01
> **matuskm said:**
> Thank you for answer but what do you recommend if my data is about 2TB and it will grow. The Internet that I have is LTE with 400GB per month.

thank you very nice and sorry for my english

I can't recommend anything without the other questions being answered. Sorry.
If you don't know the answer, that is also an answer which tells us important information. We can help you figure it out or make the most likely guess.  People do weird things to their storage all the time, so it is best not to assume anything.

---

