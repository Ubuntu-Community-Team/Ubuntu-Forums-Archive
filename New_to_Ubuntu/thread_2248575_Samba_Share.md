---
title: "Samba Share"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by JWilliams8200 on 2014-10-15
Hello Ubuntu world!
I have been a hobby Ubuntu user for about a year now. I have 3 other computers in my house running another OS which im not proud of (lol) but other people in my house find that OTHER OS alot easier to use then Ubuntu. I on the other hand have been having a wonderful time learning and using Ubuntu.
Now to my problem.
I recently decided to share a hard drive on my computer, it is a seperate drive from my file system. It is used for storage only with music/movies/tv. I would like to share it with the other computers on my home network. I have read numerous tutorials on how to use Samba and how to set it up. I have gone through the process multiple times, and everything appears to be functioning normally. But i cannot see the shares on any devices. 

A side not i was running Ubuntu 12.12 i believe, Quantal Pretzel or something like that, i realized it was not a LTS so i have since switched to 12.04LTS, it is a fresh install and everything is working properly. I setup my samba shares like i had done previously. But nothing seems to be working. 

I am some what familiar with using the terminal, i just really dont know what to do now.

Someone please help me share my hard drive on my network!!!!!

---

### Post by mansonfan78 on 2014-10-15
From my own previous experience with this - I'm betting it's a firewall setting blocking access.  You probably need to set inbound traffic to allow connections from the ip addresses of your other computers.  You may also have to do something similar on your other machines.  Also (on the other machines) you would need to go to your file manager and select "connect to server" and enter in the location of the shared folder (ip address, share name).  There are ways to have these mounted automatically, but until you have it working you should stick to doing it manually.

---

### Post by sp40140 on 2014-10-17
Please provide more details: How did you try to create share. provide link to the page if you followed one specific tutorial. Have you tried to look at logs for errors? if not, please do so: /var/logs.
If possible look up sample smb.conf files online and compare it with the one in your machine : /etc/samba/smb.conf

---

### Post by bab1 on 2014-10-18
> **JWilliams8200 said:**
> Hello Ubuntu world!
I have been a hobby Ubuntu user for about a year now. I have 3 other computers in my house running another OS which im not proud of (lol) but other people in my house find that OTHER OS alot easier to use then Ubuntu. I on the other hand have been having a wonderful time learning and using Ubuntu.
Now to my problem.
I recently decided to share a hard drive on my computer, it is a seperate drive from my file system. It is used for storage only with music/movies/tv. I would like to share it with the other computers on my home network. I have read numerous tutorials on how to use Samba and how to set it up. I have gone through the process multiple times, and everything appears to be functioning normally. But i cannot see the shares on any devices. 

A side not i was running Ubuntu 12.12 i believe, Quantal Pretzel or something like that, i realized it was not a LTS so i have since switched to 12.04LTS, it is a fresh install and everything is working properly. I setup my samba shares like i had done previously. But nothing seems to be working. 

I am some what familiar with using the terminal, i just really dont know what to do now.

Someone please help me share my hard drive on my network!!!!!

You do not share hard drives at all.  You share a directory in a partition on a hard drive.  That can be a single partition and the root directory of that partition, but in the end it is a directory that you configure in Samba to be shared.  So the first thing that needs to be done is to crate an ext4 partition and mount it to the existing file system.  I use /srv/samba for this.  Is the partition ext and mounted someplace consistent in the file system?

You can follow this[ simple example]("http://www.jonathanmoeller.com/screed/?p=3967") using your existing directory that you want shared.

Here is a more [detailed answer]("http://ubuntuforums.org/showthread.php?t=2246424") to your question.   Read it completely and do ask questions about the parts you might not understand.

---

