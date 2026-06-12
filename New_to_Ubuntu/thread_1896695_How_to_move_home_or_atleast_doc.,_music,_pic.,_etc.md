---
title: "How to move /home or atleast doc., music, pic., etc."
date: 2011-12-17
forum: New to Ubuntu
---

### Post by Dragonpoet on 2011-12-17
OK, let me begin by saying that I am a complete newbie to Ubuntu.

Background: I am running Ubuntu 11.10 64-bit. I am dual booting with Windows 7. I have three partitions on my hard drive. The first one (/dev/sda1) is where I have Windows 7. Then on the second on (/dev/sda2) I have it labled "Storage" where I want to share files such as my pictures or documents between to the two OS's. And on the 3rd (/deva/sda3) I have sda5 and sda6. Sda5 has the files for Ubuntu and sda6 is Linux swap.

Problem: As mentioned earlier, I want to share files on my partition marked "Storage" on /dev/sda2. It is formatted NTFS. I was wondering how to move /home/max/Documents, /home/max/Pictures, /home/max/Downloads, /home/max/Videos, and /home/max/Music to /media/Storage/.

If I am not being clear enough let me know and I will do my best to try and explain myself. Thank you so much for the help in advance.

---

### Post by 9072997 on 2011-12-17
your best option would be soft links:
  to make /media/hd/home the new home folder
#  mv /home /media/hd/home   DO NOT continue unless this step succeeds as you will lose everything
#  rm -r /home
#  ln -s /media/hd/home /home

---

### Post by Morbius1 on 2011-12-17
Is the /media/Storage partition mounted automatically when you boot? In other words do you have an entry in /etc/fstab for that partition?

If you do then I would use "bind". Try the following as an experiment to illustrate what I mean:

[1] Create a "test" directory in your home folder
```
mkdir /home/max/Test
```[2] Create an identical folder in your "Storage" partition
```
 mkdir /media/Storage/Test
```[3] Bind the two together ( temporarily ):
```
sudo mount --bind /media/Storage/Test /home/max/Test
```Now add a file to /home/max/Test and look at the contents of /media/Storage/Test. They should be the same.

If you unmount the bind:
```
sudo umount /home/max/Test
```The contents of Test in your home directory will be empty but the contents of Test in the Storage partition will contain the added file.

I would not put your entire home directory on an NTFS partition but you can copy each of the subfolders in your home directory over to /media/Storage, use bind to have all these subdirectories connect back to your home directory, and you can have this done automatically at boot: [http://ubuntuforums.org/showthread.php?p=10899012#post10899012](http://ubuntuforums.org/showthread.php?p=10899012#post10899012)

---

### Post by oldfred on 2011-12-17
I think 9072997 suggestion is dangerous as the hidden files & folder in /home have to have Linux ownership & permissions. You cannot move all of /home to NTFS and link back. It might work if the other partition was not NTFS but it is not necessary.

I often refer to Morbius1's posts on mounting and using bindfs, but I use simple linking as I do not need all of the advantages that bindfs has.

If you have partition mounted in /mnt/Storage and it has a folder Music you can do this. If you have the default /home/Music you have to rename or delete (if no data) first.

#from home so default location of link is in /home/fred or your /home.
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/Storage
ln -s /mnt/Storage/Music
I have not tried it, but if your are in the folder /home/fred/max I think the above would put the link there or in the link command you can specify the to location rather than let it default to where you are.

---

### Post by Paqman on 2011-12-17
> **oldfred said:**
> You cannot move all of /home to NTFS and link back.

+1

You can link the individual folders in your home to another location, or you could mount them through /etc/fstab, but I wouldn't move your whole home folder.

---

### Post by Morbius1 on 2011-12-17
For the record I'm not using bindfs but bind especially since bindfs won't install in the latest Ubuntu :wink:

The only reason I don't line symlinks is because I use Samba and Samba doesn't allow any client to follow symlinks. It can be overridden but Samba's not hot on the idea. 

Nothing wrong with symlinks and that's the "normal" way this sort of thing is done, I've just never liked them. If the folders aren't being shared across the network then bind may be overkill I suppose. The way my system is set up I have a /Data partition and a /home directory not a separate home partition. I use bind to link them back so if I change OS's my data is preserved.

Different paths to the same destination.

---

### Post by amjjawad on 2011-12-17
> **Dragonpoet said:**
> OK, let me begin by saying that I am a complete newbie to Ubuntu.

Background: I am running Ubuntu 11.10 64-bit. I am dual booting with Windows 7. I have three partitions on my hard drive. The first one (/dev/sda1) is where I have Windows 7. Then on the second on (/dev/sda2) I have it labled "Storage" where I want to share files such as my pictures or documents between to the two OS's. And on the 3rd (/deva/sda3) I have sda5 and sda6. Sda5 has the files for Ubuntu and sda6 is Linux swap.

Problem: As mentioned earlier, I want to share files on my partition marked "Storage" on /dev/sda2. It is formatted NTFS. I was wondering how to move /home/max/Documents, /home/max/Pictures, /home/max/Downloads, /home/max/Videos, and /home/max/Music to /media/Storage/.

If I am not being clear enough let me know and I will do my best to try and explain myself. Thank you so much for the help in advance.

Hello and Welcome to Ubuntu Forum :)

