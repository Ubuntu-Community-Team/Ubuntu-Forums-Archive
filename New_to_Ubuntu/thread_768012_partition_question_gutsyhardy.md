---
title: "partition question gutsy/hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by DSn0wMan on 2008-04-26
I just installed hardy on a spare 20G (sdb) hard drive. I have an 80G (sda) drive with gutsy on it (all one partition).

I was going to make a separate /home on the 80G (sda) drive with my old home directory, then install hardy on the 20G drive. so I would have 20G for / and 80G for /home on hardy. The only problem is that gparted wont shrink my old partition so I can create a separate home.

Any idea how I can turn my old / partition into just a home partition and keep the data in the home directory?

---

### Post by luceerose on 2008-04-26
Are you using gparted from within Hardy or have you tried with the Gparted Live CD ???

---

### Post by DSn0wMan on 2008-04-26
gparted on the Hardy CD, but I have had the same problem with the Gparted live CD.

---

### Post by luceerose on 2008-04-26
Maybe post a couple of screenshots of how your drives show up in gparted.
That might help us see something.

---

### Post by DSn0wMan on 2008-04-26
> **larsenguitars said:**
> Maybe post a couple of screenshots of how your drives show up in gparted.
That might help us see something.
Here is my layout. the /dev/sda1 is my gutsy installation which can go away except I want the home directory.

[IMG]http://www.flickr.com/photos/26021593@N07/[/IMG]

Evidently I don't know how to user flikr or something.

---

### Post by Belak on 2008-04-26
Ok, this may be a little bit complicated because some Gutsy config files may not work with Hardy.

In your Hardy install, mount your Gutsy drive and sun the following command (Where gutsy_mnt is the mounted dir):
gksu nautilus /media/gutsy_mnt

Now, delete everything but the home folder.

Next run the following 2 commands (Once again where gutsy_mnt is the mounted dir):
sudo mv -v /media/gutsy_mnt/home/* /media/gutsy_mnt/
sudo rm -rv /media/gutsy_mnt/home/

Those will copy the stuff in the previous home dir into the root of the drive.

Next, we need to copy the stuff from our current home dir into the Gutsy one (For compatibility I'd reccomend overwriting everything you aren't sure on)
cp -Rvi /home/* /media/gutsy_mnt/

You will need the HD device name to continue.
Run the following command and determine which HD it is based on the device geometry

Now to edit the fstab to make this work.
Run the following command to get an editor up:
gksu gedit /etc/fstab

You will see a line for the root partition that looks something like the following:
UUID=8603bf52-e99c-4056-a86c-812d2a032603 /               ext3    errors=remount-ro 0       1

We just need a line like that for the new home partition. I'd use the following 2 lines (if your HD was /dev/sdb1):
```
# New Home Partition
/dev/sdb1 /home           ext3    defaults        0       2
```
PLEASE NOTE: One of them is just a comment (the one starting with #). You don't need it if you don't want it. It's just for clarity.

That should do it.

Cheers,
Belak

---

### Post by amohanty on 2008-04-26
So assuming you have the following:

/dev/sda - 80G - / (gutsy)
/dev/sdb - 20G - / hardy

What you can do is the following:
replace <fs_type> with the filesystem type of sda

1. boot into hardy
2. sudo mkdir -p /mnt/gutsy
3. mount -t <fs_type> /dev/sda /mnt/gutsy -o"rw"
4. chmod -R /mnt/gutsy username:username
5. then edit your /etc/fstab and add
/dev/sdb     /home      <file system type - ext3/xfs/etc>    defaults    0     0
6. wipe away everything on /mnt/gutsy except /home, reboot and let your /home grow to fill the 80G.

Disclaimer: I have not tried this on a machine, so you might want to backup your /home somewhere.

HTH
AM

---

### Post by DSn0wMan on 2008-04-26
Thanks for the help guys. I will give this a shot in the morning (close to midnight here). I don't want to frack things up just because I am sleepy.

---

### Post by Belak on 2008-04-26
Alright.
Good luck.

---

### Post by DSn0wMan on 2008-04-26
It worked, I am now hapily using my old home on hardy. Thanks!

---

### Post by Belak on 2008-04-26
Out of curiosity, which method did you use?

---

### Post by DSn0wMan on 2008-04-29
Actually I used a little of both. Both methods pretty much do the same thing, but I think the first post forgot to mention the changing of permissions, but has a better example of how to edit fstab. The first post also explanes that you should remove the config files. I actually copied all my hidden files and folders from my old home into a backup directory and then removed them. After that I coppied all the hidden files and folders from my new home to my old home. That way I can put the confg files back at my leasure.

---

