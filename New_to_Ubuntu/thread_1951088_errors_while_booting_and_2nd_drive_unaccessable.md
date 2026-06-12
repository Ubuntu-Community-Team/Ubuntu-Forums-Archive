---
title: "errors while booting and 2nd drive unaccessable"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by CarterD13 on 2012-04-01
Hey guys I am having an issue with boot "A error occurred while mounting 0" after I skip that I have another error which states "serious errors with mounting sdb1" 

Here is my fstab
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0 
# / was on /dev/sda1 during installation
UUID=15885993-bac4-44f1-9472-dc4c09ffb39e / ext4 errors=remount-ro 0 1 
# swap was on /dev/sda5 during installation
UUID=4fd873c2-da6c-4179-94c2-907f6241409d none swap 

default 0 0
sw 0 0 

/dev/sdb1 /media/sdb1 ntfs nls=iso8859-1,umask=000 0 2 

This is the blkid
/dev/sda1: UUID="15885993-bac4-44f1-9472-dc4c09ffb39e" TYPE="ext4" 
/dev/sda5: UUID="4fd873c2-da6c-4179-94c2-907f6241409d" TYPE="swap" 
/dev/sdb1: LABEL="Expanded Disk" UUID="1094C4C294C4AB92" TYPE="ntfs"

I am brand new to Ubuntu and have only been using it for a few days. I appreciate the information in here and have attempted a few changes but no luck.

---

### Post by acimi66 on 2012-04-01
Have you installed Gparted, from the software center?

If so, do a print screen and add the pic here.

---

### Post by CarterD13 on 2012-04-01
[IMG]https://dl-web.dropbox.com/get/Screenshot%20at%202012-04-01%2020%3A10%3A58.png?w=cc0862c6[/IMG]
[IMG]https://dl-web.dropbox.com/get/Screenshot%20at%202012-04-01%2020%3A11%3A06.png?w=c530ae35[/IMG]

---

### Post by CarterD13 on 2012-04-02
Here they are

---

### Post by acimi66 on 2012-04-03
I realize this is not what your problem is, and I can't but being a new install you want to consider re-doing your partitioning to ADD a /home so that you keep all your data whilst still being able to re-install the OS.
Just a thought.

Your problem as it is I am not able to help you with. Sorry.

Maybe some more searching of the exact problem.

Good Luck

---

### Post by CarterD13 on 2012-04-05
> **acimi66 said:**
> I realize this is not what your problem is, and I can't but being a new install you want to consider re-doing your partitioning to ADD a /home so that you keep all your data whilst still being able to re-install the OS.
Just a thought.

Your problem as it is I am not able to help you with. Sorry.

Maybe some more searching of the exact problem.

Good Luck

Thanks for the help. I did try to find advice in another forum but no one replied so I did reinstall and backed up using rsync. Seems everything is fine so far just need to update everything again.

---

### Post by Cheesemill on 2012-04-05
> **CarterD13 said:**
> /dev/sdb1 /media/sdb1 ntfs nls=iso8859-1,umask=000 0 2 

I know it's too late now but this line was your problem, the 2 at the end should have been a 0.

A bit of an explanation:
The number in the last column is the PASS option, this defines how Ubuntu will check the disk for errors when it boots. As there is no method of checking NTFS disks available, then anything other than 0 (for don't check the disk) will result in the error you saw.

---

