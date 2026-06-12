---
title: "Recommend a simple backup solution?"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by david_brown on 2014-02-19
I know there are quite a few around, but as it's only a simple home network I am looking for something simple with a GUI. No critical data, but stuff we want to keep up to date copies of in case of emergencies. I'm not going down the raid route - I have one big drive for data and one small drive for the OS only inside the server.

Firstly, it needs to be able to pull data - specifically from a shared hard drive plugged into the router. And secondly, it needs to be able to copy data from various files on several PC's. I'm wondering if a push arrangement would be better here (as long as it's a simple interface) so that family members can choose what they want to back up. I'm tired of being in the wrong for not backing up some obscure folder I didn't know was important on someone else's PC. Families eh?  Ideally, I'd also like it to push one of the folders on it's internal drive to another drive on another PC.

I'd be grateful for some advice here. Thanks.

---

### Post by Bucky Ball on 2014-02-19
Luckybackup could be for you. You can set up the backup job, give it a name, then anyone can run it quite easily. It's in the repositories. Have a play.

You can go for something like Clonezilla for less frequent backups. Clones the partition or the whole disk. You can clone the OS and make a bootable ISO even! Take your distro with you ... ;)

---

### Post by newbietwo on 2014-02-19
Deja Dup...simple, easy to use....reliable

---

### Post by mastablasta on 2014-02-19
another option is grsync

but luckybackup does seems to have a nice gui

---

### Post by Ubi_one_2014 on 2014-02-19
seems you got dead storage, like an USB drive
innitailly i thought to recommend you owncloud, or at least a sync server, like rsync
but bot options only suitable on a storage server like a NAS

