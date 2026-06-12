---
title: "Cant share folder in 8.04"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Faud on 2008-05-07
```
net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
```
Is the message I get when I try and create a share so that my wife (also using 8.04) can see a folder in my home folder.

---

### Post by mtonsbeek on 2008-05-07
When you go into System>Administration>Services>Unlock, enter password and enable Samba File Sharing.

That should do the trick

---

### Post by Faud on 2008-05-07
Thank you very much.

---

### Post by mtonsbeek on 2008-05-07
Cool! You are actually the first person I have been able to help with my very limited and new knowledge of Ubuntu! Normally I am the one asking for help.

---

### Post by SonicSteve on 2008-05-07
> **mtonsbeek said:**
> When you go into System>Administration>Services>Unlock, enter password and enable Samba File Sharing.

That should do the trick

What would you say if I've already enabled this but I still have the same error as Mtonsbeek?

---

### Post by stchman on 2008-05-07
> **Faud said:**
> ```
net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
```
Is the message I get when I try and create a share so that my wife (also using 8.04) can see a folder in my home folder.

Best way to share between Linux machines is to use NFS.

---

### Post by bodhi.zazen on 2008-05-07
The user creating the share must have permission to access the shared directory, so check permissions of /var/lib/samba/usershares , or what ever directory you are sharing.

samba is more secure then nfs

---

### Post by SonicSteve on 2008-05-07
> **bodhi.zazen said:**
> The user creating the share must have permission to access the shared directory, so check permissions of /var/lib/samba/usershares , or what ever directory you are sharing.

samba is more secure then nfs


I have no permissions for var/ lib/ samba/ usershares
Should I by default have access to this folder? If so what should I do chown it? What permissions should I have?

---

### Post by bodhi.zazen on 2008-05-07
Typically one shares a directory from within their home.  Otherwise, yes if you want to share that directory you will need to change the permissions, which may have system or security implications.

If needed, I would create a new group, call it samba (this group may already exist). Add your user to the this group and make the directory in question owned by root.samba

---

### Post by SonicSteve on 2008-05-08
> **bodhi.zazen said:**
> Typically one shares a directory from within their home.  Otherwise, yes if you want to share that directory you will need to change the permissions, which may have system or security implications.

If needed, I would create a new group, call it samba (this group may already exist). Add your user to the this group and make the directory in question owned by root.samba

I have been sharing folders from my home folder. However in gutsy 7.10 I could share folders from any folder that owned and it was quite easy to setup. Something seems to be wrong in hardy 8.04. (I'm using both codename and version # to help new users).

---

### Post by life4himsq on 2008-05-08
Ok, so after looking at bug reports, I saw that you need to reboot after installing the sharing even though it doesn't say to. Also make sure that in System---Administration---services the Folder sharing service (samba) is checked. You will have to click unlock to change any services. I just did the reboot after getting the error and it works now. Hope this helps.

---

### Post by bodhi.zazen on 2008-05-08
> **life4himsq said:**
> Ok, so after looking at bug reports, I saw that you need to reboot after installing the sharing even though it doesn't say to. Also make sure that in System---Administration---services the Folder sharing service (samba) is checked. You will have to click unlock to change any services. I just did the reboot after getting the error and it works now. Hope this helps.

You need to log out an then back in. You may reboot if you like, but for those uptime fiends, reboot is not requited :twisted: :-\"

---

### Post by life4himsq on 2008-05-08
Cool thanks, I was dreading the reboot but did it anyway. I do like my uptime.

---

### Post by matthiasj on 2008-05-10
I can share folders on my internal hard drive that 8.04 is installed, but I can't share folders on my external hard drive, i want to put it on the network for backups and centralized place for files.  I get the net usershare 255 error when trying to share a folder on the external.

---

### Post by scott@matheson.com on 2008-05-11
Hi I have just tried this and still get te error do you keep the service window open then go and share ?

---

### Post by scott@matheson.com on 2008-05-11
I want to share a folder to a MAC so NFS would be a good methord, could you give me the steps I should follow to create a folder can be shared using nfs  

the share inthe GUI is onle for SMB

---

### Post by DeMartini on 2008-07-27
Thanks so much for all the help, a simple restart was all I needed as well...

---

### Post by Yfrwlf on 2008-08-16
Yes, thanks for the help on this thread.  I assume this is a bug with Samba with the whole permissions issue.

As for sharing an external drive, it *should* let you by default, but I don't think it does which is something they need to change.  The problem is ownerships don't change until you force them to, so files on some other device normally won't be owned by you, and they don't want to make it change ownership otherwise it could hose someone up if they wanted it that way.  Perhaps just all Linux file permissions just needs a 21st century update to allow for scenarios like this one while still being able to be secure.  Strange thing is I thought the access to user auto mounted devices was solved.  Weird.

Any way, first check to make sure you can share out folders in your home folder, and if that is working but mounted media sharing isn't, you can fix it like this:

```
sudo chown -R your_user_name /media/name_of_mounted_device
```

I really hope Gnome throws something into gvfs or whatnot to help users with the mounting of new devices and ownership issues, *somehow*.  With mem sticks you don't have to worry because they are FAT32 and don't have ownership, but other partition types need to be dealt with in a better way that doesn't force users to drop to a terminal and learn stuff they shouldn't have to.

---

### Post by UnaXdk on 2008-09-02
Thanks a lot, that was just what I needed :)

---

