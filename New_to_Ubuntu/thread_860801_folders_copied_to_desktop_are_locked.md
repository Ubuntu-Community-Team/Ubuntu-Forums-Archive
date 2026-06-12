---
title: "folders copied to desktop are locked"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by shredfitz on 2008-07-15
I have a cd with several folders of music files. I copied the folders from the cd to my desktop. Now, each folder has a padlock icon over the folder and I am unable to access any of the folders. 

Why are the permissions set this way? I am logged in as the same user who was able to copy them to my hard drive from the cd. How do I change them and prevent this from happening next time?

Thanks.

---

### Post by Mongoose.wa on 2008-07-15
Try this:

1. Open up a Terminal and type: sudo nautilus /home/**your username here**/Desktop
2. Right-click the folder with the padlock.
3. Go to the Permissions tab.
4. Check the settings to make sure you (as a normal user) have access to create and delete the files.

---

### Post by nowshining on 2008-07-15
in a terminal do the following & try again:
(ur pw won't show as you type & change username to your username)

```
sudo chown -R username:username /home/username/
```

---

### Post by Yuki_Nagato on 2008-07-15
> **Mongoose.wa said:**
> Try this:

1. Open up a Terminal and type: sudo nautilus /home/**your username here**/Desktop
2. Right-click the folder with the padlock.
3. Go to the Permissions tab.
4. Check the settings to make sure you (as a normal user) have access to create and delete the files.

If that does not work for some reason, try "gksudo" instead of plain old "sudo".

---

### Post by mc4man on 2008-07-15
> How do I change them and prevent this from happening next time?you really can't prevent this (maybe it'll be fixed, maybe not)
What i do now is copy to a holding folder and change all tha files, folders at once.
[http://ubuntuforums.org/showthread.php?p=5259083#post5259083](http://ubuntuforums.org/showthread.php?p=5259083#post5259083)

---

