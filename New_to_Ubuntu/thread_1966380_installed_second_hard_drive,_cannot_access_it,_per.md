---
title: "installed second hard drive, cannot access it, permission denied"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by koolkatkiwi on 2012-04-27
Hi. I'm still a beginner. This is an AMD Athlon64 3500+ with 4GB RAM, running Xubuntu 10.04 in 32 bit mode. I ran out of storage space, so I physically installed a second hard drive, then tried to get the drive recognised using this tutorial:

[http://www.mikestechblog.com/joomla/operating-systems-section/operating-systems-ubuntu/53-add-a-second-hard-drive-in-ubuntu.html](http://www.mikestechblog.com/joomla/operating-systems-section/operating-systems-ubuntu/53-add-a-second-hard-drive-in-ubuntu.html)

It seemed to work fine - the drive is now recognised in the BIOS, and in the System Monitor. He instructed to mount the drive in the /mnt folder, so I did that, using vi (shudder), as he instructed. 

But, the drive is not showing up in the File System as a separate drive. When I look for it in /mnt, it is there, but when trying to access it, access is denied, and on checking the file permissions, I see that it is owned by root.

How can I get this drive to show up in the file system as a separate drive, and just be able to access it as extra storage, which is what I wanted it for? I didn't install any operating system on it, just formatted it as ext4. I can't really understand why the tutorial said to mount it in /mnt, if it won't show up as a separate drive.

Sorry if this sounds totally dumb. Any ideas how I can get it to show up as a drive that I can use?

---

### Post by carl4926 on 2012-04-27
It shouldn't be necessary to do all that fiddling.
It should just mount on the fly

What format is the HD and how many partitions?

You could add it to fstab I guess.
I wouldn't set the mount point to /mnt though. I'd create a folder on the root tree
Eg:  /STORE
Then chown it to yourself
Do you follow or need ABC

---

### Post by koolkatkiwi on 2012-04-27
Hi. Thanks for replying. :) I used the whole disk in one logical partition. I formatted it as ext4. If you look at that link I gave, you'll see what I did, as I followed his instructions to the letter. 

It doesn't seem to want to mount on the fly. I see your point about not setting the mount point to /mnt, but I needed a tutorial that I could follow exactly, and that's what he said to do. If you look in the tutorial, he has set the permissions to 777, so I don't know why I was denied permission.

I would need ABC, I think. :confused: Though, with your comments, I could do some more googling with the clues you've given.

Thank you. 

Kath :KS

> **carl4926 said:**
> It shouldn't be necessary to do all that fiddling.
It should just mount on the fly

What format is the HD and how many partitions?

You could add it to fstab I guess.
I wouldn't set the mount point to /mnt though. I'd create a folder on the root tree
Eg:  /STORE
Then chown it to yourself
Do you follow or need ABC

---

### Post by carl4926 on 2012-04-27
If the device is sdb1

edit fstab like this

```
/dev/sdb1 /STORE ext4 acl,user_xattr        1 2

```

Create the dir STORE
From a terminal
```
cd /
```
```
sudo mkdir /STORE
```

```
sudo chown -R yourusername /STORE
```

reboot

---

### Post by koolkatkiwi on 2012-04-27
Hi. Before I do these things, can you tell me if the fstab looks correct? This is what it looks like before editing it as you suggest:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=f8014e54-6bda-4e96-97b1-6bdfa7cf16d4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=3375130d-7fa3-4bf9-b51d-71b47acb3385 /home           ext4    defaults        0       2
/dev/sdb1 /mnt/sdb1 ext4 defaults 0 0 
```

So, should I just put in the line you have given me below, at the end of this file, or remove the current last line first?

I will go ahead and do the operation once you say whether to remove that last line before adding the line you gave me. Thanks.


> **carl4926 said:**
> If the device is sdb1

edit fstab like this

```
/dev/sdb1 /STORE ext4 acl,user_xattr        1 2

