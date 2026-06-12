---
title: "ubuntu is dead ! DEAD !"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Ginoxy on 2008-06-15
hello !  i dont knwo whats happened to ubuntu ! i just boot again and guess what my evulotion mail wont get messages it says that there is no enough space ! and when i want to print screen it says that i dont have "desktop" and my bluetooth device wont work !!! 

whats wrong ?

---

### Post by PmDematagoda on 2008-06-15
Post the output of:-
```
df
```

---

### Post by lswest on 2008-06-15
More descriptive titles would help first off.  Secondly: what was the last thing you did on Ubuntu? can you please post the output of ```
df -h
``` and run ```
sudo apt-get autoclean
``` (see if that frees up some space)  Can you post the output of ```
ls ~
```

Sorry, but I don't have or use bluetooth, so I can't help you there.

---

### Post by Ginoxy on 2008-06-15
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       8719628   8408784         0 100% /
varrun                  517248       108    517140   1% /var/run
varlock                 517248         0    517248   0% /var/lock
udev                    517248        64    517184   1% /dev
devshm                  517248        12    517236   1% /dev/shm
lrm                     517248     38176    479072   8% /lib/modules/2.6.24-18-generic/volatile
overflow                  1024        36       988   4% /tmp
gvfs-fuse-daemon       8719628   8408784         0 100% /home/ginoxy/.gvfs

---

### Post by mikewhatever on 2008-06-15
>  Re: ubuntu is dead ! DEAD

Well, at least it boots.:lolflag:

---

### Post by damis648 on 2008-06-15
What are you doing to get your bluetooth device working and what is it?

---

### Post by PmDematagoda on 2008-06-15
Yep, you don't have any space on it. 

Do the sudp apt-get clean command provided lswest and get rid of any other files you may not need.

---

### Post by Ginoxy on 2008-06-15
ginoxy@ginoxy-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      8.4G  8.0G     0 100% /
varrun                506M  108K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   64K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   38M  468M   8% /lib/modules/2.6.24-18-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
gvfs-fuse-daemon      8.4G  8.0G     0 100% /home/ginoxy/.gvfs

---

### Post by Ginoxy on 2008-06-15
what is my space ? and how can i gain more space ?

---

### Post by PmDematagoda on 2008-06-15
> **Ginoxy said:**
> what is my space ? and how can i gain more space ?

One way is with:-
```
sudo apt-get clean
```
as suggested by lswest.

And the other is by removing any unnecessary files. One more way is to increase the amount of space Ubuntu has by increasing the partition or by simply buying a bigger hard drive:).

After that is done, reboot the PC, everything should work properly again.

---

### Post by motoperpetuo on 2008-06-15
is "sudo apt-get autoclean" kind of like a disk cleanup in windows xp? because if it is, i gotta try that.

where is ubuntu most likely to leave unneeded temp files and things like that? i know the main places where junk files build up in windows, but not in linux.

---

### Post by durand on 2008-06-15
Nice title ;)

---

### Post by Ginoxy on 2008-06-15
i already have a huge harddisk but im running wubi when i first installed it i gave it 8G can i increase it now ?

---

### Post by pinecone on 2008-06-15
> **Ginoxy said:**
> what is my space ? and how can i gain more space ?

You can delete files.

---

### Post by PmDematagoda on 2008-06-15
> **Ginoxy said:**
> i already have a huge harddisk but im running wubi when i first installed it i gave it 8G can i increase it now ?

If you can, go for it:).

---

### Post by durand on 2008-06-15
> **motoperpetuo said:**
> is "sudo apt-get autoclean" kind of like a disk cleanup in windows xp? because if it is, i gotta try that.

where is ubuntu most likely to leave unneeded temp files and things like that? i know the main places where junk files build up in windows, but not in linux.

sudo apt-get autoclean removes the files downloaded by apt-get, the program you use to install software. It keeps them there so that you can reinstall them later if you want to. If you have a faster connection (fast enough to redownload the files later if you need), I suggest using:

```
sudo apt-get clean
```

instead. autoclean removes old packages while clean removes all packages that reside in the /var/cache/apt/archives/ directory

---

### Post by Ginoxy on 2008-06-15
yeah im asking , how? how can i increase ?

---

### Post by PmDematagoda on 2008-06-15
> **Ginoxy said:**
> yeah im asking , how? how can i increase ?

You may want to ask that in the Wubi sub-section found [here]("http://ubuntuforums.org/forumdisplay.php?f=234"). I am not an expert at Wubi unfortunately.

---

### Post by Joeb454 on 2008-06-15
You can try asking in the Wubi sub-forum, here's a [Link]("http://ubuntuforums.org/forumdisplay.php?f=234")

