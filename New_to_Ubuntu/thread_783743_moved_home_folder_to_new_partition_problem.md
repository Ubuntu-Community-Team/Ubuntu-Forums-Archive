---
title: "moved home folder to new partition problem"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by baddnady23 on 2008-05-06
Hi all, 

I moved my home folder to a new 500gb partition today on /dev/sdb4.  All was workin fine until i rebooted and now it says that user's HOME/.dmrc file is being ignored. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.  I reconfigured fstab to mount this on start up, but have no luck.  the fstab file "reads /dev/sdb4/home ext3 nodev,nosuid 0 2" in regards to this partition.  ANy ideas?

---

### Post by laffinet on 2008-05-06
I had this problem at some stage myself.

The issue is not mounting the partition but the permissions on your home folder and the files in it (the HOME/.dmrc file in particular).

So what you need to do is change ownership via chown and permissions of that file (and preferably the whole home folder) via chmod to yourself.

---

### Post by baddnady23 on 2008-05-06
how would i change the permissions for the entire directory?

---

### Post by amohanty on 2008-05-06
Try the following:
1. change the nodev,nosuid to defaults. They really don't make a difference unless you intend to use your home partition in unusual ways.
2. In the terminal (in recovery mode) change the permissions for your home folder:
sudo chown -R your_username:your_username /home/your_username

In the recovery console you should not need to do the sudo, but in case you are doing this from a live cd that may be required.

hth
AM

---

### Post by laffinet on 2008-05-06
Start by changing the owner of your home folder to the respective user with sudo:

```
sudo chown -R *username*:*group* /home/*username*
```

Then change the permissions for user and group

```
sudo chmod -R 775 /home/*username*
```

That should fix it.

---

### Post by baddnady23 on 2008-05-06
ok thank you. real quick, i only had the command line available right now and i cant check what group my default user, andrew, is in.

---

### Post by laffinet on 2008-05-06
```
groups [username]
```

will give you the groups you belong to. I think by default there will be a group with the same name as the user which is what you should use for the procedure described earlier.

---

### Post by amohanty on 2008-05-06
> **laffinet said:**
> Start by changing the owner of your home folder to the respective user with sudo:

```
sudo chmod -R *username*:*group* /home/*username*
```

Then change the permissions for user and group

```
sudo chmod -R 775 /home/*username*
```

That should fix it.

The first one is **chown** not **chmod**. I made the same mistake :)

am

---

### Post by baddnady23 on 2008-05-06
pure geniuses.  thanks :-)

---

### Post by laffinet on 2008-05-06
You're welcome. Sorry for the chown <-> chmod mix up. I'll edit my post in case someone else wants to follow this.

---

### Post by baddnady23 on 2008-05-06
ok one more quick question, everything else seems to be working again, but now when i want to unmount my windows partition on /dev/sda1, it says only root can do that, but i used to be able to unmount it before also.

---

### Post by laffinet on 2008-05-06
Sorry, I'm not experienced enough to help with that problem. Try searching the forum or google it ("unmount root only" or something like that).

Or maybe someone else will come to the rescue ?!

---

### Post by amohanty on 2008-05-06
well if it was mounted via fstab, only root can unmount it. I am not entirely sure what gvfs does. You can use the pmount tool too:
1. remove the relevant entry from /etc/fstab 
2. install pmount
sudo apt-get install pmount
3. Use it
pmount -t ntfs /dev/sda1 windows
will mount it in /media/windows - you dont need to create the folder.
pumount /dev/sda1 will unmount it.

OR

add the words **user,noauto** to the options section. This will not mount the drive by default and allow user mounts. 

HTH
AM

---

### Post by subzero316 on 2008-05-06
> **baddnady23 said:**
> ok one more quick question, everything else seems to be working again, but now when i want to unmount my windows partition on /dev/sda1, it says only root can do that, but i used to be able to unmount it before also.

then do it as root,

```

sudo umount
```

---

### Post by baddnady23 on 2008-05-08
Thank you, it all works beautifully now :-)

---

### Post by Tatty on 2008-05-08
The only (possible) problem with chowning your entire /home is that there may be some files in there which are supposed to be owned by root...  This may or may not cause problems.

Do you still have a full backup of your old home folder somewhere?  If not, dont worry about it, it wil probably be fine.  But if you do have a backup, cd to it then run ```
ls -lR | grep root
```

"ls -lR" will recursively list all files in the directories along with permission information.  Grep will then give you only those lines which contain "root", this will include anything owned by root, or anything with "root" in the filename.

You can then manualy chown the files back to root in your new home directory.  If you arent sure which directory they are in you can use ```
locate *filename*
```

---

### Post by tayhe on 2008-05-08
to Tatty:
there will be,in default, no entry owned by root,so don't worry about it.:guitar:

---

