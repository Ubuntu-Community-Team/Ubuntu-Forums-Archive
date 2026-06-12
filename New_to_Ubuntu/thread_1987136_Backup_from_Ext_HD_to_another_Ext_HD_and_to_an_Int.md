---
title: "Backup from Ext HD to another Ext HD and to an Internal Computer HD"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by wstay on 2012-05-26
Is there a Backup tool/software/program to back-up data from one External Hard-Disk-(A) to another External Hard-Disk-(B) and to an Internal Computer Hard-Disk-(C), so that any changes in Hard-Disk-(A) are reflected in (B) and (C) when doing backup from time to time.

---

### Post by mapes12 on 2012-05-26
Sounds as if you are trying to configure some kind of RAID set up. Google **Ubuntu Raid Software** for loads of advice.

---

### Post by Ghost_Mazal on 2012-05-26
Look into rsync.

You could create an rsync script with a command to backup from A to B and a 2nd command to backup from A to C.
Then you can either run the script manually from time to time as you mention , or schedule it in crontab.

---

### Post by wstay on 2012-05-26
I think 'Backup' is such a big and complicated thing.

First, do we need different Backup Tools for different backup like say system files, pictures, movies, etc, etc. Can we just backup everything in one go?

Secondly, in my example above, I find that I cannot use my Hd-A (External HD) to be my original copy of my Backup. When I use HD-A as an Internal HD on my Laptop (to backup data files not system files) I can use it as an original copy of my Backup. Can we configure HD-A to be use as the original Backup copy when I use it as an external HD?

---

### Post by wstay on 2012-05-28
> **Ghost_Mazal said:**
> Look into rsync.
You could create an rsync script with a command to backup from A to B and a 2nd command to backup from A to C.
Then you can either run the script manually from time to time as you mention , or schedule it in crontab.

How do I create an rsync script.
Please help.

---

### Post by Ghost_Mazal on 2012-05-30
> **wstay said:**
> How do I create an rsync script.
Please help.

An example of a very plain one:

Use a text editor and add these lines:

```
#!/bin/bash
rsync -av /path/to/source1/ /path/to/destination1
rsync -av /path/to/source2/ /path/to/destination2

```Save the file with a name you like , for example backup.sh

Make it executable with

```
chmod +x backup.sh

```Now the file can be executed. It is as simple as that.
Rsync has many advanced switches and options , that is just a basic one.
Use

```
man rsync

```to see all options.

Grsync is also an option , that is a gui front-end for rsync

---