```

Create the dir STORE
From a terminal
```
cd /
```
```
sudo mkdir /STORE
```

```
sudo chown -R yourusername /STORE
```

reboot

---

### Post by Morbius1 on 2012-04-27
Your fstab is fine although I would have used a UUID number rather than the /dev/sdb1 notation. All you need to do is take possession of the mounted partition:
```
sudo chown morbius /mnt/sdb1
```[COLOR=Blue]*Change morbius to your own login user name*[/COLOR]

---

### Post by carl4926 on 2012-04-27
You can # that line out

And add in what I gave you.
FYI: You could use the defaults 0 0 setting if you prefer

SO instead of

```
/dev/sdb1 /STORE ext4 acl,user_xattr        1 2
```

it could be

```
/dev/sdb1 /STORE ext4 defaults        0 0
```

Make sure to hit return in fstab on the very last line at the end of the code, as if you were starting a new line..

I don't use XFCE, but I do seem to recall some different behaviour with it in mounting on the fly compared to gnome and kde.

---

### Post by Morbius1 on 2012-04-27
You know I decided to look at the HowTo referenced in the original post and I think I see how we all got here.

He had him:

(1) Create a mount point (** sudo mkdir /mnt/sdb1** )
(2) Change permissions ( **sudo chmod 777 /mnt/sdb1** )
(3) Add a line to fstab using vi because he's sadistic ( **/dev/sdb1 /mnt/sdb1 ext4 defaults 0 0** )
(4) And then issue a command that will not work since he forgot to preface it with sudo (** mount -a** )

Changing permissions on a mount point before that partition is mounted will do nothing since a mount always overrides the permissions of the mount point folder.

So had the author put step (2) after the corrected ( sudo mount -a ) step (4) we would not be having this conversation ;)

---

### Post by koolkatkiwi on 2012-04-27
OK - thanks for all your help. (I'm a lady, BTW, dealing with my husband's computer - he can't fix stuff or use the terminal. ;))

I've done what you said. Here's the situation now: In the /mnt folder is sdb1. This shows a volume of 9G and is owned by billw (my husband), and has read and write access. sdb1, I would have thought, would be the second hard drive, which is 500GB and not 9G.

The /STORE folder is owned by billw and has read and write access. It shows 500GB volume, which is what the second hard drive is.

So, we can now access the 500GB drive, but only by going into the /STORE folder. What I had really wanted was for the second hard drive to appear in the file tree at the left hand side of the File Manager as a drive, much the same as you see an extra drive when you plug in a thumb drive, for instance. It seems to me that it should appear as a drive in its own right, not in a folder off the root.

Is this possible to do, or not? I want to make it easy for my husband to use the new drive, and not have to go into the File System folder to get to it. 

Thanks again, and sorry to be obtuse. It is at least usable now anyway, if we can't get it showing up as a separate drive.

---

### Post by koolkatkiwi on 2012-04-27
Oh, about vi. I'm glad you agree with my sentiments. I don't know what kind of convoluted brain would have invented such a counter-intuitive interface. :P

---

### Post by carl4926 on 2012-04-27
> **koolkatkiwi said:**
> OK - thanks for all your help. (I'm a lady, BTW, dealing with my husband's computer - he can't fix stuff or use the terminal. ;))

I've done what you said. Here's the situation now: In the /mnt folder is sdb1. This shows a volume of 9G and is owned by root. In the Properties - Permissions, the file permissions are all greyed out - nevertheless, I do seem to be able to access and change the test file that's in that folder. sdb1, I would have thought, would be the second hard drive, which is 500GB and not 9G.

The /STORE folder is owned by billw (my husband) and has read and write access. It shows 500GB volume, which is what the second hard drive is.

So, we can now access the 500GB drive, but only by going into the /STORE folder. What I had really wanted was for the second hard drive to appear in the file tree at the left hand side of the File Manager as a drive, much the same as you see an extra drive when you plug in a thumb drive, for instance. It seems to me that it should appear as a drive in its own right, not in a folder off the root.

Is this possible to do, or not? I want to make it easy for my husband to use the new drive, and not have to go into the File System folder to get to it. 

Thanks again, and sorry to be obtuse. It is at least usable now anyway, if we can't get it showing up as a separate drive.

Forget /mnt
You should be able to put /STORE to your 'Places' (not sure what is in XFCE)

---

### Post by koolkatkiwi on 2012-04-27
I have just been doing a bit of researching and I think the problem might be the Thunar File Manager. I have now installed nautilus, but I can't seem to make the switch, because there are no options to change this in the "Preferred Applications" in the xfce Settings Manager (xfce 4.6).

I may move away from xubuntu and change to the current ubuntu distro, because there is a bit too much of a "bare bones" feel to me with this distro. It was to try to make his computer run as fast as possible that we changed to this distro.

---

### Post by oldfred on 2012-04-28
I use Ubuntu, so it may be a bit different. And I still learn about permissions and ownership from Morbius1.

I mount my data partitions in /mnt as I have what used to be my /home folders like Documents, Music, Videos etc at the top level of my data partition (and only folders). I then link each folder into my /home replacing the defaults.

But I also have a shared NTFS partition that I also mount in /mnt and just link the entire thing to /home. This one could probably just be directly mounted into /home. 

The other alternative it to mount in /media. Then the mount will be directly shown in Nautilus (not sure about Thunar)

I intentionally mount in /mnt so it is not shown. And mounts in /home or /media will be shown. And if not mounted in fstab and you label it, a default mount uses a label, so I label all partitions even if I do not mount them so I know what they are. You can add labels with gparted or Disk Utility.

---

### Post by koolkatkiwi on 2012-04-28
[SIZE="3"]**[COLOR="MediumTurquoise"]YES![/COLOR]**[/SIZE] :popcorn:

After your tip, I googled how to add it to "Places" and was able to drag and drop it in the File Manager. That was all there was to it! Just, drag and drop the STORE folder and it now shows up in the file tree. :guitar:

Thank you all. It will now be easy to use this hard drive.

Cheers,
Kath :KS


> **carl4926 said:**
> Forget /mnt
You should be able to put /STORE to your 'Places' (not sure what is in XFCE)

---

### Post by carl4926 on 2012-04-28
Good to know you are OK

---

### Post by koolkatkiwi on 2012-04-28
Thank you, oldfred. I never realised that if I mounted the drive in /media it would show up, but of course, that is where the removable drives mount, isn't it, and they show up. I should have thought of that! I tend to just take peoples' instructions very literally, and don't stop to think for myself sometimes. Got to get the old brain working on its own. ;)

I will look at what you've suggested, and maybe try that sometime. Meanwhile, I can get back to my computer and give this one back to Bill, with the new drive available to him, thanks to you guys! :)

Cheers,
Kath :KS

> **oldfred said:**
> I use Ubuntu, so it may be a bit different. And I still learn about permissions and ownership from Morbius1.

I mount my data partitions in /mnt as I have what used to be my /home folders like Documents, Music, Videos etc at the top level of my data partition (and only folders). I then link each folder into my /home replacing the defaults.

But I also have a shared NTFS partition that I also mount in /mnt and just link the entire thing to /home. This one could probably just be directly mounted into /home. 

The other alternative it to mount in /media. Then the mount will be directly shown in Nautilus (not sure about Thunar)

I intentionally mount in /mnt so it is not shown. And mounts in /home or /media will be shown. And if not mounted in fstab and you label it, a default mount uses a label, so I label all partitions even if I do not mount them so I know what they are. You can add labels with gparted or Disk Utility.

---

### Post by Morbius1 on 2012-04-28
> What I had really wanted was for the second hard drive to appear in the  file tree at the left hand side of the File Manager as a driveThe key work in your post was "tree".

Thunar and Nautilus both have 2 ways to display the left panel in the file manager: Tree and Shortcuts. Tree will show the mount point at wherever you ended up setting it within the tree. If you set Thunar to display shortcuts:

Thunar > View > Side Pane > Shortcuts 

and then select /mnt/sdb1 or /Store or whatever your mountpoint is and drag it to the side panel it will show up as a separate link to that folder.

And btw, Thunar has many advanced features that Nautilus no longer possesses:

** Open Parent Folder
** The ability to set a custom command through "Open With" 
** Easily set the Location Selector from Pathbar to Toolbar

To name a few.

---

