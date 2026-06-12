---
title: "[SOLVED] Reinstalling Ubuntu"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by dwally89 on 2008-05-12
Hi,

I have my /home directory on its own partition, and I store my data (videos, photos, documents etc) on their own data partition too.

So if I was to reinstall Ubuntu, would I actually lose anything?

Thanks

---

### Post by mister_pink on 2008-05-12
You'd have to make sure that when you do the reinstall you do manual partitioning and tell it to mount you /home partition correctly. All you stand to lose is the extra programs you have installed and any customisation you made to system files. Once you reinstall programs though they will use their current settings as most of them are in your home directory.

Is there anything in particular you're worried about? Bear in mind its always worth a backup of anything important, and make sure the format box isnt ticked next to /home when you do the manual partition!

---

### Post by DeathStar on 2008-05-12
It totally depends on how careful you are when you do it. If your /home directory is on it's own partition (which is the way I always do it), then you can reinstall and only format you / (root) partition. You need to tell it to leave the /home partition alone. I made the mistake one of just telling it  to format the home partition as well! :(

You should be fine. Just be careful to tell it to leave the /home partition alone!

---

### Post by Mr A Mouse on 2008-05-12
Theoretically speaking ... no. Your file permissions would no longer point to a user account, but that can be taken care of with a command called "chown."

Practically speaking ... anything can happen. If you monkey with the partition table, it can accidently destroy the table, leaving you with an unusable drive that must be reformatted. 

My advice--always backup to separate media, whether it be CDs/DVDs, another physical drive, or a "cloud backup" of some sort.

---

### Post by dwally89 on 2008-05-12
What's a cloud backup?

---

### Post by Mr A Mouse on 2008-05-12
Some form of online backup service--you know, your files are "out on the cloud." ;)

---

### Post by Het Irv on 2008-05-12
As long as you don't delete those partitions,  after the install I think you have to remap the /home partition to /home.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by dwally89 on 2008-05-12
OK Thanks.

I'm not actually planning on reinstalling any time soon, but just wondered when the time came, how easy it would be, and if I would lose anything.

---

### Post by dwally89 on 2008-05-12
So to clarify, after the reinstallation, would I have to do anything to make my computer the same as it was before?

---

### Post by forestpixie on 2008-05-12
> **Het Irv said:**
> As long as you don't delete those partitions,  after the install I think you have to remap the /home partition to /home.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


When you reinstall - edit the /home partition - you will get the option to set mountpoint - it has to be /home again - as has already been said don't mistakenly click the format box and you should be fine.

In the same manner to get the install over the original - give that partition a mountpoint of /

Always make sure you have backups - I didn't and had problems

---

### Post by dwally89 on 2008-05-12
Would I have to reinstall all my programs again?

---

### Post by forestpixie on 2008-05-12
Yes - but configs are usually in /home.

---

### Post by dwally89 on 2008-05-12
OK Thanks

---

### Post by H.Callahan on 2008-05-12
I haven't done this myself yet, but I ran across [this HowTo: Create a list of installed packages](http://ubuntuforums.org/showthread.php?t=261366) which looks like it would be just the ticket for finding currently installed packages and then being able to reinstall them after a clean OS install.

---

### Post by dwally89 on 2008-05-12
Thanks.

I've only been using Ubuntu since January, and love it when I find things in Ubuntu that are better than Windows.
Another one to add to my list now :-)

---

### Post by H.Callahan on 2008-05-12
I'm a newbie myself.  I love it when I can actually help someone else out.  It happens so seldom...  :D

---

### Post by Het Irv on 2008-05-12
> **H.Callahan said:**
> I'm a newbie myself.  I love it when I can actually help someone else out.  It happens so seldom...  :D

Keep up the effort, you would be surprised how quick you can learn, I have only been using Linux for a year.:lolflag:

---

