---
title: "Shared Dropbox folder on same drive between dual boot OS"
date: 2015-07-03
forum: New to Ubuntu
---

### Post by wayne29 on 2015-07-03
Hey guys 

This may not seem like a directly Ubuntu related question, but the purpose is to keep me in Ubuntu and not reliant on Windows as much as I am. Here goes:

  
I have a laptop I do almost all of my work on,  and seen as I am on the road a lot, it is my go-to for getting things  done. I have a dual boot system at the moment, one with Windows 8.1 and  one with Ubuntu 14.04. On the Ubuntu OS, I also have a Windows 8.1  installation running in Virtualbox. 
I tried a little  while back to get Dropbox working in Ubuntu and share the  folder with the Windows 8.1 (not the virtualised one, the dual boot installation), but this cost me  dearly and wiped half my data (30GB+) before I managed to stop it. I  then had a fun few hours of recovering all deleted data and re-syncing  across multiple devices. Not going that route again. Besides, for work, my company is Windows heavy and the work just goes way faster if we're all on the same page.
Anyway, it's pretty annoying to have to close the Ubuntu session I am in  and load Windows OS  to access Dropbox, do some work, sync changes etc,  then restart and log into Ubuntu again until I have to do work, then go  through the repeated cycle.
Seen as though I prefer to stay in Ubuntu, I decided on the virtualised  Windows OS to get work done and not have to leave my session each time.  What I would like to know is - How can I install Dropbox in the  virtualised OS and set up the folder as the same one on My Windows  partition, without having to download a huge amount of files, and at the  same time not compromise the data in the original folder? This is a  work directory shared by multiple users, and I can't afford to repeat  previous mistakes.

  I know that this is more of a Dropbox issue than Ubuntu, but I've trolled forums on Dropbox, Virtualbox and Ubuntu alike and just cannot seem to find an answer. Maybe I'm not searching correctly, but I thought I'd try this here :)

Any help would be greatly appreciated. (It should be noted that I am  noob levels of noob, so simple explanations would be helpful) :)

  
Thanks!

---

### Post by tristan16 on 2015-07-04
Where did you download Dropbox from? Searching "Dropbox" in the Software Center, and actually downloading it from the website are 2 different versions. If you haven't already, I would recommend trying the official version from Dropbox.com and see if it works any better.

Another suggestion would be to use a USB hard drive, or even access your Windows hard drive directly from Ubuntu if possible.

---

### Post by Bucky Ball on 2015-07-04
Welcome. Accessing the Windows OS partition directly from Ubuntu is not a good idea. Why not just create a shared partition, NTFS filesystem, and dump the dropbox folder on there, or have you already tried? If you want to share data between Ubuntu and Win, you should have an NTFS partition for it in any case rather than lobbing directly into the Win OS partition.

Incidentally, the Dropbox in the repositories of 14.04 works just fine on my wife's machine. If you install from a third-party it is not checked for compatibility by Canonical. 

Always best to stick with the repo version unless there is a specific reason to start installing third-party software and PPAs. You are clearly warned at the time that you do this at your own risk. They are maintained by a third-party that generally has no official connection with Ubuntu or Canonical. :)

Good luck.

---