Edit: PmD beat me to it :(

---

### Post by Victormd on 2008-06-15
> **lswest said:**
> run ```
sudo apt-get autoclean
``` (see if that frees up some space)

what's the difference between autoclean and autoremove?

---

### Post by durand on 2008-06-15
One tool I find really useful is baobab. It might already be installed in ubuntu, I'm not sure. Anyway, you can access it at: Applications > Accessories > Disk Usage Analyser. If you scan your computer or whatever, it gives you a breakdown of all your files and has a nice way of showing you big files that you might want to delete.

---

### Post by durand on 2008-06-15
> **Victormd said:**
> what's the difference between autoclean and autoremove?

Autoremove removes orphaned packages, ie, packages that are not used by any programs anymore. Autoclean deletes old downloaded packages. See my comment above.

---

### Post by damis648 on 2008-06-15
> **Victormd said:**
> what's the difference between autoclean and autoremove?

Autoclean will remove the package installation files (debs) that are no longer needed. Autoremove will actually remove and uninstall packages that are no longer being used.

---

### Post by dnns123 on 2008-06-15
> **durand said:**
> sudo apt-get autoclean removes the files downloaded by apt-get, the program you use to install software. It keeps them there so that you can reinstall them later if you want to. If you have a faster connection (fast enough to redownload the files later if you need), I suggest using:

```
sudo apt-get clean
```

instead. autoclean removes old packages while clean removes all packages that reside in the /var/cache/apt/archives/ directory

Wow, thanks! That cleaned up 700mb of space!

---

### Post by PmDematagoda on 2008-06-15
> **Victormd said:**
> what's the difference between autoclean and autoremove?

Autoremove removes any packages that are not in use any more, autoclean(or clean) clears the archive of downloaded deb files.

---

### Post by mdpalow on 2008-06-15
> **Ginoxy said:**
> Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       8719628   8408784         0 100% /
varrun                  517248       108    517140   1% /var/run
varlock                 517248         0    517248   0% /var/lock
udev                    517248        64    517184   1% /dev
devshm                  517248        12    517236   1% /dev/shm
lrm                     517248     38176    479072   8% /lib/modules/2.6.24-18-generic/volatile
overflow                  1024        36       988   4% /tmp
gvfs-fuse-daemon       8719628   8408784         0 100% /home/ginoxy/.gvfs

You may have freed-up some space, but it doesn't solve the original problem. I have a feeling (could be wrong of course) you're experiencing what I call the .gvfs bug, which is unique to Hardy Heron (8.04). I don't know how the developers are coming along with all the .gvfs bugs that have been reported (quite a few), but it sounds like this one isn't fixed yet.

It was a show stopper for me and I had to go back to 7.10. Basically, your /home partition is tied to your / partition via this .gvfs and somehow it will fill up your / partition, which is MUCH smaller than /home. Looking at your 'df' output, I see your gvfs-fuse-daemon is at 100%. That's the sign of the bug unfortunately.

I installed 8.04 three times with complete success. However, while copying folders/files from an external drive I noticed this .gvfs was getting bigger and bigger. On one occasion it filled up to 100% and then my system couldn't do anything. On another occasion, it filled up to 95% and then upon my first scheduled rsync to an external drive it filled up to 100 % and then couldn't do anything. 

What I don't understand is why it's happening on my computer and perhaps yours, but not everyone's. By the third install, I was paying very close attention to exactly what I was doing and how the .gvfs was effected. That's when I learned it was during the copying of folders/files from ext. drive using nautilus and gksudo nautilus.

Anyways, this is a possibility for your problems and I'm just trying to give you something else to go on if you didn't already know about this reported bug.

If you or anyone reading this know of a fix or work-a-round, please Private Message me as I won't be following this thread.

Thank you and good luck.

---

### Post by motoperpetuo on 2008-06-15
> **durand said:**
> sudo apt-get autoclean removes the files downloaded by apt-get, the program you use to install software. It keeps them there so that you can reinstall them later if you want to. If you have a faster connection (fast enough to redownload the files later if you need), I suggest using:

```
sudo apt-get clean
```

instead. autoclean removes old packages while clean removes all packages that reside in the /var/cache/apt/archives/ directory

is there any good equivalent in ubuntu to running disk cleanup and then defraging in windows xp? or maybe linux in general just isn't as high-maintenance as windows and doesn't leave as many temp files, system restore points, and other kinds of garbage on your hard drive?

---

### Post by durand on 2008-06-16
> **motoperpetuo said:**
> is there any good equivalent in ubuntu to running disk cleanup and then defraging in windows xp? or maybe linux in general just isn't as high-maintenance as windows and doesn't leave as many temp files, system restore points, and other kinds of garbage on your hard drive?

It doesn't leave any that I know of. Anything that it does leave behind is because it might or will be used in the future. Most temp files are generated in /tmp and they are mostly deleted after the program closes.
I know that blender leaves behind simulation files which I find really annoying but I guess they are useful for future use...

Ext2/3 doesn't get very fragmented, I certainly haven't used any defrag tools so far and I can't think of any...

---

