---
title: "Help changing file permissions"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by TaintedBllack on 2008-07-05
All my music and each containing folder is set only to have root permissions. When I try to change the permissions (yes I am using sudo) it will only change the permissions for one file at a time. I tried changing the folder permissions and clicked apply permissions to enclosed files.. but that isn't working.

Please help

---

### Post by aysiu on 2008-07-05
Is this on your Ubuntu drive? Or is this on an external drive that's NTFS or FAT32?

---

### Post by ghostdog74 on 2008-07-05
use the command line dude, you are on linux :)
```

chmod -R u+x *.mp3 #for example

```
look up the man page for more info

---

### Post by ChameleonDave on 2008-07-05
> **TaintedBllack said:**
> All my music and each containing folder is set only to have root permissions. When I try to change the permissions (yes I am using sudo) it will only change the permissions for one file at a time. I tried changing the folder permissions and clicked apply permissions to enclosed files.. but that isn't working.

Please help

Let's say your music is in a directory called "Music" on your desktop, and your user name is "tainted".

```
sudo chown -R  tainted  ~/Desktop/Music
```

...will make you the owner of those files.

---

### Post by aktiwers on 2008-07-05
Or change them like this:
```
sudo chown -R **USERNAME:USERNAME** /Path/to/folder/
```

Where you replace USERNAME with your username and /path/to/folder/ with the path to your folder.

---

### Post by ghostdog74 on 2008-07-05
> **ChameleonDave said:**
> Let's say your music is in a directory called "Music" on your desktop, and your user name is "tainted".

```
sudo chown -R  tainted  ~/Desktop/Music
```

...will make you the owner of those files.
if i didn't see wrongly, OP indicates changing permissions, not owner.

---

### Post by aktiwers on 2008-07-05
Ohh true..  sorry ignore my post then.

Then this command would be better
```
sudo chmod 777 -R /path/to/folder/
```

---

### Post by aysiu on 2008-07-05
All of this *chmod* and *chown* stuff will work only if it's on a Linux drive or partition.

If it's external media (that's usually FAT16 or FAT32), those commands are all for naught.

That's why I asked earlier what filesystem was used.

---

### Post by ChameleonDave on 2008-07-05
> **ghostdog74 said:**
> if i didn't see wrongly, OP indicates changing permissions, not owner.

Yes, but you have to read people's words through the filter of n00bishness.  He said "permissions" but probably meant ownership.  Someone else had already indicated how to use *chmod*, so I indicated how to use *chown*.

---

### Post by ghostdog74 on 2008-07-05
> **aysiu said:**
> All of this *chmod* and *chown* stuff will work only if it's on a Linux drive or partition.

If it's external media (that's usually FAT16 or FAT32), those commands are all for naught.

That's why I asked earlier what filesystem was used.

OP indicates he can change one file at a time, or did i misread something?

---

### Post by phillipi on 2008-07-08
How would I go about changing the permissions on a FAT16, FAT 32, or NTFS file system.  I tried getting ntfsconfig but the package could not be found. You are right using chown and chmod were ineffective.  It still reads "read only file system"

[QUOTE=aysiu;5322885]All of this *chmod* and *chown* stuff will work only if it's on a Linux drive or partition.

If it's external media (that's usually FAT16 or FAT32), those commands are all for naught.

That's why I asked earlier what filesystem was used.[/QUOTE

---

### Post by ChameleonDave on 2008-07-08
> **phillipi said:**
> How would I go about changing the permissions on a FAT16, FAT 32, or NTFS file system.  I tried getting ntfsconfig but the package could not be found. You are right using chown and chmod were ineffective.  It still reads "read only file system"

I believe that FAT systems simply are too primitive to support permissions for individual files.  You have to state in your fstab file what permissions all files on the partition are to have.

I thought that NTFS was the same, but maybe it isn't.

To mess with NTFS partitions, install software with the following command:

```

sudo apt-get install  ntfs-3g  ntfs-config  ntfsprogs

```

P.S. Plug in your drive and post the output of these commands:

```

cat /etc/fstab
sudo blkid

```

---

### Post by epidemiks on 2008-09-23
I have a similar problem with a 40Gb mp3 collection on an NTFS drive.
Some files I am able to rename/change id tags etc, some not..
what is the right chmod option to use?

---

### Post by kylebridge on 2008-09-23
Here's the command I used and it worked, for a while...

sudo chown -hR username /home/server/Public/Calendars

It changes username to owner of the folder, and all of the files contained, but as soon as a windows user accesses or saves one of the shared files, the owner changes back to "nobody"  Is there any way I can permanently change the owner?  I'm sharing about 3 dozen files in a Windows workgroup, and can't have these files become unavailable to the users.

---

