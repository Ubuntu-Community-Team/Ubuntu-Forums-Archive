---
title: "ecryptfs filenames"
date: 2011-06-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by free2decide on 2011-06-25
Hello,

After a recent update and reboot, my decrypted files in my home folder have been renamed to ECRYPTFS_FNEK_ENCRYPTED.blah. This makes me sad :(

I can look in the files, the contents are fine, just the names are all messed up.

any ideas?

---

### Post by afv on 2011-06-25
I'm having the exact same problem. :|

---

### Post by jfernyhough on 2011-06-25
Mine has just done the exact same thing... looking into it now.

For others who haven't had this yet, the filenames in ~/.Private are not decrypted in ~/Private but the file contents are.

I have an encrypted Private from when this was first introduced. The only thing I can see that looks related is that mount was updated from 2.17 to 2.19.

I seriously hope it hasn't renamed all of my files, though thankfully I think I have a backup (Wuala is awesome).

--edit
OK, looks like ecryptfs has borked somewhere. Files are safe (I think), but when using
$ sudo ecryptfs-add-passphrase --fnek
then typing in my passphrase I get the error "Error: Your kernel does not support filename encryption", which is a bit odd as it did just before... same kernel (3.0-rc4 mainine build). Going to download 3.0-2 from launchpad and see if that helps.

--edit2
After a bit more searching I can't help but feel this is due to the old style ecryptfs setup (using /home/USER/.ecryptfs) compared to the new style (/home/.ecryptfs/USER)

---

### Post by afv on 2011-06-25
It was the mount:

> 
upgraded: mount (2.17.2-9.1ubuntu4) to 2.19.1-2ubuntu1
installed: libmount1 (2.19.1-2ubuntu1)


Just downgraded to the previous version (amd64: [https://launchpad.net/ubuntu/oneiric/amd64/mount/2.17.2-9.1ubuntu4](https://launchpad.net/ubuntu/oneiric/amd64/mount/2.17.2-9.1ubuntu4)) and purged libmount1, and now the filenames are back, but I have duplicated folders/files (when doing ls), with the same name and inode, example:

> 
 605333 drwxr-xr-x    2 afv  afv   4096 2011-06-25 23:36 Templates
 605333 drwxr-xr-x    2 afv  afv   4096 2011-06-25 23:36 Templates
1079472 drwx------    3 afv  afv   4096 2011-06-25 23:57 .thumbnails
1079472 drwx------    3 afv  afv   4096 2011-06-25 23:57 .thumbnails


nautilus only "sees" the recent/empty ones (auto-created when I logged in during the mount problem). Any hint to solve this?

---

### Post by NCLI on 2011-06-25
This be annoying -_-

Anyone filed a bug yet, or can I have the honor?

---

### Post by jfernyhough on 2011-06-25
The honour is yours. I spent 30 minutes searching before I noticed there were two new posts including a solution. :D

--edit
Hmm... did a ecryptfs-umount-private, downgraded, did ecryptfs-mount-private and still have encrypted filenames... might need a reboot?

---

### Post by afv on 2011-06-25
> **afv said:**
> It was the mount:



Just downgraded to the previous version (amd64: [https://launchpad.net/ubuntu/oneiric/amd64/mount/2.17.2-9.1ubuntu4](https://launchpad.net/ubuntu/oneiric/amd64/mount/2.17.2-9.1ubuntu4)) and purged libmount1, and now the filenames are back, but I have duplicated folders/files (when doing ls), with the same name and inode, example:



nautilus only "sees" the recent/empty ones (auto-created when I logged in during the mount problem). Any hint to solve this?


Removing the duplicated files/folders through nautilus (that were showing just the recent ones) made the originals appear. I killed X (didn't want to try to go through normal logout having just removed the config files in use, that could be rewritten/recreated) and everything seems to be "normal" here by now. Uff! :neutral:

---

### Post by jfernyhough on 2011-06-26
A reboot gave it a poke and now I have filenames back to normal (with mount 2.17).

Fun. :D

---

### Post by firefish5000 on 2011-06-26
I have found that the files created before you fix the problem are quite annoying. all applications i opened are now acting like i just downloaded them (all the ones i used after the upgrade) should i delete the cache file or the files within them that i used??? I am guessing the cache since it seems that everything within the home folder was left alone but I want some reassurance.
<---EDIT--->
Never mind, i just deleted it and it went back to normal. I also deleted my config and the .blank of every application I know I used.
but what other common files should we delete? my default applications have gone back to the 'default' value as well. how would I fix this.
(ex. when i right click a file named 2 or .tc i ususaly get 'open with true crypt' but now it is gone.)
Could we not accommodate to the new style somehow? Perhaps move our encrypted files into the directory its looking in for them?

---

