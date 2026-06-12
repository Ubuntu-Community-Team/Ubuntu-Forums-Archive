---
title: "Moving personal folders"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by XSaenen on 2011-11-28
Another day, another (probably stupid) question.
 
I have a multiboot setup and would like my personal folders (downloads, pictures, etc) to be accessible by any OS on this machine. 
I have created a partition for such data, but am struggling to teach Ubuntu that the user folders should go there.
 
Setup : single 250GB HDD with 4 systems and a data partition.
```

**Partition        File system       Mount Point     Label           Size               Flags**
/dev/sda1        NTFS                              XP Disk         30.00 GiB          boot
/dev/sda2        NTFS                              Vista Disk      30.00 GiB
/dev/sda3        NTFS                              Win 7 Disk      30.00 GiB
/dev/sda4        Extended                                          142.89 GiB
   /dev/sda6     linux-swap                                        976 MiB
   /dev/sda7     ext4               /                              28.61 GiB
   /dev/sda5     NTFS               /media/Data    Data            113.32 GiB

```
 
For cleanliness (each OS makes its recycle bin folders which are visible in the other OS) I created a "User files" folder in the Data partition (sda5). That folder contains the usual folders (Pictures, Music, Videos, etc).
 
I did not to use a separate /home mount point because I want the user folders to be accessible by every OS.  
That way if I drop a picture in my "Pictures" folder in one OS and boot into another one, the picture will be in the "Pictures" folder there as well.
  
I managed to get the Data partition to mount automatically (by editing the fstab file) and hid its icon from the desktop (by using the gconf-editor). 
However I can't seem to find a way to tell Ubuntu that the personal folders are on that drive.
 
For example : the default picture folder is /home/USERNAME/Pictures. I want it to be /media/Data/User files/Pictures. 
 
 
 
 
How do I tell Ubuntu to do that? I read elsewhere that ...
```
gedit ~/.config/user-dirs.dirs
```
... would do the trick, but if I enter that code in Terminal I only see a blank document.

---

### Post by Derek Karpinski on 2011-11-28
I wouldn't try to move any of your folders in /home.  I think you're just asking for trouble.  What you could do is make links from your /home folder to your data drive.

```
man ln
```

Example:
```
ln -s /home/$USER/Documents/ /media/Data/Documents/
```And I would mount your data drive in /mnt instead of /media so the drive icon won't show up on your launcher bar.........unless you like it like that.

---

### Post by Derek Karpinski on 2011-11-28
After doing that, in the windows side, assuming you're running Win 7, you can change the location of your 'libraries' by right clicking on the library and going to the location tab.

---

### Post by XSaenen on 2011-11-28
Thanks. How will the folders behave with that link code? Is everything automatically transferred to the data disk or something?
 
Also thanks on the /mnt tip. Should have thought of that, and probably would have saved me a lot of effort.

---

### Post by Derek Karpinski on 2011-11-28
It's just a link of your data.  It doesn't copy the file or anything, it is just like a 'shortcut' in Windows.

Just try it yourself, and drop some files in your /home/$USER/Documents, and then browse to wherever you made the link to.  You'll see your file, or a link to it.  Tough to explain..........just do it man! :D

---

### Post by XSaenen on 2011-11-28
Ok, that enables me to get to the user folder in Ubuntu. However in windows that link shows up as a system file instead of transferring me to the actual folder I'm aiming for. 
 
This is precisely why I want Ubuntu to physically use the folder on the /media/Data partition.
 
To explain it again, I want to be able to put a file in my users folder in any OS, and then have access to that same folder in any other OS.  
Getting the 3 MS systems to go hand in hand is no biggie, and if I can let Ubuntu use the folder on the /media/Data partition as a home folder, I can get all 4 to go hand in hand.

---

### Post by Derek Karpinski on 2011-11-28
I forgot one thing.........

All data will be stored on your actual / partition.  And your /data partition will not really store anything but links.  The way you have everything partitioned now, you're likely to run out of room on your / partition. Unless we revise your partitioning structure.

Another thing.........

