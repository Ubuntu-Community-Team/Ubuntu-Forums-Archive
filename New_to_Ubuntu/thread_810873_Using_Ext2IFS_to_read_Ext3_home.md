---
title: "Using Ext2IFS to read Ext3 /home"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Philoserine on 2008-05-28
Hello all,

I am dual-booting XP and Ubuntu with an NTFS partition for Windows, an Ext3 partition for Ubuntu / and a large Ext3 partition for Ubuntu /home.  From these forums, I learned about FS-driver and downloaded and installed it on Windows.  
Now my Ext3 partitions are visible through Windows, but not accessible:  A window pops up saying my Ext3s are not formatted, and won't open the files.  
I was planning on storing all my music, documents, etc on the /home.  Is there something else I should be doing to get Ext2IFS to work?  I've read through the FS-driver FAQ and other sites, but still don't know where to go from here.

Thank you!

---

### Post by louieb on 2008-05-28
Have you gone into the control panel and assigned a drive letter to your Linux /home partition?

---

### Post by Philoserine on 2008-05-28
Yes, I assigned letter drives to both the /home and the /swap, as promped by the program.  So now those letters show up with the drives in the My Computer window, but won't open.

---

### Post by Philoserine on 2008-05-28
Also, I looked into SAMBA as an alternative to the FS-driver program.  It seemed more complicated, would you suggest that instead?  Would I need the whole package, or just smbfs?

---

### Post by Oldsoldier2003 on 2008-05-28
> **Philoserine said:**
> Also, I looked into SAMBA as an alternative to the FS-driver program.  It seemed more complicated, would you suggest that instead?  Would I need the whole package, or just smbfs?

Samba wont help if you are dual booting. I would suggest that if you have files you want to share beteen your windows install and your ubuntu install, make a ntfs partition and keep your shared files there. Do not under any circumstances try to make you /home directory on a NTFS partition because it will wreck your Ubuntu installation (you won't be able to log in)

---

### Post by Philoserine on 2008-05-28
So then I would have a smaller Ext3 /home partition, an Ext3 / partition, and a larger NTFS /share partition.  Would I run into problems with the four-primary-partition limit?  Or should I make the /share a logical partition?

---

### Post by Oldsoldier2003 on 2008-05-28
> **Philoserine said:**
> So then I would have a smaller Ext3 /home partition, an Ext3 / partition, and a larger NTFS /share partition.  Would I run into problems with the four-primary-partition limit?  Or should I make the /share a logical partition?

what does your partition table look like now?

```
sudo fdisk -l
```

from there you can figure out what you want to do. Juggling partitions can be a tricky process sometimes, depending on the layout and whether or not you are willing to just nuke and restore...

---

### Post by Philoserine on 2008-05-28
My partition table is currently as follows:

25GB NTFS /windows, 110GB Ext3 /home, 20GB Ext3 Ubuntu /, 5GB /swap

I got the idea for this configuration from the psychocat partitioning page-- it was really helpful, so I was hoping to keep it if the FS-driver program was going to work, but I'm open to anything.

---

### Post by louieb on 2008-05-28
Hum never had a problem with it. Are you sure /home is formatted with the ext3 file system?  The output from **sudo fdisk -l  **would tell you for sure.

Another program you can try is [Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs") might give it a try just to see if it works or not.

BTW: assigning a drive letter to swap isn't going to do anything. Its not formatted ext3.

---

### Post by doorknob60 on 2008-05-28
This has helped that problem with me before. Just restart into Ubuntu, then from the login screen (or you can log in, doesn't matter), restart and boot in to Windows. It worked for me once :)

---

### Post by Philoserine on 2008-05-28
This worked!  All of my files are accessable, at least for now.  =o)  Thank you so much!

---

### Post by Philoserine on 2008-05-28
I tried the command, and yes, it's Ext3.  Thanks for the heads up on the /swap, I just gave it a letter because the program had a drop-down menu for it.  =o)

---

### Post by pk_rulz on 2011-06-19
> **doorknob60 said:**
> This has helped that problem with me before. Just restart into Ubuntu, then from the login screen (or you can log in, doesn't matter), restart and boot in to Windows. It worked for me once :)

Just for your info ... this works because EXT3 has journaling support and the system probably believes that yout last linux shutdown was not clean ... mounting EXT3 in windows would then lead to inconsistency and hence not mounted ... once you restart the shutdown is clean and problem solved.

---