therefore i recommend you symform.
10Gb free, [http://www.symform.com/](http://www.symform.com/)

i have storage based on contribution, up to 100Gb, for free
the pc must be on 24/7

---

### Post by Bucky Ball on 2014-02-19
Just adding that Luckybackup (and some others) has the ability to only backup what has changed since the last run of the backup job. Very quick unless a lot has changed. I've meticulously tested this out, right to the point of changing one character in the middle of one text document of a large backup up job. It only backed up the changed character and left the rest of the data from the last run as was. In other words, it worked faultlessly.

---

### Post by Buntu Bunny on 2014-02-19
Take a look at [MyPaint]("http://mypaint.intilinux.com/"). It's in the Software Center.

---

### Post by whitesmith on 2014-02-19
> **david_brown said:**
> I know there are quite a few around, but as it's only a simple home network I am looking for something simple with a GUI. No critical data, but stuff we want to keep up to date copies of in case of emergencies. I'm not going down the raid route - I have one big drive for data and one small drive for the OS only inside the server.

Firstly, it needs to be able to pull data - specifically from a shared hard drive plugged into the router. And secondly, it needs to be able to copy data from various files on several PC's. I'm wondering if a push arrangement would be better here (as long as it's a simple interface) so that family members can choose what they want to back up. I'm tired of being in the wrong for not backing up some obscure folder I didn't know was important on someone else's PC. Families eh?  Ideally, I'd also like it to push one of the folders on it's internal drive to another drive on another PC.

I'd be grateful for some advice here. Thanks.Consider SimpleBackup. It's configurable and does both full and incremental backups. You'll find it in the repos. Check it out. Cheers.

---

### Post by david_brown on 2014-02-19
Thanks - I am trying luckybackup first. So far I've downloaded it,and installed it but it won't run from the terminal when I type luckybackup when logged in as superuser. The error is 

> luckybackup: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory
david@ubuntu:~$
 I downloaded the amd64 version for 12.04 and installed it via webmin. Any ideas please?

---

### Post by sudodus on 2014-02-19
I recommend that you remove that version and install the version in the repository from the software center, synaptic or with the command line
```

sudo apt-get install luckybackup
```

By the way, you want a GUI version, but mentioning webmin makes me think you run Ubuntu Server? In that case what desktop environment have you installed?

---

### Post by david_brown on 2014-02-19
I'm running a small home server and access it by either webmin or terminal windo via a windows7 machine

---

### Post by sudodus on 2014-02-19
The problem with the version of LuckyBackup that you downloaded might be that

- you need libraries for graphics, if you want to run a GUI backup program, and/or
- the version you downloaded is too modern for the version of the server.

When you install packages from the repositories, they are tested for that particular version of Ubuntu, and much more likely to work. They should also be able to suggest which other packages (libraries etc) that must also be installed.

If still no go, I would install a desktop environment or at least a window manager (for example Openbox).

---

### Post by david_brown on 2014-02-19
OK - have uninstalled it but do not have a clue how to use the repository way of getting software. Can someone point me in the right direction please?

---

### Post by david_brown on 2014-02-19
Don't worry - have found out how to install stuff. Will have a play tomorrow to see if I can make it go. Thanks

---

### Post by Bucky Ball on 2014-02-19
Just a word; as far as I know, luckybackup will not run in a terminal. It is a simple GUI app. You can launch if from a terminal, but to its GUI, not the terminal.

---

### Post by epikvision on 2014-02-19
I would also recommend Deja Dupe if you're looking for a really simple backup solution.

---

### Post by david_brown on 2014-02-21
Having spent a couple of days on this, I've managed to get luckybackup to run by opening up an x server on Windows, and starting PuTTy with the xserver options. I have managed to mount an external hard drive attached to my router, set up a backup task and schedule and it's running. Steeeeeep learning curve :)

Silly question:- For this to work, all it needs is the hard drive on the router to be available (it is - 24/7) and the Ubuntu server that it's backing up to to be available at the time it's scheduled to back up? If I don't have the PC I'm using running, or shut the PC down it will still perform the backup on schedule as the PC isn't part of this - just the router drive and the server? The idea obviously is to set up tasks that just work provided the relevant boxes are on.

---

### Post by sudodus on 2014-02-21
In that case I suggest you skip the convenience of GUI applications and run a backup service with a text (command line) interface. You can make a shell-script with ***rsync***, run it manually, and when you are happy with it, make a ***cron*** job for example via a command line using
```
sudo crontab -e
```

Rsync is very powerful and flexible. The manual ```
man rsync
``` is quite good, but maybe it is easier to search for a ***tutorial*** via the internet and get an introduction.

---

### Post by Bucky Ball on 2014-02-21
What sudodus mentions is good advice and, while perhaps more of a learning curve, best for you. If the boxes allocated in the cron job are off at the scheduled time of the cron job (and if you don't schedule a time I think it goes for something like 6:25AM by default) then the cron job will run whenever all boxes are on and available. It don't mind. ;)

---

### Post by maglin2 on 2014-02-21
I've always used deja-dupe, but never actually need to do a backup from it.

I tried a little test today. I moved three unimportant files to the trash, and then clicked restore missing files. It quickly identified the correct three files as missing, but could only then actually find one of them to restore!

I think I may look for another backup solution.

---

### Post by Bucky Ball on 2014-02-21
! I'm unaware of any backup software that will take files out of the trash! :-k

---

### Post by kevdog on 2014-02-22
You have a lot of opinions in this thread for sure.  I've tried a number of backup solutions, however what I've found for me is that in many cases its easy to backup, however you only know how good your backups are when you have to restore something.  In some cases I thought I was making a backup, but then couldn't restore anything.  What a shame.

I'd hands down recommend a rsync backup.  It's not the most sexy, however its very reliable.  I'd also combine this possibly with sshfs if need be -- although you could use nfs, or samba as an alternative depending on the platforms your have.  You could run your rsync script to backup a folder tree, although if something were created outside this folder tree, it wouldn't be included. The rsync script could be run manually or automatically as suggested above via use of a cron job.  I usually rsync over ssh, however this requires you know how to setup an ssh server -- which isn't very hard but is a learning curve if you have never done it before.  Topics such a firewalls or access control lists usually appear when talking about running servers, so perhaps this might not be where you want to start.  

You should probably provide more details about your individual configurations.  That way this general discussion could become a lot more focused.

---

### Post by maglin2 on 2014-02-22
> **Bucky Ball said:**
> ! I'm unaware of any backup software that will take files out of the trash! :-k

Ah, you misunderstand - I wasn't expecting deja-dupe to restore the files from trash.

Those three files were initially in my /home/documents and home/pictures folders, which are part of my scheduled deja-dupe backup.

I then moved them - it happened to be to trash, it could equally have been to anywhere.

Deja-dupe correctly identified that they were missing (ie it identified they had formed part of the backup, and that it should have them stored at my backup location), but it then only managed to restore one of them, and said it couldn't find the other two.

What was weird was that for the two files that it failed to restore, what it did was create a new empty folder with original file names (but note that these had been files, not folders).

I will switch to a backup solution that doesn't used compressed archives, and so is easier to manually inspect for success.

---

### Post by Bucky Ball on 2014-02-23
> **kevdog said:**
> ... you only know how good your backups are when you have to restore something. 


Tell it like it is.

---

