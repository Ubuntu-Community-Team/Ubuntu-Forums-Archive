---
title: "Hosting my own repository"
date: 2006-02-17
forum: Repositories &amp; Backports
---

### Post by crashman0 on 2006-02-17
Hi all,

At school I setup a small network lab minus Internet access. I want to use ubuntu as my choice for the desktop OS. I would like user's to be able to use apt-get (most likely synaptic) to add apps. 

My plan is to set up 1 computer to act as a repository and have all the desktops connect to it. To keep this repository up to date I want to download the repository at my home computer (cable modem) place it on a DVD/external HD and use it to update the repository in the lab.

Here are my questions, btw I am a lousy googler, so if you respond with "just google it" please provide me with the search words to use, 1. What services do I need to setup on the lab repository computer so that can connect to apt-get? 2. How do I get access to a repository to copy? I don't want to just grab and run, I'd like to have permission, if needed, so that I can copy like Ubuntu's official repositories.

Thank you,
crash

---

### Post by az on 2006-02-17
[QUOTE=crashman0]
1. What services do I need to setup on the lab repository computer so that can connect to apt-get? [/QUOTE]

Either apache to run a http repository or NFS to make it a filesystem repo

Ex:
deb [http://192.168.0.101/ubuntu](http://192.168.0.101/ubuntu) breezy main universe restricted multiverse

deb file:/repo/ubuntu breezy main universe restricted multiverse

Those would be then entries in the client's apt sources.list to access your repo hosted by apache or by nfs.


[QUOTE=crashman0]
2. How do I get access to a repository to copy? I don't want to just grab and run, I'd like to have permission, if needed, so that I can copy like Ubuntu's official repositories.

Thank you,
crash[/QUOTE]

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

Use that to create a repo on a cd or DVD.

You do not need any permission to grab and run.  This is free-libre software.  Just be sure to provide the source, as well, to comply with the GPL.

---

### Post by crashman0 on 2006-02-17
Thanks that was very helpful. I just have 1 more question. As I read through the instructions for moving a repository on to a CD I still at the end of the tutorial end up with a CD that I can use as a repository, which means I need to hand out to a user everytime they want to add an application. Is it possible to copy the directory structure on the CD on to a HD of my repository server? If I can so that, do I just put it under one of the public appache folders "/var/www/<forget the rest>/"?

Thank you again,
Martin

---

### Post by az on 2006-02-18
About providing the source, you don't need to do that if you are just deploying ubuntu in your computers that some others will be using.  Now if this is a lab where people will come in and connect to your network to install ubuntu, you should be able to provide the source for them if they ask.  But if these are your boxes on your network, never mind about distributing the source - you are not distributing Ubuntu in this case.




[QUOTE=crashman0]Thanks that was very helpful. I just have 1 more question. As I read through the instructions for moving a repository on to a CD I still at the end of the tutorial end up with a CD that I can use as a repository, which means I need to hand out to a user everytime they want to add an application. Is it possible to copy the directory structure on the CD on to a HD of my repository server? If I can so that, do I just put it under one of the public appache folders "/var/www/<forget the rest>/"?

Thank you again,
Martin[/QUOTE]

Apt-move will create to local repository, which you can move to another computer by copying it to a cd.  You just copy it back.

---

### Post by nanotube on 2006-02-19
you might also consider using the "apt-proxy" package. look for it in synaptic. seems like that would do exactly what you want, and automatically, to boot.

---

