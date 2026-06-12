---
title: "Sync files in two different folders? (windows --&gt; ubuntu)"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by airplanesimen on 2012-03-21
Hello! I have once again a clean install of ubuntu 11.10, and i dont  have any documents, music or pictures in my home folder yet, and i was  wondering if it was possible to sync my user folder from windows, and  into ubuntu? And that if it was possible to sync it every-day if it is  done changes in it? 

I dont want to save ex. a document two places each time i am saving it,  and my folders are way too big for Ubuntu one and dropbox, so, is there  any folder-syncing program to sync the folders at the computer?  Shortcuts is my last option, so i want to see if it is any possible way  to do this first.

Thanks! 
- Airplanesimen

---

### Post by SlugSlug on 2012-03-21
I'd use symbolic links,

ln -s /mnt/windows-drive/users/user/Documents ~/home/WinDocs

---

### Post by oklokl on 2012-03-21
[URL="http://freefilesync.sourceforge.net/"]
[/URL]
[http://freefilesync.sourceforge.net/](http://freefilesync.sourceforge.net/)
[URL="http://freefilesync.sourceforge.net/"]
[/URL]
[https://launchpad.net/~freefilesync/+archive/ffs]("https://launchpad.net/%7Efreefilesync/+archive/ffs")
sudo apt-get install freefilesync

deb [http://ppa.launchpad.net/freefilesync/ffs/ubuntu](http://ppa.launchpad.net/freefilesync/ffs/ubuntu) oneiric main 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 715BE097

[http://cafe.daum.net/candan/AURX/20](http://cafe.daum.net/candan/AURX/20)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214690&stc=1&d=1332327319[/IMG]

---

### Post by HiImTye on 2012-03-21
[https://one.ubuntu.com/downloads/windows/](https://one.ubuntu.com/downloads/windows/)

---

### Post by centaurusa on 2012-03-21
> **airplanesimen said:**
> I dont want to save ex. a document two places each time i am saving it

Why bother syncing the files between two directories?  Just use the Wjndows files in Ubuntu from a mounted drive (eg. \media\DataDisk).  Precisely the same files will be available when you boot into Windows (e.g. drive d).

---

### Post by Mark Phelps on 2012-03-21
> **centaurusa said:**
> Why bother syncing the files between two directories?  Just use the Wjndows files in Ubuntu from a mounted drive (eg. \media\DataDisk).  Precisely the same files will be available when you boot into Windows (e.g. drive d).

Very BAD idea -- if the Windows version is 7 and the folders are in the OS partition, which typically they are if they are under users ...

Writing to folders and files inside a mounted Win7 OS partition has been known to result in data corruption and resulting inability to boot Win7.

Much better approach is to have a shared data partition.  That doesn't have to BOOT, so there is no problem writing to it.

---

### Post by airplanesimen on 2012-03-21
> **oklokl said:**
> [URL="http://freefilesync.sourceforge.net/"]
[/URL]
[http://freefilesync.sourceforge.net/](http://freefilesync.sourceforge.net/)
[URL="http://freefilesync.sourceforge.net/"]
[/URL]
[https://launchpad.net/~freefilesync/+archive/ffs]("https://launchpad.net/%7Efreefilesync/+archive/ffs")
sudo apt-get install freefilesync

deb [http://ppa.launchpad.net/freefilesync/ffs/ubuntu](http://ppa.launchpad.net/freefilesync/ffs/ubuntu) oneiric main 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 715BE097

[http://cafe.daum.net/candan/AURX/20](http://cafe.daum.net/candan/AURX/20)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214690&stc=1&d=1332327319[/IMG]
Sorry, but what is on the picture in english? Or, i will try that first, thanks.

And i dont want to have a different partitition to save the files on. they should be easy to access from the home folder, and i want the folders here synced with windows folder. I am "auto-mounting" the partitition where the windows files are each time i log in, so that should not be a problem.

---

### Post by muteXe on 2012-03-21
You could always use something like dropbox?

---

### Post by airplanesimen on 2012-03-21
> **SlugSlug said:**
> I'd use symbolic links,

ln -s /mnt/windows-drive/users/user/Documents ~/home/WinDocs
Symbolic link, arent they the same as shortcuts?

---

### Post by oklokl on 2012-03-21
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214698&stc=1&d=1332333763[/IMG]
[]("http://ubuntuforums.org/attachment.php?attachmentid=214698&stc=1&d=1332333763")
[http://www.unixmen.com/freefilesync-free-folder-comparison-and-synchronization-tool-ppa-ubuntu/?utm_source=rss&utm_medium=rss&utm_campaign=freefilesync-free-folder-comparison-and-synchronization-tool-ppa-ubuntu](http://www.unixmen.com/freefilesync-free-folder-comparison-and-synchronization-tool-ppa-ubuntu/?utm_source=rss&utm_medium=rss&utm_campaign=freefilesync-free-folder-comparison-and-synchronization-tool-ppa-ubuntu)


[http://www.webupd8.org/2012/02/compare-and-synchronize-folders-with.html](http://www.webupd8.org/2012/02/compare-and-synchronize-folders-with.html)

---

### Post by airplanesimen on 2012-03-21
> **muteXe said:**
> You could always use something like dropbox?

Read my first post :D No, i cant, my folders are all together WAY to big for the 2 and 5 GB limit :/ I tried the file-sync-program, and it worked perfectly!

Thanks for the help guys, But is it possible to get this program to do its tasks automatically? Like, in the background? I know, in windows you can create a batch-file, and add it to tasks. But what about ubuntu?

Thanks!

---

### Post by airplanesimen on 2012-03-21
> **oklokl said:**
> [IMG]http://ubuntuforums.org/attachment.php?attachmentid=214698&stc=1&d=1332333763[/IMG]
[http://ubuntuforums.org/attachment.php?attachmentid=214698&stc=1&d=1332333763](http://ubuntuforums.org/attachment.php?attachmentid=214698&stc=1&d=1332333763)

[http://www.webupd8.org/2012/02/compare-and-synchronize-folders-with.html](http://www.webupd8.org/2012/02/compare-and-synchronize-folders-with.html)

[http://www.unixmen.com/freefilesync-free-folder-comparison-and-synchronization-tool-ppa-ubuntu/?utm_source=rss&utm_medium=rss&utm_campaign=freefilesync-free-folder-comparison-and-synchronization-tool-ppa-ubuntu](http://www.unixmen.com/freefilesync-free-folder-comparison-and-synchronization-tool-ppa-ubuntu/?utm_source=rss&utm_medium=rss&utm_campaign=freefilesync-free-folder-comparison-and-synchronization-tool-ppa-ubuntu)
Thanks!

---

### Post by SeijiSensei on 2012-03-21
> **airplanesimen said:**
> Thanks for the help guys, But is it possible to get this program to do its tasks automatically? Like, in the background? I know, in windows you can create a batch-file, and add it to tasks. But what about ubuntu?

Read this document:  [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by centaurusa on 2012-03-22
> **Mark Phelps said:**
> Very BAD idea -- if the Windows version is 7 and the folders are in the OS partition, which typically they are if they are under users ...

Writing to folders and files inside a mounted Win7 OS partition has been known to result in data corruption and resulting inability to boot Win7.

Much better approach is to have a shared data partition.  That doesn't have to BOOT, so there is no problem writing to it.

DataDisk (drive d: is a shared data partition (i.e. it's not the OS drive c:.)  However, my main reason for doing this is to make it easy to backup all of my data independently from the OS.

---

### Post by zombifier25 on 2012-03-22
I know this post is irrelevant and useless to you now, but...
> **airplanesimen said:**
> Symbolic link, arent they the same as shortcuts?
Not really. Symbolic links are handled by the file system itself. Shortcuts are defined by the softwares that uses it (like .lnk files for Windows Explorer, .desktop files for Linux, etc) A file browser when enters a symbolic links will see it like just another folder, regardless if the browser is aware that it is a symbolic link or not. In contrast, entering a shortcut will "teleport" the browser to the specified folder.

For example, you have a folder named foobar in /media/LOL, and you have a symbolic link to it named foobar2 in your home folder.
So we have the original folder /media/LOL/foobar and the symlink /home/foobar2.
When you enter the foobar2 folder, you will see it as just another folder, nothing strange or weird. The file browser will tell you that you are in /home/foobar2, though in fact you are in /media/LOL/foobar. You put a file named lol.txt into foobar2 and it will automatically show up in foobar. So you can treat foobar2 as a folder and drag-and-drop files into it, something you obviously can't do with shortcuts.

Of course, the symlink method is easier, but that means you must keep the original folder foobar intact. If you prefer to keep two copies of a file in two places at once, stick to your plan :p

---

### Post by airplanesimen on 2012-03-23
> **zombifier25 said:**
> I know this post is irrelevant and useless to you now, but...

Not really. Symbolic links are handled by the file system itself. Shortcuts are defined by the softwares that uses it (like .lnk files for Windows Explorer, .desktop files for Linux, etc) A file browser when enters a symbolic links will see it like just another folder, regardless if the browser is aware that it is a symbolic link or not. In contrast, entering a shortcut will "teleport" the browser to the specified folder.

For example, you have a folder named foobar in /media/LOL, and you have a symbolic link to it named foobar2 in your home folder.
So we have the original folder /media/LOL/foobar and the symlink /home/foobar2.
When you enter the foobar2 folder, you will see it as just another folder, nothing strange or weird. The file browser will tell you that you are in /home/foobar2, though in fact you are in /media/LOL/foobar. You put a file named lol.txt into foobar2 and it will automatically show up in foobar. So you can treat foobar2 as a folder and drag-and-drop files into it, something you obviously can't do with shortcuts.

Of course, the symlink method is easier, but that means you must keep the original folder foobar intact. If you prefer to keep two copies of a file in two places at once, stick to your plan :p
Okay, thanks for the very detailed explanation, so, can you maybe show me how to do this? Sounds much easier to have symbolic links instead of a lot of programs xD Thanks! and i think it was perfect timing to post it here! i have some problems using the software, so lets use symbolic links :D is the "-s" for symbolic links?

---

### Post by zombifier25 on 2012-03-23
> **airplanesimen said:**
> Okay, thanks for the very detailed explanation, so, can you maybe show me how to do this? Sounds much easier to have symbolic links instead of a lot of programs xD Thanks! and i think it was perfect timing to post it here! i have some problems using the software, so lets use symbolic links :D is the "-s" for symbolic links?
```
ln -s /source/folder /link/location/linkname
```In your case, replace /source/folder with the user folder on Windows, and /link/location/linkname with the name of the link in your home folder.
And yes, the -s flag is for symbolic links. Without the flag, it will create a hard link, which
1. Can only link to files, not folder.
2. Can only link to files of the same partition.

If you want to know what hard links are, feel free to ask.

---

### Post by airplanesimen on 2012-04-08
> **zombifier25 said:**
> ```
ln -s /source/folder /link/location/linkname
```In your case, replace /source/folder with the user folder on Windows, and /link/location/linkname with the name of the link in your home folder.
And yes, the -s flag is for symbolic links. Without the flag, it will create a hard link, which
1. Can only link to files, not folder.
2. Can only link to files of the same partition.

If you want to know what hard links are, feel free to ask.

I guess i know what hard links are then, maybe the same as if you right-click on the file, and selects "create link" or "create shortcut"? But i am getting used to the Symbolic links now, noone told me before, so thanks a lot!

---

