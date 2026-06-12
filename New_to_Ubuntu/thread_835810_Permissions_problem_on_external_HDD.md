---
title: "Permissions problem on external HDD"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by slibuntu on 2008-06-20
Hi, 
My external HDD won't let me add files to it, or create folders etc.

I mounted it with the following command - ```

sudo mount -t vfat /dev/sdb1 /media/sdb1
```

It mounts and I am able to read and excecute files, ls -l gives ```

drwxr-xr-x 28 root root    32768 1970-01-01 01:00 sdb1

```

Hunky dory, all i need to do is sudo chown slibuntu:slibuntu -R /media/sdb1 right?

Nope, it gives me operation not permitted every time for every file! Any ideas?

---

### Post by sharks on 2008-06-20
then sudo mkdir name-of-the-folder

---

### Post by mamcgrath on 2008-06-20
Hi

I had a problem like this a while back. It has something to do with permissions on a FAT drive. Why are you trying to mount it manually? Does it not mount automatically when you connect it? 
If it is permanently connected you try something like this in your /etc/fstab

 '/dev/sdb1 /media/sdb1 vfat auto,user,uid=1000,gid=1000,exec,rw 0 0

This is assuming your uid and gid is 1000.

---

### Post by oshilig on 2008-06-23
I am having the same problem with an external drive that I cannot change from Read-Only.  

It mounts when I plug it in, I but when I try to change permissions (right click, Properties) it tells me it is Read-Only.

ls -l /media gives

drwx------ 18 silver root   32768 1969-12-31 16:00 LOCAL DISK

Any advice how to change my permissions?

---

### Post by paulderol on 2008-06-23
can you alter the folder permissions inside of the drive? i would reccomend that as at least a temporary workaround. 

If that doesn't work out for you, you might have to reformat the drive...Western Digital puts a bunch of BS on their drives as a "service" which messed up my permissions early in my linux career.

---

### Post by hyper_ch on 2008-06-23
why do you use fat32 drive?

---

### Post by oshilig on 2008-06-23
> **paulderol said:**
> can you alter the folder permissions inside of the drive? i would reccomend that as at least a temporary workaround. 

same problem, error message saying it is read only again.

[/QUOTE]If that doesn't work out for you, you might have to reformat the drive...Western Digital puts a bunch of BS on their drives as a "service" which messed up my permissions early in my linux career.[/QUOTE]

This would blow, there is a lot of data there I don't want to lose.

---

### Post by paulderol on 2008-06-23
i think that if you run the following in the terminal it should repair some of this...
```

sudo chmod a+rw /location/of/drive -R -v
```

this should allow read and write access for everyone.

---

### Post by hyper_ch on 2008-06-23
it's FAT32 - UNIX permissions don't work on it.

---

### Post by vanadium on 2008-06-23
> there is a lot of data there I don't want to lose
then I am sure you have a second drive with a copy of the data anyway.

That said, external USB drives should automatically mount with read/write permissions for the current user: do not put an external drive in /etc/fstab!

The permissions you showed for the mount point indicate that user "silver" would have all rights.

If you are user "silver" and you can still not write, then perhaps there is a problem with the file system: you would need to check the drive and repair it.

To check a fat drive without repairing it:

1) Unmount the drive (right-click the icon on the desktop)
2) Find the device name of your drive: open a terminal using "Applications - Accessories - Terminal", and on the command prompt, type "sudo blkid". You will need to provide your login password (and have user rights).
3) Check the drive with the command "sudo dosfsck /dev/sd?", where you replace /dev/sd? with the actual device name found under 2)

If in doubt, post the output of the commands here (Select in terminal using mouse, then "Edit - Copy) so we can continue to help.

Sorry if these instructions are too basic: this is the Absolute beginners forum.

---

### Post by slibuntu on 2008-06-23
I'll try that, thanks, i've been meaning to reformat it, but its mt dumping ground, everything is on there, and annoyingly, it doesn't auto mount!

---

