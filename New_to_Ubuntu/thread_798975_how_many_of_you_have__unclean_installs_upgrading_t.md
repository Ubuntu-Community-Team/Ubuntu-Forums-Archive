---
title: "how many of you have  unclean installs upgrading to hardy heron with update manager?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by thebestofall007 on 2008-05-18
hi, i was wondering how many of you have had problems with an unclean upgrade using the update manager to upgrade from gutsy to hardy versus a fresh install. i certainly have.

like: 
1. getting parsing errors when i click on audio streams loaded onto panels or click certain apps, like a shortcut to innotek virtualbox loaded onto the desktop.
2. less stability (like if, when testing stability, opening a lot of videos; with gutsy i was able to open up to 60, with 1gb of ram on my acer laptop)
3. the "ask me" option doesn't work even when i select it. instead of giving me the menu of what i want the computer to do, it just goes to the login screen when i press the power button.
4. slower and clumsier boot up. the boot up splash screen shows at first, then pauses, then gives a black screen with the text, then goes to the login screen. when i have no internet connection available, the boot up is even slower.


for now, i have went back to gutsy, but i am wondering how hardy does with a boot install versus clicking the "upgrade" button in update manager? i ask because i have tried hardy in innotek and didnt have these problems.

---

### Post by JoshuaRL on 2008-05-18
I haven't had that many issues, but I have had some.  The driver keeps reverting to the open source and messing with my resolution.  I have a bug in compiz, so I just stopped using it.  Also, the upgrade faulted most of the way through and I had to do:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get update-manager -d

```
and it finished everything alright.  The compiz bug is on Launchpad, so hopefully it will be fixed soon.  Not sure about the driver issue though.

---

### Post by umfas on 2008-05-21
how did you rol back to gutsy?

---

### Post by Inxsible on 2008-05-21
I didnt upgrade on my ubuntu machine. But I did on my Xubuntu and everything is working just as it should. No problems whatsoever.  Except for the 1 hour download and 2.5 hours installation time :(  I would think that a fresh install would have been much faster. But oh well !!!

---

### Post by reeksy on 2008-05-21
Hi

I've upgraded via the package manager and had several issues! I can no longer access my CD drive and I'm getting system crashes every 2-3 days. The previous version of Ubuntu was excellent, i never had any issues! I wish i could roll back!

I notice you're talking about a fresh install. By this do you mean re-formatting you HD? Is this common practice with Ubuntu Linux when upgrading? It seems like a lot of effort; as you'd have to back-up all your files (on DVD or something). However, due to the issues I'm having I'm seriously considering it though.

Jon

---

### Post by TransitMan on 2008-05-21
If you have a separate /home directory, doing a fresh install would be easy.

As for the upgrade via the update manager, I had no problems. Just has to re-install Innotek Virtualbox to get it to work, and I was good to go. In fact, I installed the RC version just prior to the official release.
As for video, I had to re-install the ATI drivers, but that was not a big deal.

---

### Post by reeksy on 2008-05-21
> **TransitMan said:**
> If you have a separate /home directory, doing a fresh install would be easy.

By this do you mean /home/<my username>?  If the answer is yes, then i do. So i guess you mean you would only have to backup and restore your /home/<my username> directory if you did a fresh install?

Regards,
Jon

---

### Post by avtolle on 2008-05-21
> **reeksy said:**
> By this do you mean /home/<my username>?  If the answer is yes, then i do. So i guess you mean you would only have to backup and restore your /home/<my username> directory if you did a fresh install?

Regards,
Jon
What the question really was asking was "do you have a separate /home partition on your hdd?". If you have created such a partition in the past, then you would only need to backup said partition prior to a fresh install. If you do not have a separate partition for /home, then you have a bit more work to do to back up the /home/<username> "folder", as this will be overwritten by a new install, and you would need to restore from your backup.

---

### Post by reeksy on 2008-05-21
I see, OK thanks for the info.

---

### Post by thebestofall007 on 2008-05-22
> **umfas said:**
> how did you rol back to gutsy?

i backed up my data and started off with a fresh boot install from a gutsy live cd. thats the only way i know of to roll back.

---

### Post by thebestofall007 on 2008-05-22
> **reeksy said:**
> Hi

I've upgraded via the package manager and had several issues! I can no longer access my CD drive and I'm getting system crashes every 2-3 days. The previous version of Ubuntu was excellent, i never had any issues! I wish i could roll back!

I notice you're talking about a fresh install. By this do you mean re-formatting you HD? Is this common practice with Ubuntu Linux when upgrading? It seems like a lot of effort; as you'd have to back-up all your files (on DVD or something). However, due to the issues I'm having I'm seriously considering it though.

Jon

what i mean about a fresh install is using a live cd to reinstall from boot up by changing the boot order and booting up from cd the traditional way (after backing up the data, of course). i didnt have to reformat the hd, since hardy heron already had my ubuntu partition in an ext2 format. the total install from cd took 20-25 minutes.

---

### Post by Efros on 2008-05-22
I have two machines that had 7.10 installed and one with Hardy Beta all of which were upgraded through the update manager. I have subsequently clean installed both of the formerly 7.10 machines, because of little niggling problems. The former beta machine doesn't seem to have any of these issues.

---

### Post by philinux on 2008-05-22
Having a separate home partition makes reinstalling really easy.

---

