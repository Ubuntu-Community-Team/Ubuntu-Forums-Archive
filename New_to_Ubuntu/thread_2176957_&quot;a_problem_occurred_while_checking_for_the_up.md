---
title: "&quot;a problem occurred while checking for the updates&quot;"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by arai on 2013-09-26
When I try to open Ubuntu Software Centre it quits. I also see a "-" icon on right hand side top of the screen, it states a problem occurred while checking for the updates.

Help me overcome this trouble.

Thanks in advance.

---

### Post by ibjsb4 on 2013-09-26
What happens if you update in terminal?

```
sudo apt-get update
```

---

### Post by arai on 2013-09-27
I get this

> sudo apt-get update
[sudo] password for h1: 
E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.


I am unable to update packages please help me.

---

### Post by arai on 2013-09-27
hi Saint, thanks for your reply. Yes, I was waiting for somebody to reply. Also I was thinking of doing a complete reinstallation.

Thanks again for taking your time to read my question and writing a reply.

No I am not Japanese. But I wish I am a Japanese for their brain power and technology development. :D

---

### Post by westie457 on 2013-09-27
What does ```
cat /etc/apt/sources.list
``` tell us

---

### Post by ibjsb4 on 2013-09-27
> **westie457 said:**
> What does ```
cat /etc/apt/sources.list
``` tell us

Make that code:

```
cat -n /etc/apt/sources.list
```

..:)

---

### Post by grahammechanical on 2013-09-27
Do not be quick to re-install. What do you see when you click that icon? Have you tried some of the options in that menu?

The next time you boot select Recovery Mode and at the Recovery menu select dpkg - repair broken packages. That will run a script that will run these commands.

> rm /var/lib/pat/lists/partial/*
rm /var/cache/apt/archives/partial/*
dpkg --configure -a
apt-get update
apt-get install -f
apt-get dist-upgrade

In just a few clicks a lot of fixing can be done with Recovery Mode.

Regards.

---

### Post by arai on 2013-09-27
hi friends, thanks for all your reply. But I had to reinstall Ubuntu. 

Some error while updating happened. 

Now, after fresh reinstall it is working fine.

I have two other minor issues if anybody could help I would be happy. I don't know if this forum would be apt for that. Anyway, 

I have Ubuntu 12.04 LTS 32 bits on one partition, Windows 8 64 bit on another partition. 

While in Ubuntu everything works fine, in Windows 8 64 bit 

1) I see time always showing wrongly. 

2) And the sound doesn't play when I plug in the headset. When I remove the headset the sound plays normally. I tested with two different headsets. Both headsets doesn't work in windows 8 64bit. 

As said earlier everything works perfectly in Ubuntu. Anybody could help resolve this issue?

---

### Post by ibjsb4 on 2013-09-27
You have marked this thread "Solved".  People will not look at it anymore, better to start a new thread with your new problem in the title :)

---

### Post by arai on 2013-09-28
Sorry Changed it now. Can the two problems mentioned be solved ?

> While in Ubuntu everything works fine, in Windows 8 64 bit 

1) I see time always showing wrongly. 

2) And the sound doesn't play when I plug in the headset. When I remove the headset the sound plays normally. I tested with two different headsets. Both headsets doesn't work in windows 8 64bit. 

It is a lenovo laptop.

---

### Post by Gyokuro on 2013-09-28
1.) disable network time either in windows or ubuntu

---

### Post by Jonathan Precise on 2013-09-28
Please mark this thread as solved by going to thread tools and start a new thread about the other 2 topics.

---

