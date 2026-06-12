---
title: "HOWTO: Local shared folder"
date: 2006-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by DrBair on 2006-06-16
**_Introduction:_**
I've seen some references to this across the boards, but never much of an official how-to for beginners.  I'll try to explain how to set up a directory that can be easily accessed and written by all users on the system. I'll also try to keep this as graphical as possible. However if you are wishing to learn more about the command line, I encourage you to investigate ACLs (Access Control Lists) and try this on your own.

For this guide, I will be assuming you are using a recent version of KDE, and an ACL compatible filesystem (the default filesystem is).

**_Packages:_**
Fire up Adept and find a package simply named 'acl'. Install this package.

**_Enabling ACLs:_**
To use ACLs, we need a special mount option for the drive you wish to place the shared directory on. 

1. Go to the System Settings panel. 
2. Select Disks and Filesystems. 
3. Select Administrator Mode and enter your password.
4. Now, right click the partition you want to add the directory in, and select modify.
5. Select Advanced in the new window that comes up.
6. In the options box, add a comma after the last value and add the option 'acl' at the end. Press OK.
7. It will probably now through 2 errors, one that it can't umount the drive, and another because it can't mount it. That's OK, the drive is in use and this is expected.

We're almost there. At this point we have two options, either reboot the system to apply the new options, or bring up a konsole to remount the partition.

For the brave, use this command in the terminal window:
```
sudo mount /dev/foo -o remount
```

That will remount drive foo, which is the partition we modified prior.

Now with the rebooters rejoining us, we're ready to move on to the next step.

**_Making the directory:_**
Open up the run dialog from the KMenu and type in this line:
```
kdesu konqueror /home
```

CAREFUL! This will open konqueror with root permissions, if you tell it to delete something it WILL delete it. 

1. Make a new directory here, name it pub (or share, or something else of your liking). 
2. Right click and select properties for this new folder.
3. Select 'Advanced Permissions' under the permissions tab.

Here is where the magic happens. 
1. Click 'Add Entry'
2. Select the 'Default for new files in this directory' checkbox.

Now you have some choices. If you want to add permissions per user, select 'Named User' and pick the user name to modify permissions for.  If you want to add permissions per group, do that. You can go through this dialog multiple times to add additional users or groups to the list. After adding everyone, you can modify their permissions to r(ead), w(rite), and e(x)exute files.
Personally, I gave the 'users' group full run of the shared directory.

That's all! Your directory and all of its new contents should now be readable and writable by whoever you selected. No more 'chmod'ing!

**_Gotchas:_**
OK, now for a few potential drawbacks to think about.

1. OK, this new directory thing is great. Mom, Dad, and little Jimmy can now put all of their family stuff in one folder and everyone can access and modify the data. Now suppose little Jimmy here downloads and runs a shell script which deletes EVERYTHING he has write access to. Mom and Dad will not be thrilled when the public directory is nuked. Carefully chose who has write access to this directory, and back things up.

2. AFAIK, this will not be accessible over SFTP connections. It will just give you plain old permissions and you'll be back to where you started. Samba shares can be made to use ACLs, but that is beyond the scope of this document.

**_Why not chmod 777?:_**
Good question. Chmodding a directory will change the permissions for the directory (good) but it will not affect the permissions of files added in the future (bad). That is why I went the path of ACLs. Take a look at this for example.

```

ryan@Pascal:/home$ sudo mkdir pub
ryan@Pascal:/home$ sudo chmod 1777 pub/ -R
ryan@Pascal:/home$ cd pub

```

So now we are in our publically writable directory, now to test it out.

```

ryan@Pascal:/home/pub$ touch testfile
ryan@Pascal:/home/pub$ ls -l
total 0
-rw-r--r-- 1 ryan ryan 0 2006-06-16 09:47 testfile
ryan@Pascal:/home/pub$

```

Uh oh. That's not what we are after. Although I was able to create a new file, testfile, looking at the permissions reveals that it is only writable by the owner. To keep things writable would require constantly using the chmod command to keep the permissions world accessible. 


**_Disclamer:_**
I'm not responsible for any damages that occur while following these steps. Don't yell at me if you nuke your computer/data/dog etc doing this.

Feedback welcome!

---

### Post by Owdy on 2006-11-14
Beatiful! Thanks!

---

### Post by sd_smoker on 2007-12-24
I realize this is quite old, but it is exactly what I'm looking for! Only problem is that I'm using GNOME rather than KDE. As I complete newbie I'm not sure how much would be lost in translation if I were to follow these steps in my environment (i.e. just replace "kdesu" with "sudo", etc.). Anyone with a little more knowledge on the matter care to comment?

---

