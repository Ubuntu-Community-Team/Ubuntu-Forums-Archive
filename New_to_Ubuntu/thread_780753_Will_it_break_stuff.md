---
title: "Will it break stuff?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by AdNZL on 2008-05-03
I've been using Gutsy since about November last year, and have got it set up pretty much just the way I like it. All the little things that don't "just work" (Without a bit of patience... and sometimes a lot of patience)like playing DVD's playing WMP files in firefox and Java, are now working really really well. I also have a heap of programs, some from the repository and some just installed from normal downloads, like Google Earth and a bunch of others.

So here's my question, If I upgrade to Hardy will it break the things that I took so long to get working, such as java, DVD playback and encoding, ect? will I loose all my programs, or even some of them? I don't mind to much if it does as long as I get some warning and can prepare for it properly.

---

### Post by SunnyRabbiera on 2008-05-03
you should not have any problems with most of that stuff.
though expect a few hiccups

---

### Post by NIT006.5 on 2008-05-03
I haven't done my Hardy upgrade yet, but I had built up everything much like you on Feisty, and everything worked great when I upgraded to Gutsy. The only things I had issues with after upgrades were VirtualBox and TrueCrypt, but those were fixed easily enough.

---

### Post by SlappyPappy on 2008-05-03
Not to steal the thread but what kind of problems with Virtualbox? I need VB for a writing program and can't do without it.

I'm in Gutsy myself and loving it. I think I'm going to hold off the upgrade for a while as I'm crazy happy with it right now.  :)

---

### Post by mrzaius on 2008-05-03
You may see a hit in your multitasking ability, due to changes to the kernel process scheduler. That said, I can't tell the difference on my box.

---

### Post by volkswagner on 2008-05-03
One never knows what can happen.  Create a backup image of your happy system.  There are several ways to create a backup.  A few were mentioned recently.  I have had things break during non essential updates so be warned.

Here are a few.
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")
[http://www.partimage.org/Main_Page]("http://www.partimage.org/Main_Page")

My preferred way to get the latest and greatest is create an additional partition and install fresh (creating dual, triple, quad, etc boot).  If you have a happy system, move your files to the new os.  You can then slowly phase out gutsy. leave the old partition for the next greatest, or test OS.  It helps to keep your OS partitions small and create separate /home partitions, and /data partitions.

My two pennies worth.

---

### Post by AdNZL on 2008-05-03
Wow so many replies =D

Thanks everyone, especially volkswagner for the links, really really helpful stuff :D

---

### Post by tjwoosta on 2008-05-03
i have heard of many people here on the forums who have experienced problems updating Ubuntu 
( if i were you i would update the safe way)

partition disk and istall hardy beside gutsy (that way if anything goes wrong you still have a perfectly working O.S.)

but then you have to copy over most of the changes youve made like configs and stuff, but thats not usually a big deal 
(for instance for my hardy xorg.conf i simply copied the one from gutsy and used it to replace the one in hardy)

after all is setup and working correctly you can just delete the old partition and expand the new one

---

### Post by acelin on 2008-05-03
I have had no problems with Hardy other than its default look.

---

### Post by dondad on 2008-05-03
> **volkswagner said:**
> One never knows what can happen.  Create a backup image of your happy system.  There are several ways to create a backup.  A few were mentioned recently.  I have had things break during non essential updates so be warned.

Here are a few.
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")
[http://www.partimage.org/Main_Page]("http://www.partimage.org/Main_Page")

My preferred way to get the latest and greatest is create an additional partition and install fresh (creating dual, triple, quad, etc boot).  If you have a happy system, move your files to the new os.  You can then slowly phase out gutsy. leave the old partition for the next greatest, or test OS.  It helps to keep your OS partitions small and create separate /home partitions, and /data partitions.

My two pennies worth.
That is exactly what I did except that I use two different drives. I migrated from edgy to fiesty to gutsy to hardy that way. Works great, and with separate /home partitions in both setups, I can reinstall either to my hearts content without losing data.

---

### Post by w7kmc on 2008-05-03
I upgraded two systems simply using the upgrade manager from System -> Administration -> Upgrade Manager. One was a desktop, and the other a laptop.

For each upgrade I was asked about files that I had modified, and was given the option of keeping the original.  

The only issues I had was the wireless with my laptop (expected and cleared up using ndiswrapper) and a very slow Firefox 3 browser on both systems 

I understand the Firefox 3 browser slowness is a known issue, so until it is cleared up, I just use Firefox 2. 

Everything else works great! Granted, these are fairly baseline systems, but flash, media players, etc. all worked out of the box with the settings I had.  

I think your mileage will vary depending on how much you have "tweaked" the system.  But pretty much baseline installs should go ok. I would heed the previous posts about backing up before you take the plunge.

---

### Post by tjwoosta on 2008-05-04
really?
i havn't had any problems with firefox3.

actually i think my firefox3 is alot faster than my firefox2 was in gutsy

---

### Post by nowshining on 2008-05-04
> **mrzaius said:**
> You may see a hit in your multitasking ability, due to changes to the kernel process scheduler. That said, I can't tell the difference on my box.

What exactly do you mean?

---

### Post by philinux on 2008-05-04
For a snapshot backup of your system use this.

[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

---

### Post by volkswagner on 2008-05-04
phillinux,  that link is broken.

[http://www.remastersys.klikit-linux.com/]("http://www.remastersys.klikit-linux.com/")

Glad I found this.  I saw this weeks ago, but did not save it.  Now I got it.  :)

---

