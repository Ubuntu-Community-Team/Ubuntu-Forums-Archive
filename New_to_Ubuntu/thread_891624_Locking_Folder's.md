---
title: "Locking Folder's"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Pioneer5000 on 2008-08-16
Is there a way to lock a folder by putting a password on it? And i dont mean by removing permissions etc but just simple if you want to enter the folder it will require a password?

---

### Post by Diabolis on 2008-08-16
That is what permissions are for. If you don't give read permissions to other users, you'll be asked for a password every time you try to open it.

What else do you need?

---

### Post by Flyingjester on 2008-08-16
You could give the ownership to another user (maybe a special user you only use for this purpose), and don't give permission to yourself to use it.. so it will prompt for password...

---

### Post by wariskampar on 2008-08-16
How do I make a folder ask for a password everytime someone (including myself) want to open it.

---

### Post by Pioneer5000 on 2008-08-16
> **wariskampar said:**
> How do I make a folder ask for a password everytime someone (including myself) want to open it.

Yes thats what i want to know. Also how do you set permissions anyway to make it ask for password.

---

### Post by Pioneer5000 on 2008-08-17
Cant seem to figure it out so it ask's me for password.

---

### Post by Pioneer5000 on 2008-08-17
No Help?

---

### Post by Diabolis on 2008-08-17
Once you change the permissions of your folder.

Go to this folder in your home folder: **.gnome2/nautilus-scripts**
*the dot at the beginning of the path means that is a hidden folder. To see hidden files press **<Ctrl>h***

In that folder create a file called "open folder" then make it executable.

The content of the file should be something like this:
[PHP]#!/bin/sh

# the -u root option allows you to choose with which user you want to execute the command
gksudo -u root "nautilus --no-desktop --browser $@"[/PHP]

Now, in nautilus, you can right click folders and in the menu you have a option that says **Scripts** where you can select the option "open folder".

---

### Post by t0p on 2008-08-17
I've had a google about, and it would seem there is no simple way to password-protect a folder (except by writing a script to do it).

But Linux offers a very secure alternative - you can password-protect files by symmetrical encryption with **gpg**.

To encrypt a file called **file**, you give the command 
```
gpg -c file
```

You'll be asked to input then confirm a pass phrase.  This will create an encrypted file called **file.gpg**.

Now delete the original file, and what's left is just the encrypted copy of file.

When you want to open file.gpg, you open terminal and give command:

```
gpg file.gpg
```

You'll be asked to type in the pass phrase.  This will unencrypt file.gpg, so you'll have an open copy of file (as well as file.gpg still).

You must remember to delete file when you've finished working with it, if you don't want an unprotected copy lying around.

If you're very paranoid about someone recovering a deleted copy of file from your computer, you could delete the open copies with the command:

```
shred -u file
```

This will delete file in a pretty well secure fashion and should give you some peace of mind.

**gpg -c** is as secure as the pass phrase you use.  So don't use a name, or a word in a dictionary. Mix upper and lower case letters, numbers and symbols like ! and & for the strongest pass phrases.  But make it easy for you to remember!  And don't write it down!

---

### Post by Paqman on 2008-08-17
> **t0p said:**
> 
```
shred -u file
```

This will delete file in a pretty well secure fashion and should give you some peace of mind.


Actually, it won't. Shred works by overwriting the file several times, which won't work on ext3. Check man shred for more info.

I believe scrub is more effective for journalled file systems.

---

### Post by t0p on 2008-08-17
> **Paqman said:**
> Actually, it won't. Shred works by overwriting the file several times, which won't work on ext3. Check man shred for more info.

I believe scrub is more effective for journalled file systems.

*sigh*

From **shred man page**:

>  In the case of ext3 file systems, the  above  disclaimer  applies  (and
       shred  is  thus  of  limited  effectiveness) only in data=journal mode,
       which journals file data in addition to just  metadata.   In  both  the
       data=ordered  (default) and data=writeback modes, shred works as usual.

What the above means, is that shred works fine with ext3 in its default mode.  And, since shred overwrites 25 times, with a mixture of 0s and random data, and most security experts nowadays agree that 3 iterations will make data unrecoverable by most methods thar don't involve an electron microscope, I'd say shred is pretty damn good.

As for **scrub**: that isn't in any of the usual repos.  I've never even heard of it before.

---

### Post by t0p on 2008-08-17
I just remembered... there *is* a way of creating a password-protected directory in ubuntu - it's **cfs**.

What cfs actually does is create encrypted filesystems.  But as such a filesystem can consist of a single directory, this will, by definition, be a password-protected directory!

```
sudo apt-get install cfs
```

If anyone wants to use cfs to encrypt a directory, I'll certainly point you in the right direction! :)

---

### Post by nicedude on 2008-08-17
I just thought everyone should know that while overwritting a file 25 times is obviously more secure. If a file is overwritten with say 0's even one time then that data will not be able to be recovered with any software tools period, at that point the disk will have to be taken apart and the platters examined with an electron microscope to recover readable data that once resided on them. To my knowledge you will have to make the FBI or CIA mad at you to have this sort of forensics performed on your disks as this is highly specialized recovery and regular police etc have no access to such equipment and would have to spend thousands of dollars do have this done for them so unless you are doing something incredibly stupid/evil one overwrite is sufficient to destroy data. Just thought everyone might feel safer if they knew that.

For encrypted partitions you might try cryptkeeper aswell as it is in the repositories and when started puts a padlock on your top menu bar and you can click on that and select new encrypted folder and go from there, once installed it is accessed from Applications -> System Tools -> Cryptkeeper and it is all GUI for ease of use, in case some don't like command line programs this should be easier.

COMMAND TO INSTALL CRYPTKEEPER

sudo apt-get install cryptkeeper

Also encryption will be much safer for your sensitive data then any folder passwords or permission settings as these could easily be defeated with just a live Linux CD and mounting of the disk. Encryption is encryption and will defeat all but the government, and I mean the NSA not the POLICE or FBI as they don't have the super computers for it. I saw a discovery channel program though with the NSA's "thinking machine" can crack encryption such as what we are all discussing in seconds.

Heres a link to you tube so you can see your tax dollars at work :-)
[http://www.youtube.com/watch?v=4VTxyRVmL5c](http://www.youtube.com/watch?v=4VTxyRVmL5c)

And welcome to 1984

Hope this info helps everyone both be safe & sleep at night :-)

---

### Post by pi.boy.travis on 2008-08-17
> **Pioneer5000 said:**
> Yes thats what i want to know. Also how do you set permissions anyway to make it ask for password.

To change a folder's permissions, right click on it, select properties, and then the permissions tab.  The drop down menus there allow you to change permissions.  As for password protection, you are better off encrypting files.  If you need to encrypt multiple files as a whole, you can put them into an archive.

---

### Post by nhasian on 2008-08-17
no one's recommended Truecrypt yet?

[http://www.truecrypt.org]("http://www.truecrypt.org")

I created a 10 gig file as a virtual encrypted disk.  when i mount the virtual encrypted disk i have to supply a password and then its used like a normal folder.  after I unmount the file or shutdown my pc, the folder is no longer accessible.  That's what you were asking for right?  Putting a password on a folder?  :)

---

