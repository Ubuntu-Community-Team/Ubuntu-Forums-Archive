---
title: "upgrading from ubuntu 10.04 to 13.10"
date: 2013-12-18
forum: New to Ubuntu
---

### Post by davidcole3 on 2013-12-18
My ubuntu shares my drive with Windows 7.  I have saved everything that is in my username folders. I have already created a bootable 13.10 64 bit DVD.   I would like my URL bookmarks / passwords etc to be saved.  How should I proceed?  Exactly what steps are necessary?

---

### Post by ajgreeny on 2013-12-18
> **davidcole3 said:**
> My ubuntu shares my drive with Windows 7.  I have saved everything that is in my username folders. I have already created a bootable 13.10 64 bit DVD.   I would like my URL bookmarks / passwords etc to be saved.  How should I proceed?  Exactly what steps are necessary?
Your only practical option is to make sure that all your personal files, including all the hidden files and folders in your old home folder, are backed up and safe and then do a clean install; you can not do an upgrade from 10.04 to 13.10 direct ; you would have to go 10.04 ->12.04 ->12.10 ->13.04 ->13.10, ie 4 separate upgrades, and the chances of problems are too high in my opinion to make it worth attempting.

All you URL/bookmarks etc etc will be in your /home folder in hidden folders, eg **/home/username/.mozilla** or **/home/.config/chromium**, depending on the browser you use, so make sure all hidden folders are backed up, and when you've installed 13.10 copy everything back to the home folder and you should be good to go.

---

### Post by davidcole3 on 2013-12-18
What command line command or options do I use to view hidden files?

---

### Post by Iowan on 2013-12-18
**ls -al** should show you what you want...
 (the "l" might not be necessary - it's just a habit.)

---

### Post by davidcole3 on 2013-12-18
Thanks a lot.  What command should I use to copy all files (including hidden files in subdirectories)?

---

### Post by plurga on 2013-12-18
to copy files ,folders,sub folders u use the cp command. this command has several options. I add 1 link 
[http://www.computerhope.com/unix/ucp.htm](http://www.computerhope.com/unix/ucp.htm) or u can issue man cp comman from ur terminal :)

---

### Post by davidcole3 on 2013-12-18
Conclusion
I really should have zipped up the whole /home directory.  But not knowing how to zip the whole directory, and because I was backing up to a Windows flash drive, rather than a LINUX directory, I used the following commands:
   cd /home
   cp -r * /media/PKBACK#\ 001/home_bu
The exact command would vary depending upon the type of flash drive, I suppose.  I encountered many error messages, but I believe that most of the important data was backed up.
Thanks to all those who answered my "learner's" questions.
I consider this thread closed.

---

### Post by Impavidus on 2013-12-19
The best way (also to others reading this thread) is to use```
tar -czf /media/your_usb_drive/homebackup.tgz --exclude=anything_you_want_to_exclude /home/username
```You can use the GUI too, but it would depend a bit on the file manager you use. I always exclude things like a google earth cache, which tends to be really big and not very important. Using tar allows you to keep the permissions after restoring the files, even when your backup drive has ntfs of fat system.

---

### Post by ajgreeny on 2013-12-19
You can also use rsync, or for a GUI application, grsync to back up your /home.  There are many others as well, but rsync is what I've been using for years.

It is a good habit to get into anyway, backing up /home files and folders is one of the essentials of modern computer use

---

