---
title: "WTF! missing disc space, VIRUS?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by SRG8 on 2008-07-04
I just experienced some very weird events over the past few hours with my hardy and computer overall. all of a sudden my mozilla and other browsers stopped working so i restarted my pc and then compiz was a little quirky, if i clicked on the power button it would shut off instead of giving me the option to log off etc. i know i had connecton cause pidgin was working fine. 
whats weird is that it says now that i have no more disc space left, only about 5GB. last time i checked i had at the very least 80GB of free space a couple days ago :P i havent downloaded anything. just a few minutes ago everything went back to normal except the free space.
Is there a way where i can see exactly whats using up my hard disc? i went to my home folder where all my files videos and music are and it says its only 40GB. My disc is 135GB!! i think i know how to substract and 135 minus 40 does not equal 5!!!
Is someone else using my hard disc? is that possible? virus?

---

### Post by hyper_ch on 2008-07-04
if you have no diskspace left, then that behaviour is normal....

run:

```

sudo fdisk -l

```

and

```

df -l

```

and post the output here

---

### Post by SRG8 on 2008-07-04
heres what i got, thanx

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bec8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17629   141604911   83  Linux
/dev/sda2           17630       17693      514080   82  Linux swap / Solaris
sergio@sergio-laptop:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            139381772 127898840   4402688  97% /
varrun                  512860       104    512756   1% /var/run
varlock                 512860         0    512860   0% /var/lock
udev                    512860        52    512808   1% /dev
devshm                  512860        52    512808   1% /dev/shm
lrm                     512860     38684    474176   8% /lib/modules/2.6.24-19-generic/volatile

---

### Post by ChameleonDave on 2008-07-04
97%?  That's a hell of a lot.  Try emptying your trash and then check again.

Do you have the program filelight?  If not, try installing (if you don't have enough space to do so, delete some other program to make room).  Use it to see what is filling up your hard drive.

---

### Post by SRG8 on 2008-07-04
it didnt make any difference after emptying the trash so i installed the filelight and apparently whats eating up my hard drive is var backups, i do remember installing a backup software to keep backups but i didnt know they took up so much space =S ! i'm going to try getting rid of most of the backups and see if that works, thanks for the tips, il post later if it worked

---

### Post by SRG8 on 2008-07-04
indeed the backups are eating up my hard drive, 75GB of it at least. 

but ok so apparently i cant delete any of them b/c i dont have permission and i cant change permissions b/c im not the 'owner' 'root' is the owner

---

### Post by drs305 on 2008-07-04
> **SRG8 said:**
> indeed the backups are eating up my hard drive, 75GB of it at least. 

but ok so apparently i cant delete any of them b/c i dont have permission and i cant change permissions b/c im not the 'owner' 'root' is the owner

```
gksu nautilus
```
will open nautilus with administrator privileges and  let you navigate to the files and delete them.

---

### Post by Marshal0505 on 2008-07-04
> **SRG8 said:**
> indeed the backups are eating up my hard drive, 75GB of it at least. 

but ok so apparently i cant delete any of them b/c i dont have permission and i cant change permissions b/c im not the 'owner' 'root' is the owner

So you open your filebrowser with the sudo command and delete what you want to delete, for instance...
```
gksu nautilus
```

it will ask for a pass, use your account password.

---

### Post by SRG8 on 2008-07-04
thanks i was able to delete them. filelight says the only thing really taking up hard disc space is my home folder 40GB, but when i open a folder it still says only about 5GB of free space so i checked in partition manager my sda and it says theres 11GB of free space. 
I'm confused which one should i ttrust and why are they not agreeing with each other

---

### Post by Victormd on 2008-07-04
Try
```
sudo apt-get clean
```
This will remove the backed-up packages downloaded during your updates
Also, clean up your packages by removing the ones that are no longer required:
```
sudo apt-get autoremove
```

---

### Post by SRG8 on 2008-07-04
thanx but that only removed 600MB, theres 75GB

---

### Post by drs305 on 2008-07-04
You may have un-emptied trash hidden in various places. You can run this command to find the various Trash files. The actual trash will be in the "files" subfolder. Use  the aforementioned "gksu nautilus" to delete them.

```
sudo find / -type d -iname Trash
```

---

### Post by zekica on 2008-07-04
Can you please post result of this command, it should take a few minutes at most to complete:

**sudo du / | sort -n | tail**

It will return folders that take up the most space on your hard drive.

---

### Post by SRG8 on 2008-07-04
sorry about the delay computer is starting to act a little slower, im assuming b/c of the lack of space.

this is what i got with :sudo du / | sort -n | tail

du: cannot access `/proc/6524/task/6524/fd/4': No such file or directory
du: cannot access `/proc/6524/task/6524/fdinfo/4': No such file or directory
du: cannot access `/proc/6524/fd/4': No such file or directory
du: cannot access `/proc/6524/fdinfo/4': No such file or directory
18207788	/home/sergio/Videos/peliculas
21864732	/home/sergio/Videos
42303968	/home/sergio
42303972	/home
79656248	/root/.local/share/Trash/files
79656424	/root/.local/share/Trash
79656608	/root/.local/share
79656612	/root/.local
79664952	/root
126328916	/

---

### Post by hyper_ch on 2008-07-04
(1) when you post output or commands enclose it in those brackets, that makes it easier to read [noparse]```

```[/noparse]

(2) how do you backup?

---

### Post by SRG8 on 2008-07-04
ok,
 i back up using Simple Backup i found in add/remove. im not really used to terminal so i avoid it when i can.

above it showed a certain trash folder which occupied 79GB, i managed to find it after a while and it was empty =S

---

### Post by SRG8 on 2008-07-04
nevermind i looked at the wrong one, now i found the right one and indeed there are all those backups i had deleted, their just hidden. i tried deleting them and they disappear for about 1 second before they come back!

---

### Post by aktiwers on 2008-07-04
Did you already go to your root trash and empty/delete the files from there?

```
gksudo nautilus /root/.local/share/Trash
```

And delete the files? Also remember to stop your backup program from making more backups

---

### Post by hyper_ch on 2008-07-04
delete them from the shell... or press "shift" from the gui to directly delete them and not move them to the trash... I think you deleted them to the trash ;)

