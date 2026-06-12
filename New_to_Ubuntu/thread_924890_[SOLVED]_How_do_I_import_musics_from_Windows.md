---
title: "[SOLVED] How do I import musics from Windows?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by msohn88 on 2008-09-20
I use rhythm box just now.
When I try to import music, it says "operation not supported".

GAW. Is there any way to get them instead of buring 9 GB of music from my Windows partition?

---

### Post by quinnten83 on 2008-09-20
ubuntu usually supports ntfs out of the box,but it might not be working properly.Install ntfs-3g from the repos. Sometimes that helps. It should be able to see and read your ntfs partitionand you shoudl be able to import into  rhythmbox. Which ubuntu version are you using?

---

### Post by msohn88 on 2008-09-20
I just downloaded it today. I don't know which version I am using.

What is ntfs-3g? I am confused and frustrated. T_T

---

### Post by quinnten83 on 2008-09-20
> **msohn88 said:**
> I just downloaded it today. I don't know which version I am using.

What is ntfs-3g? I am confused and frustrated. T_T

I can see that,
lets start from the beginning shall we?
Did you just install Ubuntu? If so, did you install the restricted packages? If you haven't you won't be able to play MP3's yet.
you can install it by going to the command prompt 
Applications > Accesories > terminal.
```
type sudo apt-get install ubuntu-restricted-extras
```
be careful, because it is going to ask you agree to java in a terminal window, do not close it without accepting the okay,otherwise you might break your java installation.
After that start rhythmbox and import music from windows.
If it doesn't work,
can you see the music on your windows partition, as in if you go to places can you see your c:\ or D:\ drive and can ifyou click on one of them can you see the folders you have in windows?
If you can do the above.
If you can't see them, go to applications > add/remove programs and search for ntfs-3g. Tick the checkbox and click ok. After that you should be able to start ntfs-3g it is under applications ntfsconfiguration tools. Chech both the options for read and write and you should be able to see the windows partition.
The next step is, can you find the music folder?
If you find the music folder, what type are they? are they mp3, AAC, WAV?
The music might be in a format that rhythmbox can't read. So let's find out first and then we can see what needs to be done.

---

### Post by Shazaam on 2008-09-20
ntfs-3g is the tool Ubuntu uses to enable read/write access with Windows. It comes with a default install. You are probably using Ubuntu Hardy Heron 8.04.
Once you get the codec issue ironed out you will need to have your Windows partition already mounted for Rhythmbox to import the music. Ubuntu used to auto-mount other partitions/drives but this has changed in Hardy. Go to Places>Removable Media and click on your Windows drive to mount it. It will place a drive icon on your desktop. To unmount the drive right-click the icon and choose "Unmount volume". More than likely you will have to do this every time you access your Windows music folder with Rhythmbox unless you edit a file named "fstab".

---

### Post by quinnten83 on 2008-09-20
actually my windows partitions were automounted. And i never had to edit fstab manually. I do know that sometimes it doesn't work ootb. That's when I have to reach for the ntfs-3g.
The thread is marked solved now. I wonder what it was.

---

### Post by Shazaam on 2008-09-20
> **quinnten83 said:**
> actually my windows partitions were automounted. And i never had to edit fstab manually. I do know that sometimes it doesn't work ootb. That's when I have to reach for the ntfs-3g.
The thread is marked solved now. I wonder what it was.

I hate to hijack but did you upgrade or do a fresh install?

---

### Post by quinnten83 on 2008-09-20
fresh install, I've heard to many horror stories of upgrades.
I have a seperate home partition, so all is good.

---

### Post by Shazaam on 2008-09-20
> **quinnten83 said:**
> fresh install, I've heard to many horror stories of upgrades.
I have a seperate home partition, so all is good.

Hmm. Prolly cause my Windows is on another drive (d'oh!). :) Thanks.

---

### Post by msohn88 on 2008-09-20
Well, I got to import the music from my Windows partition.

I cannot play MP3 files.

---

### Post by msohn88 on 2008-09-20
sudo is /usr/bin/sudo
apt-get is /usr/bin/apt-get
install is /usr/bin/install
bash: type: ubuntu-restricted-extras: not found

What I get.

---

### Post by msohn88 on 2008-09-20
Never mind, I got it!  :)

---

### Post by quinnten83 on 2008-09-20
Go to system> administration> software sources.
type your password at the security window that pops up.
In the software sources window on the first tab, make sure you have software restricted by copyright or legal issues checked.
close the window if it asks to update the repository list or something similar, let it.
try installing the restricted extras after that.
this time, skip the terminal and go to applications> add remove software.
search for ubuntu-restricted-extras.
install that, and if after installing that you still can't play MP3, carefully explain to us what exactly it is that you are doing and what error messages you get.

---

### Post by msohn88 on 2008-09-20
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

GAWWWWW

---

### Post by Martje_001 on 2008-09-20
Go to a terminal, and run:
```
sudo dpkg --configure -a
```

---

### Post by msohn88 on 2008-09-20
At the end:

 dpkg: error processing deskbar-applet (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 deskbar-applet

---

### Post by quinnten83 on 2008-09-20
if you haven't completely broken your package manager yet, try in the terminal
```
sudo apt-get update
```
 and then
```
sudo apt-get remove deskbar-applet
```

and then try 
```
sudo apt-get install deskbar-applet
```

if you still get the problem,
so sudo apt-get remove deskbar and then try continuing with the installation of the extras.

---

### Post by msohn88 on 2008-09-20
It works!!! Wheee! Thanks

---