There is a better way with LESS headache, call it a shortcut if you want :)
Instead of all that (moving, copying, etc), do one simple thing: use "sda2" which is your "Storage" drive to store these files (Photos, Music, Docs, etc) instead of having that on your /home folder (looks like you don't have a separate /home partition). End of story :)
In this way, both Systems will have access to these files. You don't need two copies, you don't need copy-paste or move-paste, you just need to store them in one place which is accessible by both systems. Luckily, I don't need that anymore because I no more Dual-Boot nor Multi-Boot with Windows but I understand your case is different.

Linux, by default, read/write from/to NTFS Partitions. 
Windows, by default, CAN NOT read/write from/to Linux File Systems (say ext4).

This is what I would do if I were you.

---

### Post by Dragonpoet on 2011-12-17
Thanks everyone for the help. But instead of moving my entire /home, what if I just move the documents, pictures, download, videos and music folders and to the "Storage" partition? How would I go about doing that with Ubuntu recognizing that those 5 folders on the "Storage" partition (or sda2) are actually part of the /home files? Thanks for the help thus far! :P

---

### Post by amjjawad on 2011-12-17
> **Dragonpoet said:**
> But instead of moving my entire /home, what if I just move the documents, pictures, download, videos and music folders and to the "Storage" partition? How would I go about doing that with Ubuntu recognizing that those 5 folders on the "Storage" partition (or sda2) are actually part of the /home files? Thanks for the help thus far! :P

By default, you should be able to do so. While you are logged in to Ubuntu, go to your Home Folder and Move the Files/Folders to your other partition which MUST be mounted of course before that.

Hope I understood your Q probably.

---

### Post by Dragonpoet on 2011-12-17
> **amjjawad said:**
> By default, you should be able to do so. While you are logged in to Ubuntu, go to your Home Folder and Move the Files/Folders to your other partition which MUST be mounted of course before that.

Hope I understood your Q probably.

I tried that. I was able to merge the folders, but it doesn't recognize that I want them to be the default folder locations.

---

### Post by evilsoup on 2011-12-17
Open up your home folder (~). From there, open up the .config folder (you will first need to enable hidden folders by pressing ctrl+h). Find the file 'usr-dirs.dirs'

This is the configuration file for what directories are treated as your 'Documents', 'Videos', etc. You may want to backup this file before messing with it.

The file will contain some comments explaining what it is, plus some lines like:

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"


For example, to make your 'Documents' match up with the 'Documents' folder on a separate partition, change
XDG_DOCUMENTS_DIR="$HOME/Documents"
to
XDG_DOCUMENTS_DIR="/media/HD/Documents"

You may need to log out and log back in for these changes to take effect.

---

### Post by Dragonpoet on 2011-12-18
Thank you! That worked like a charm! Is there any way for me to give you reps or props as thanks for helping me out?

---

### Post by amjjawad on 2011-12-18
> **Dragonpoet said:**
> That worked like a charm!

Glad you managed to fix that.

Please mark your thread as SOLVED if you don't have any further Qs :) this will help others to follow the steps you did to fix such issues.

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by satanselbow on 2011-12-18
> **evilsoup said:**
> Open up your home folder (~). From there, open up the .config folder (you will first need to enable hidden folders by pressing ctrl+h). Find the file 'usr-dirs.dirs'


You may have problems on reboot as your 2nd partition will have to be automounted at login :$

Also a cleaner way to make your changes in the defaults file and the run the update script. You will need to delete the existing ~/.config/user-dirs.dir 1st:

```

rm ~/.config/user-dirs.dir
gksu gedit /etc/xdg/user-dirs.defaults
xdg-user-dirs-update

```

---

### Post by tommpogg on 2011-12-18
> **oldfred said:**
> 
I often refer to Morbius1's posts on mounting and using bindfs, but I use simple linking as I do not need all of the advantages that bindfs has.

Me too I use soft links. What are the advantages of using bind/bindfs?

Thanks

---

### Post by Morbius1 on 2011-12-18
> **tommpogg said:**
> Me too I use soft links. What are the advantages of using bind/bindfs?

Thanks
There are 3 in my mind:

[1] The Samba thing I referenced above.

[2] Multiple ways to implement

* Adding a line to /etc/rc.local
* Creating an upstart job - my method of choice
* With a slightly different syntax you can add it to fstab directly

[3] There's a write once - run everywhere quality to a bind.

 The bind expression is all relative in that it requires you have a home directory and the partition you are binding from has to have a mount point of /media/Storage in this case. Doesn't even matter if the disk is replaced at some point in the future as long as you mount it to /media/Storage then your bind will still work. 

Copy the lines in rc.local, upstart, or fstab to a safe place and reuse them when you change OS's.

---

