---
title: "Can't upgrade from 7.04 to 7.10"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Muschnick on 2008-06-17
Update manager is giving me an error

[I]Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.


Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'archive.ubuntustudio.org'[/I]


**  I have tried a few things I have found on the forums but nothing seems to work  Its driving me nuts.

I would like to upgrade up to 8.04 but have read I need to go to 7.10 first.  

Any help is greatly appreciated!!

Let me know if you need any more info

---

### Post by shifty_powers on 2008-06-17
do you have a separate /home partition by any chance?

---

### Post by Muschnick on 2008-06-17
Yes I do.  Unfortunately a friend set this up and I am not well versed in Ubuntu or any other Linux distro for that matter

---

### Post by Muschnick on 2008-06-17
Anybody have any ideas on why I can't complete the upgrade?

---

### Post by avtolle on 2008-06-17
[http://www.mail-archive.com/ubuntu-studio-users@lists.ubuntu.com/msg00969.html](http://www.mail-archive.com/ubuntu-studio-users@lists.ubuntu.com/msg00969.html) indicates that the repository mirrors have changed. If I remember correctly, you will need to edit your /etc/apt/sources.list to reflect the change, as it is set out in the linked thread.

---

### Post by cariboo on 2008-06-17
archive.ubunutustudio.org doesn't seem to be available right now. I would wait just a bit and try again.

Jim

---

### Post by shifty_powers on 2008-06-17
well, seeing as you have a /home partition, you could go through a clean install, just WITHOUT formatting your home partition...

that way you will keep all of your data and configs, and then have a clean 8.04 install.... you amy need more advic on the install though....

plus if you follow the link in my sig, (the first one), you'll find a link explaining how to create a list of installed packages, and then use it on your new install ;)

---

### Post by Muschnick on 2008-06-17
avtolle....I am not sure what I would edit the /etc/apt/sources.list to....I think I know how to edit it but to what?

cariboo907.....I have been trying this for weeks so I can't imagine that is it but thanks....

Shifty....I am tempted to do the fresh install as I have backed up all my personal files I am concerned with....although being a beginner I am afraid I will never get the wireless connection working again among other configs I have...How much trouble will a beginner have with installing the latest version(I have the 8.04 CD) without screwing up my partitions and wireless setup??


Thank you all for your help!

---

### Post by avtolle on 2008-06-17
Muschnick, looking at the link I posted earlier suggests editing the /etc/apt/sources.list by deleting the lines referring to ubuntustudio.org, as the list is supposed to have the archive.ubuntu.org listings already in it. 

To edit, if you want to give it a go, in the terminal```
cp /etc/apt/sources.list /etc/apt/sources.list.bak #create a copy of what is there, just in case
sudo nano /etc/apt/sources.list #opens file for editing
```When you reach the lines referring to ubuntustudio.org, you may either delete them or comment them out by placing # before each.
Then, CTRL+o to write it out, <Enter> to save to the default name, and CTRL+x to exit nano.
After doing this, sitll in the terminal, refresh your sources list by```
sudo aptitude update
``` then try an upgrade by (still in the terminal)```
sudo aptitude upgrade
```
If you get any error messages, post them here. 
NB: In lieu of using aptitude in the above commands, you may use apt-get, if you desire. I prefer aptitude, but the choice is yours.
HTH.

---

### Post by Muschnick on 2008-06-17
I did that and this is what happened.....

$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  ffmpeg libdvdcss2 mencoder mplayer 
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Muschnick on 2008-06-17
I am trying the upgrade now through the update manager and it appears to be getting much further.....Thank you avtolle!!!

These forums are great and all you guys who respond take so much of your own time to help out others!!  You are awsome!!

I'll let you know if it works....

---

### Post by avtolle on 2008-06-17
Interesting "hold backs". Outside of suggesting enabling the medibuntu repositories, I've not any answer (presuming that you have not needed to enable the medibuntu repsoitories as you were running ubuntu studio).

EDIT: Just saw your latest post; sounds good, and good luck.

---

### Post by Muschnick on 2008-06-17
It worked!!  Yahooooooo!!  After 3 months of making myself miserable I make 1 post and avtolle tells me exactly what to do....Thank you avtolle and all the others who responded!!!

All I had to do is comment out the ubuntustudio.org lines in /etc/apt/sources.list and the upgrade went through

Thanks guys!  Now on to upgrading to 8.04!!  Lets hope this goes smoothly

---

