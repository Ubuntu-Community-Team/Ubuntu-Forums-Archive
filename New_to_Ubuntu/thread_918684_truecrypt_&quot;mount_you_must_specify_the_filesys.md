---
title: "truecrypt: &quot;mount: you must specify the filesystem type&quot;"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by pranayama on 2008-09-13
I downloaded truecrypt for ubuntu, unzipped it and installed it as a deb package. Installed python-pexpect from Synaptic too. I created a file container for an encrypted volume ("kryptonite") as a standard truecrypt volume in my home folder. I chose "none" instead of "FAT" for the filing system, assuming this would create the encrypted volume in ext3 on my ubuntu partition. When I try to mount the volume, it says I must specify the file system type, but there is no toolbar option to do this.
[IMG]http://www.geocities.com/septicreptile/krypton.png[/IMG]
I don't know why there's a red grinning face next to my thread title!

---

### Post by auberginepop on 2008-09-13
You cannot mount the volume because although you have created a truecrytp volume you do not have a filesystem (because you chose none instead of FAT32).

Click on the mount button enter the relevant passwords (you may get asked for  the volume's encryption password and your administrative password). Click to options button and check the do not mount box.

Truecrypt has now made the volume available and you can make a files system.

If you container is /home/user/truecrypt you can now make it the files system of your choice eg for ext3 type:
mke2fs -j -m 0 /home/user/truecrypt

If using mke2fs you will get a warning that this is not a block device do you want to continue: chose y.

You now have a files system within a truecrypt container.

Usually after creating file systems I find you need to reboot.

After a reboot open Truecrypt and you should be able to mount the volume.

---

### Post by auberginepop on 2008-09-13
sorry. Been a while since I last created a volume and I rememebred that slightly wrong.
After mounting the volume with the do not mount file system click on the volume menu and choose volume properties. THis will give you the virtual device of the volume and this is what you make the file system on.

eg instead of mke2fs -j -m 0 /home/user/truecrypt

it will be something like

mke2fs -j -m o /dev/loop0

Then you umount in truecrypt and then remount without checking the do not mount filesystem box

---

### Post by Dragon ELEMENTAL on 2008-10-11
Thanx - this info was very useful (& allows me to use any linux filesystem I want instead of just being stuck with FAT32!)

---

### Post by coeball on 2013-02-11
I have the same problem when I tried the suggest solution I get this in terminal:

"mke2fs: Permission denied while trying to determine filesystem size"

Any idea how I can get mke2fs to run and not get this message?

---

### Post by oldos2er on 2013-02-11
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