It looks like you're fairly new to the forums.  So please keep this in mind: People are more than willing to help you, but people do make mistakes.  Please be careful copying, pasting, and running code provided here in your terminal.  ALWAYS know what you're pasting in Terminal before hitting enter! :D  That's why I referred you to the man page for ln first.

---

### Post by cortman on 2011-11-28
I dual boot between Win7 and Ubuntu 11.10, and I wanted the same thing- access to my stuff from both OS's.
What I wound up doing was creating a new extended partition in Win7, so that it would automatically be accessible from Windows. I remapped my libraries in Windows to that partition, and moved all my stuff from Ubuntu onto that partition. It's been working beautifully.
Just my two cents...

---

### Post by Derek Karpinski on 2011-11-28
Okay..........options:


[LIST=1]
[*]Use links and link the other way:```
ln -s /media/Data/Documents/ /home/$USER/Documents/
```
[*]Create all your Documents, Music, Pictures, etc folders in /media/Data, and use the --bind option in fstab to mount the /media/Data/ folders to your /home. [http://ubuntuforums.org/showthread.php?t=979435](http://ubuntuforums.org/showthread.php?t=979435)
[/LIST]

---

### Post by Derek Karpinski on 2011-11-28
oldfred has some good links here:

[http://ubuntuforums.org/showpost.php?p=11441028&postcount=3](http://ubuntuforums.org/showpost.php?p=11441028&postcount=3)

Another thread:

[http://ubuntuforums.org/showthread.php?t=1816406](http://ubuntuforums.org/showthread.php?t=1816406)

---

### Post by XSaenen on 2011-11-28
Derek,
 
I'm fairly new to this forum, but I do have some forum experience. So I know I need to be careful. 
 
Resetting the entire thing and installing Ubuntu again only takes about 10/15 minutes, which I can use to look things up on another machine and think about my options. 
Because I use an old HDD which I intend on replacing soon, I'm not too worried about wasting an SSD's write cycles either. 
Right now I'm just trying to get it to work. Once I figured everything out I can do it properly on the new SSD. So I'm not too worried about messing it up and starting over from scratch again.
While I prefer correct answers (who doesn't?), I don't mind mistakes. I make plenty of them myself. We all learn from our (and eachothers) mistakes.
 
As for the way I have everything partitioned : I intend to have all data on the 110-ish GB partition, using the system partitions only as a place to store the operating systems. So 30GB should do the trick. For some (XP and Ubuntu) 15 or 20 would actually suffice.
 
----
 
Just had another idea. Can I create a separate /home partition in FAT or NTFS? If so, I could let Ubuntu work the details out its own way, and then trick the various Windows versions into using the same folders Ubuntu uses. Sort of what Cortman suggests.
 
EDIT : Just saw that you suggested linking them the other way round. I'll look into that once I'm through this new install.

---

### Post by Miljet on 2011-11-28
This is a very interesting thread that I am sure will help many people. Please follow through and let us know what eventually works for you.

---

### Post by Derek Karpinski on 2011-11-28
I remember seeing a multipage thread here, where someone was trying to do what you are attempting.  Lots of good info.  IMHO using the bind option in fstab would be a better choice than linking.

I'm leaving for a bit. I'm sure someone can step in and help you.  But, reinstalling with a separate /home would be a good idea, and probably make things easier IMHO.

---

### Post by XSaenen on 2011-11-28
Yeah, I'm doing just that right now. Only problem is the ext4 format. 
But then again there appear to be tools that allow Windows (XP and up) to read ext4, so it should work out.
 
I'll update as soon as I solved it or ran headfirst into a brick wall.
 
Thanks again for your help.
 
-----
 
EDIT : One brick wall after another.  I'm really getting fed up with this now.  I like Ubuntu, I really do.  I love the customizeable UI and everything, but this file managment system is just WRONG.

---

### Post by Derek Karpinski on 2011-11-28
So you should now have a nice, clean install of XP, W7, Vista, and Ubuntu with separate /home.  You also have a separate data partition with NTFS type.  This is what I'm thinking:


[LIST=1]
[*]```
sudo mkdir /mnt/data/
```
[*]```
sudo blkid
``` to find UUID for /data partition
[*]Edit fstab to mount /data to /mnt/data ```
gksudo gedit /etc/fstab
``` ```
UUID="YOUR UUID from above" /mnt/data ntfs defaults,umask=000 0 2
```
[*]```
sudo mount -a
```
[*]Make Documents, Pictures, Videos, etc folders in /mnt/data/$USER
[*]```
ln -s /mnt/data/$USER/Documents/ /home/$USER/Documents/
``` repeat for each folder (Pictures, Videos, etc)
[*]in Win XP follow this: [http://support.microsoft.com/kb/310147](http://support.microsoft.com/kb/310147)
[*]in Win Vista and Win 7 should be similar.
[/LIST]
That should work well.  You might have to mount the data drive with world read-write-execute. use umask, dmask, and fmask..........for now ```
UUID="YOUR UUID from above" /mnt/data ntfs defaults,umask=000 0 2
``` will open everything up until you figure out how you want to lock down your drive.  Windows, I don't think, cares about unix permissions, so you may want to mount with acls instead. And I'm pretty sure Windows repsects acl permissions.  But I maybe wrong.

Note: when I say $USER, I mean your username, or other usernames you want folders for.

---

### Post by Derek Karpinski on 2011-11-28
> **XSaenen said:**
> Yeah, I'm doing just that right now. Only problem is the ext4 format. 
But then again there appear to be tools that allow Windows (XP and up) to read ext4, so it should work out.
 
I'll update as soon as I solved it or ran headfirst into a brick wall.
 
Thanks again for your help.
 
-----
 
EDIT : One brick wall after another.  I'm really getting fed up with this now.  I like Ubuntu, I really do.  I love the customizeable UI and everything, but this file managment system is just WRONG.

What's wrong with the file management system?  I think you'll find that Linux in general holds to strict guidelines/file structure/permissions at the expense of being easy to use.  That also makes it way more secure.  Windows on the other hand throws standards/guidelines out the window so monkeys can operate it, at the expense of security/compatibility.

So, take a deep breath, and realize Ubuntu is NOT windows. What you're attempting is not that trivial for a beginner. :D

---

### Post by cortman on 2011-11-29
> **XSaenen said:**
> Yeah, I'm doing just that right now. Only problem is the ext4 format. 
But then again there appear to be tools that allow Windows (XP and up) to read ext4, so it should work out.
 
I'll update as soon as I solved it or ran headfirst into a brick wall.
 
Thanks again for your help.
 
-----
 
EDIT : One brick wall after another.  I'm really getting fed up with this now.  I like Ubuntu, I really do.  I love the customizeable UI and everything, but this file managment system is just WRONG.

I didn't want to have to get any special tools to read ext4 for Windows, so I just made the storage partition NTFS in Windows. Linux will read/write fine in NTFS, the only things that don't work are file permissions, but that's the price you pay.
I would seriously recommend skipping the "try-to-make-windows-see-ext4" and just make an NTFS partition with Windows, which will be plug and play with both of your OS's.

---

### Post by cortman on 2011-11-29
[Here's]("http://ubuntuforums.org/showthread.php?t=1865750") a thread with some advice I got when I was looking to do the same thing.

---

### Post by Derek Karpinski on 2011-11-30
Your post about NTFS made me take another look at what I was typing.  The /data drive needs to be mounted as ntfs in the fstab.

Changes made.

---

### Post by 1childish1 on 2011-12-15
Hi XSaenen

Well, I'm very new to Ubuntu and I don't know if this is what you are looking for:

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

I had asked about sharing files with Ubuntu 11.10 and Windows 7 Ultimate, and Megaptera replied this link. I tried it out with the Virtual PC I made (with VBox) and I am pleased with the results! It allows for me to have a single folder for Music (and others) for Ubuntu and Windows in an NTFS partition. And every time I log into either OS I see the same files in the same folders.

Hope this helps!

=P

---

