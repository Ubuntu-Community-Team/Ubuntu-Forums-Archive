---
title: "Can Folder and File go missing in Ubuntu?"
date: 2017-12-11
forum: New to Ubuntu
---

### Post by wrongusername2 on 2017-12-11
I am running Ubuntu 16.04
Using LibreOffice I had created a document and saved it to '/tmp/R/Instalhurdle.doc'. Then rebooted the machine using
        sudo reboot


Now I login back to OS and the document is missing, there is no folder (/tmp/R). Not only the file, even the folder is missing. 


I have so many questions now. This never happened to me on NTFS.
-Is this file missing because of some file-system caching and that did not persists data? Can I disable that permanently?
-Did i create the folder at wrong place? Even if I did it should not simply delete the file.

This is a major concern for me as I plan to migrate from Win7 to Ubuntu, please educate me what is going on. If there are doc please give me the link.

Thanks

---

### Post by QIII on 2017-12-11
Hello!

/var/tmp persists across boots.  /tmp does not.  /tmp really is temporary.  The Linux file hierarchy is not the same as Windows, so it is best to leave those expectations behind when using Linux.  That should save you some frustration.  :) 

I'd not save a file to /var/tmp in general in any case.  That's a system directory to store system temp files.  Why not save the file to your /home directory?

---

### Post by Douglas_White on 2017-12-11
If you are new to Ubuntu / Linux and, doing work that is important, I'd save EVERYTHING to a removable flash drive until
I got comfortable with Linux.

All the Best,
D. White

---

### Post by wrongusername2 on 2017-12-11
> **Douglas_White said:**
> If you are new to Ubuntu / Linux and, doing work that is important, I'd save EVERYTHING to a removable flash drive until
I got comfortable with Linux.

All the Best,
D. White

I will important data in to ext-hd :D. Thanks

---

### Post by ajgreeny on 2017-12-11
Your home folder, ie /home/username, is specifically created when you install a Linux distro as the area of the filesystem in which you should save all your own files.

So the most important question to you, as already asked by QIII, is why have you not saved the files you created to that home folder?

---

### Post by wrongusername2 on 2017-12-11
> **QIII said:**
> /var/tmp persists across boots.  /tmp does not.  /tmp really is temporary. 

Thanks. I will stay away from /tmp/ :grin:
I have to read up about folder designation in Ubuntu.

---

### Post by wrongusername2 on 2017-12-11
> **ajgreeny said:**
> is why have you not saved the files you created to that home folder?
Thanks,.  Coming from Windows OS, I always created folders under root or temp  say C:\Source or C:\Work or C:\Backup or C:\temp\R and  stored the files  there.  In case of Windows I never stored anything under OS designated  folders like 'home, pictures, documents'. I have to get adjusted to  Linux ecosystem.

---

### Post by again? on 2017-12-11
> **wrongusername2 said:**
> Thanks. I will stay away from /tmp/ :grin:
I have to read up about folder designation in Ubuntu.
For a start, in terminal run...
```
man hier
```

---

### Post by wrongusername2 on 2017-12-11
> **guber2 said:**
> For a start, in terminal run...
```
man hier
```
Thanks, needed something like this.

---

### Post by oldos2er on 2017-12-11
Also see [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by 1clue on 2017-12-11
On all my systems, I configure all tmp directories (/tmp, /var/tmp, and directories my apps use as temp space) as tmpfs, which means they never actually go to the disk. They go to RAM. When the system reboots there's nothing left.

Temp directories should be files you no longer want after your session exits. Or for that matter, after you closed the file for a period of time even if you left a session running.

---

### Post by wrongusername2 on 2017-12-12
> **1clue said:**
>  tmpfs,

Thanks. *Temporary File System *that is good to know.

---

### Post by 1clue on 2017-12-13
The best advice to give a new user is, never store anything outside of your home directory tree unless you're doing something about a service or system maintenance. If it doesn't require sudo, then it goes to /home/<user>/<something>

Probably most Linux users start out throwing files everywhere, and eventually they lose a lot of data because of it. Putting all your files in the /home/<user> directories makes your relevant stuff easy to back up and keeps permissions suitable for decent security.

---

### Post by col48 on 2017-12-13
Even in Windows days, I tried hard to avoid using directories "helpfully" provided by default, so I had a directory on the C drive called something beginning with a (so it appeared at the top of the list) and stored everything I created there. Including downloads etc.

In Ubuntu, I still have a similar setup since there are still hidden folders and files in my home directory which I have not created directly and whose deletion might therefore cause problems - for instance config files, mail folders, cookies, many more obscure things also.  Each home folder contains everything pertinent to its owner; other folders at the same or higher hierarchical levels contain items which could relate to every user.

Having a folder structure which makes sense to you helps you keep control of your computing activity.  I hardly ever need to search for a file I have made because I store it where I would expect to look for it later, with a descriptive name.  Yes, I have temporary files, but these are files which I may want for a week or so and then delete - I store them in a Temp folder within my own file structure, not one created by Ubuntu.

---

