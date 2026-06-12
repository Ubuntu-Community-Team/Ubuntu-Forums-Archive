---
title: "New to Ubuntu and having issues"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by cirathorn on 2008-07-04
(Imagine that! A Newb with questions!)

Okay so first off I think I am expecting more and am still stuck in a "Windows" Mentality. I am certified A+, MCSE, MCSA, basic networking, and Lefthand. So I know my way around Windows Desktops and servers.

So I figured lets try out Ubuntu/ Linux. I grabbed 8.04 and installed it on a box with 6 gb RAMM, and 4x 320gb HD's. My intention was using it as a file server/ Media center as I was told this was one of the easiest things to do/ learn.

So right out of the box I loved the install process, I figured out the restricted driver deal for my Nvidia 8800gt card and thats pretty much where the fun ended.

The other 3 HD's are acting odd. I grabbed a "Partition Editor off the "Add/Remove -> system" section of Applications. I used to to format the other drives into an EST3 format, but the system:
A) Won't automount them, and 
B) won't allow me to do anything once I do mount them.

Also is there anyway to have it STOP asking me for my password once I login and try to work? The password needing really reminds me of Vista, but I know the registry editting needed to stop Vista from asking.

---

### Post by jombeewoof on 2008-07-04
Auto mounting partitions

you need to add them to /etc/fstab
the basic layout of that file is 
```

device    mountpoint   filesystem  options 
example

/dev/sdb1   /data    ext3   defaults  0  0

```

I don't remember what the numbers are for at the end, Ijust always use 0  0



Ubuntu's version of UAC
This is actually where Vista got the idea, if you really don't want to have to provide your password when doing admin tasks you can log in as root. 

From gnome go to system > administration > login 
Click the security tab and check "allow local admin"

It's a really bad idea to log in as root, you could inadvertently damage something blah blah blah. 
You're just learning, so you're bound to screw something up anyway, it's just a bad habit to get into.

---

### Post by Martje_001 on 2008-07-04
> **cirathorn said:**
> Also is there anyway to have it STOP asking me for my password once I login and try to work? The password needing really reminds me of Vista, but I know the registry editting needed to stop Vista from asking.
I'm sorry if I'm sounding a bit harsh, but: **learn to live with it**. It's far more secure, than disabling the password!

You can, it's your choise, however disable your password. See [this](http://ubuntuforums.org/showpost.php?p=364040&postcount=3) or google for 'disable sudo'.

---

### Post by hyper_ch on 2008-07-04
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by cirathorn on 2008-07-04
What about the Permissioning issue with each drive?

---

### Post by Martje_001 on 2008-07-04
> **cirathorn said:**
> What about the Permissioning issue with each drive?
That you can do with fstab as described above. Change **defaults** to **defaults,user,users,rw**

Good luck!

Or install Ubuntu again and point (when installing) out where everything needs to be mounted.

---

### Post by Canis familiaris on 2008-07-04
> **cirathorn said:**
> 


Also is there anyway to have it STOP asking me for my password once I login and try to work? The password needing really reminds me of Vista, but I know the registry editting needed to stop Vista from asking.
Learn to live with it. It is an ADVANTAGE of Ubuntu.
If you meant Ubuntu not to prompt for password at login:

**System->Administration->Login Window**

Go to security tab and enable automatic login and select the user

---

### Post by Martje_001 on 2008-07-04
> **Anurag_panda said:**
> **System->Administration->Login Window**

Go to security tab and enable automatic login and select the user
I don't thing that he means that. That's called autologin.

---

### Post by Canis familiaris on 2008-07-04
> **Martje_001 said:**
> I don't thing that he means that. That's called autologin.
Yes I corrected my post

---

### Post by jombeewoof on 2008-07-04
> **cirathorn said:**
> What about the Permissioning issue with each drive?

you need to change the owner of the drives. I'm the only user on my server so I make my user account own them. Then I don't have any issues with ftp, samba, ushare and permissions issues at all because my user account owns it all. 
anyway here is what I use
```

sudo chown -R tom:tom /data
```

sudo == run as admin
chown == change owner
-R  == recursive, all subdirectories are parsed
tom:tom == user:group
/data == the directory I'm changing permissions on

---

### Post by The Cog on 2008-07-04
By default the other drives are owned by root. Or at least, the directories where you mount them are owned by root, because you will have been acting as root when you created the mount points.

What permissions to you want to give to those directories? And who do you want to be the owner?

Perhaps set them to being readable/writeable by everyone?
**sudo chmod 777 /media/sda2**
substituting the correct mount point, of course.

---

### Post by DrMelon on 2008-07-04
The main thing to remember is to [SIZE="7"]NEVER DO THIS ONE:[/SIZE]


```

sudo rm -rf /

```

---

### Post by cirathorn on 2008-07-04
Here is what I changed the /etc/fstab to:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=86bf0f81-dff2-49b0-b853-8e9f5b2e0ea8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd5
UUID=a62a30a7-6aa2-4db7-9d99-51306a8439c4 none            swap    sw              0       0
# /dev/sda1    /data        ext3    defaults,user,users,rw    0    0
# /dev/sdb1    /data        ext3    defaults,user,users,rw    0    0
# /dev/sdc1    /data        ext3    defaults,user,users,rw    0    0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
sda1, sdb1, sdc1 are the other drive designations.

Hope this is right, that or I boned up something.

Also I went into the gksudo nautilus and then was able to make a few changes that made life a little easier for me.

---

### Post by hyper_ch on 2008-07-04
> **DrMelon said:**
> The main thing to remember is to NEVER DO THIS ONE:

```

sudo rm -rf /

```

why not?

---

