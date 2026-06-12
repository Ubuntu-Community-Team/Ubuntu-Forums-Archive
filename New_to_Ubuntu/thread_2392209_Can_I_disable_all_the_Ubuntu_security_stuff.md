---
title: "Can I disable all the Ubuntu security stuff?"
date: 2018-05-17
forum: New to Ubuntu
---

### Post by zipkode on 2018-05-17
Moderators, forgive me if I've posted in the wrong place -- I'm new to the forum.

I am giving a laptop to an older person who is unfortunately not well.  I've loaded Ubuntu [Gnome] on it, in hopes that the user
will be able to have an easy time using it.  I will not be present or available to coach them, so I'm hoping I can get the machine to
behave as much like Windows as possible.

To that end, can I disable all the security checks when installing apps/updates?  My concern is that older folks (especially those with health issues) would find
it a barrier to entry -- and I'm trying to keep this user as in-touch with the outside world as possible.

Most grateful for your help.

---

### Post by wildmanne39 on 2018-05-17
If you disable the user password that is created when ubuntu is installed then they will not be able to install updates and I will leave the risks of doing that to someone else. I have seen many people do this in the past only to come here for help to restore the password because of not being able to install updates.

---

### Post by mastablasta on 2018-05-18
> **zipkode said:**
> 
To that end, can I disable all the security checks when installing apps/updates?  M.

don't disable security. work with it. for example use unnatended upgrades: [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

also install a software that will give you access to their either desktop or at least the PC so you can solve the issue on distance (e.g. SSH access with keys):
[https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

more (GUI access): 

[https://websiteforstudents.com/access-ubuntu-17-04-17-10-remotely-windows/](https://websiteforstudents.com/access-ubuntu-17-04-17-10-remotely-windows/)

[https://www.makeuseof.com/tag/how-to-establish-simple-remote-desktop-access-between-ubuntu-and-windows/](https://www.makeuseof.com/tag/how-to-establish-simple-remote-desktop-access-between-ubuntu-and-windows/)
[https://www.lifewire.com/setup-ubuntu-remote-desktop-4129666](https://www.lifewire.com/setup-ubuntu-remote-desktop-4129666)


alos teamviewer might also be an option:
[https://www.teamviewer.com/en/download/linux/](https://www.teamviewer.com/en/download/linux/)

---

### Post by kerry_s on 2018-05-18
have a look at endless os. it self updates, it's secure.
[https://distrowatch.com/?newsid=10210](https://distrowatch.com/?newsid=10210)

it's what i use for my mom. you can also run it live to test everything out, make sure things work.
i used the basic version.

---

### Post by Autodave on 2018-05-18
My mom and another rather old relative both have Linux machines. I use Teamviewer to keep both of them running and to fix things that they manage to screw up. Teamviewer is very easy to set up and get running.

---

### Post by zipkode on 2018-05-22
Extremely helpful -- thank you all.

---

### Post by darthvader0 on 2018-05-23
> **zipkode said:**
> 
To that end, can I disable all the security checks when installing apps/updates?  My concern is that older folks (especially those with health issues) would find
it a barrier to entry -- and I'm trying to keep this user as in-touch with the outside world as possible.

Most grateful for your help.
Correct me if I'm wrong, but Windows itself has its own security. I'm not sure why you want to disable any and all security, one of the major traits of of Linux is its security especially compared to windows.  Why not give the older folks a tablet, if you're concerned about them not being able to handle updates and what not

---

### Post by fyfe54 on 2018-05-23
Teamviewer.  My mother-in-law is 92 and I just switched her to Ubuntu after a particularly nasty piece of malware struck.  One smallish SSD, Ubuntu Bionic and Teamviewer later, she is in business with Facebook, email etc.  She messes things up and finds it difficult sometimes but I can help her and explain.

---