as for backups, have a look at rsync...  and the CLI is your friend ;)

---

### Post by aktiwers on 2008-07-04
This one is pretty need too..
[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

---

### Post by SRG8 on 2008-07-04
yea i am there and have pressed delete many times but they seem to be deleted for about 1 second before they reappear again. when i right click to select delete, theres no delete, only move to trash. Im assuming it just moves them from the trash to the trash. i also dont see anywhere where i could select to empty it.

---

### Post by hyper_ch on 2008-07-04
delete the files using the CLI ;)

---

### Post by SRG8 on 2008-07-04
alright im back upto 80GB!!!! thanks so much everyone, learned some new tricks as well

---

### Post by drs305 on 2008-07-04
> **SRG8 said:**
> yea i am there and have pressed delete many times but they seem to be deleted for about 1 second before they reappear again. when i right click to select delete, theres no delete, only move to trash. Im assuming it just moves them from the trash to the trash. i also dont see anywhere where i could select to empty it.

If these are in the root trash folder:
```
cd /root/.local/share/Trash
sudo chown -R **username** files
rm -R files
```

This is not the most direct way to delete root files via the command line but it will help prevent an inadvertent deletion of critical system files by misuse of 'sudo rm -R'...

---

### Post by MrWES on 2008-07-04
I too thank you. Recently I noticed my / filling up and I couldn't figure where the files where coming from. Never thought to look in root .trash. Is there a script that would clean that out periodically?

Bill

---

### Post by ChameleonDave on 2008-07-04
> **MrWES said:**
> I too thank you. Recently I noticed my / filling up and I couldn't figure where the files where coming from. Never thought to look in root .trash. Is there a script that would clean that out periodically?

Bill

Well, yeah, you could add the following line to /etc/crontab:

```

11 13   * * 1   root   rm -fr /root/.local/share/Trash/*

```

That will clean out root's trash every Monday afternoon.

There are more complicated and elegant ways to do it though.

---

### Post by MrWES on 2008-07-06
Such as? :)

---

### Post by ChameleonDave on 2008-07-06
> **MrWES said:**
> Such as? :)

Well, my little suggestion is quite crude.  If you send a file to the trashcan just after it's emptied, that file won't be flushed out for a whole week; whereas if you send a file to the trashcan a minute before it's emptied, that file will only survive a minute!  Also, if your computer is not switched on at the time assigned to emptying, then the emptying will be skipped for the week.  It also does not take into account how many files are in the trash.  It would be better to empty it more frequently if it's full.

I could spend a long time writing a complicated bash script to automate all that in a beautifully logical and foolproof way... but I can't be bothered.  I prefer to empty my trash manually anyway!

Somebody will probably end up writing some fancy "Advanced Trashcan" program with a nice graphical interface for KDE 4.  But not me!

---

