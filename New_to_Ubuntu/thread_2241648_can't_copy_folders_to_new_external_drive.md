---
title: "can't copy folders to new external drive"
date: 2014-08-27
forum: New to Ubuntu
---

### Post by Gnusboy on 2014-08-27
I can't figure out a problem with backing up to an external drive with Deja Dup Duplicity When I set it to copy my files (folders et. all) it comes up with an error and stops the process.
I've read through all the help threads and spent a lot of time trying to make it work, but it isn't cooperating.
I have an Samsung 1 TB external hard drive which Gparted shows as 2 partitions that are mounted and ready, but I  still can't copy anything over to it.
My system seems to be getting unstable (A variety of problems) so I want to make a backup and upgrade to Ubuntu 14.04 to solve that problem.
I tried several times to make the backup work in Deja Dup Duplicity, but finally turned it off because it kept copying the same folders over and over and kept freezing my system.

I'm running a fast system with 4 GB of ram which worked flawlessly until recently. I've tried everything I can find to copy my Home Folder to the new drive. So any help is appreciated.
  
Thanks.

---

### Post by yancek on 2014-08-27
You forgot to post the error you get so all we can do is guess.
What filesystem format is on the partitions on the external drive?  What are permissions?  Are you using sudo to copy?  You might need to do that.

---

### Post by Gnusboy on 2014-08-29
> **yancek said:**
> You forgot to post the error you get so all we can do is guess.
What filesystem format is on the partitions on the external drive?  What are permissions?  Are you using sudo to copy?  You might need to do that.

yancek
Thanks for the reminder. I had to leave and forgot to post them.

I'm not sure what you need, but gparted shows\

file:///home/jess/Pictures/Screenshot%20from%202014-08-28%2022:07:28.png

I wish I couyld do more tonight, but my system keeps freezing. Which is why I want to copy everything and upgrade to a newer Ubuntu. I'm so disgusted right now I might just might say f**k it and slick the drive. My computer and Ubuntu ran flawlessly for the past 4 years until a month ago when it started doing crazy stuff. It freezes for several seconds, videos that used to play without problem, now won't even open and when I switch to Chromium it gets stupider. I'm no genius and Ubuntu has been a learning experience, but it seems like a gremlin has taken over.
Yes, I know that this rant has nothing to do with what you needed me to post and I apologize. try to get you more info on the external drive as soon as I can.
Thank you

---

### Post by yancek on 2014-08-29
You need to post the image somewhere on line at a site which allows you to upload images and then link to it as we cannot see it on your local computer.

If your computer freezes frequently regardless of what you are doing, that is a sign it might be overheating so you might try cleaning it.  Also, check that the cables are secure for the external.

---

### Post by Gnusboy on 2014-08-31
Here's a Gparted pic of my external drive I want to use to backup. I've tried to move files to either of the partitions shown in this photo, but it didn't work.
Also, I can't seem to find out how to change permissions. The help files explain what should work, but it doesn't do it for me.
I desperately want to get this stuff backed up. I've been trying to do it for several weeks (part time) and nothing seems to work for me.
Is there an idiot's guide for backing up to an external drive? Deja Dup doesn't seem usable for me. I just found "Back in Time" Will that work? 
    
[IMG]http://farm4.staticflickr.com/3864/14914661038_083983c075_b.jpg[/IMG]

---

### Post by sotiris2 on 2014-09-01
If it is a permission issue we can fix that. First find out where the disks are mounted. You can see that in Gparted, mount point column. Or via command ```
 mount
``` You will have to identify them via UUID (the long string of characters and numbers you can see in your  screnshot, different for each partition) probably.  They seem to be mounted at /media/UUID.  

So to change the owner to you, so that you can write freely ```
sudo chown -R gnusboy:gnusboy /media/UUID
```

Of course if you use a different usename in ubuntu than forums you must change it in the command. Also change UUID to the actual UUID. 

Then you should be able to copy files to disk via your preferred method.

---

### Post by yancek on 2014-09-01
If you open a terminal and simply type:  ls -l /media/  you will get the owner:group as well as permissions.  You can use the chmod command to change permissions and it would need to be preceded with sudo.  Posting the output of the command above will give us something to work with.

---

### Post by Gnusboy on 2014-09-01
yanek

Here is the output: 

jess@Ranha:~$ ls -l /media/
total 20
drwxr-xr-x 4 root root 4096 Nov 24  2013 205504c6-6bf7-4fc0-a732-4ea634c2d00a
drwxr-xr-x 3 root root 4096 May 24 20:15 897fbe47-71a3-4afa-9722-109fc80bc2a4
drwxr-x--- 2 root root 4096 Dec 29  2012 apt
drwxr-xr-x 4 root root 4096 Nov 24  2013 d60ed036-350a-4524-833e-c91e7dd76fc3
drwxr-xr-x 2 root root 4096 Aug 16 13:52 mynewdrive

I get that I need that need to change the UUID as noted with the command offered by sotiris, "change UUID to the actual UUID" 
But where/how to I find the UUID? How would the command be written? Also do I need to change the permissions before entering new code?

Sorry I'm so dense about all this. All help is greatly appreciated.

---

### Post by sotiris2 on 2014-09-02
The UUIDs are 205504c6-6bf7-4fc0-a732-4ea634c2d00a and d60ed036-350a-4524-833e-c91e7dd76fc3 for the 430 gb and 500 gb partitions. From the output above your username is jess. 


So in order to change the owner of the 500gb partition 


```
sudo chown jess:jess /media/d60ed036-350a-4524-833e-c91e7dd76fc3
```


for the 430gb partition


```
sudo chown jess:jess /media/205504c6-6bf7-4fc0-a732-4ea634c2d00a
```


To leave the owner as root but allow yourself to write to the disks do 


```
sudo chmod 666 /media/d60ed036-350a-4524-833e-c91e7dd76fc3
```


and 


```
sudo chmod 666 /media/205504c6-6bf7-4fc0-a732-4ea634c2d00a
```

---

### Post by Gnusboy on 2014-09-03
Sotiris

I copied and pasted the codes you put up. So now what?
Do close the terminal and copy & paste my home folder?
Or do I need to use the terminal to move everything over to the new drives?

Sorry to take up so much of your time, but if I can get backups to a safe place then I can finally do the upgrade I need.

---

### Post by sotiris2 on 2014-09-03
Did you paste all of them? Only one set of them was necessary, the first set making you owner and the second allowing anyone to write on it. It won't break anything though. Now you should be able to copy the files in any way you want, either via nautilus (the default graphical files application) or via terminal.

---

