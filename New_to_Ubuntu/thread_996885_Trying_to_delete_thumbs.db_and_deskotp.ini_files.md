---
title: "Trying to delete thumbs.db and deskotp.ini files"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Pablo W on 2008-11-29
Hi, 
I'm a full newbie. I have just put to sleep my Windows XP and I'm giving my first steps with linux through Ubuntu 8.1. I have copied all the music I had under Windows XP in a series of DVDs and I have noticed that when I paste the music folders in Ubuntu, thumbs.db and desktop.ini files are there too. I assume those are not needed in Ubuntu so I have tried to delete them but I could not. Questions:

1: Should I keep those files?

2: If not, how can I delete them?

Thanks for your help,
Pablo W.

---

### Post by bhadotia on 2008-11-29
> **Pablo W said:**
> Hi, 
I'm a full newbie. I have just put to sleep my Windows XP and I'm giving my first steps with linux through Ubuntu 8.1. I have copied all the music I had under Windows XP in a series of DVDs and I have noticed that when I paste the music folders in Ubuntu, thumbs.db and desktop.ini files are there too. I assume those are not needed in Ubuntu so I have tried to delete them but I could not. Questions:

1: Should I keep those files?

2: If not, how can I delete them?

Thanks for your help,
Pablo W.

1. You don't need them in ubuntu (linux).
2. Press shift+delete as in windows.

---

### Post by night_fox on 2008-11-29
Windows doesn't strictly need them either but it might make viewing thumbnails faster in windows. It recreates them whenever you visit that directory in windows. Do what you want.

Personally I delete them.

---

### Post by Pablo W on 2008-11-29
> **bhadotia said:**
> 1. You don't need them in ubuntu (linux).
2. Press shift+delete as in windows.

Thanks for your quick answer, bhadotia. I'm afraid that doesn't work. I have tried that and nothing happens. The files stay there, alive and kicking.

---

### Post by Pablo W on 2008-11-29
> **bhadotia said:**
> 1. You don't need them in ubuntu (linux).
2. Press shift+delete as in windows.

Hi again,
I have noticed that both the files and the containing folder had a little orange icon with a lock. I did right button, properties, permits (sorry if that is not the exact word, but I'm running Ubuntu in Spanish) and noticed that in "access to folders" it was set to "access files". I have switched that to "create and delete files" and... problem solved!

Now, I have noticed that all my music folder have that orange lock. So, my question now is:

Is there any way I can change the default setting so that when I paste a new folder (I still have lots of music folders in DVDs to be migrated to Ubuntu) I have granted "create and delete" access to those folders and their sub folders and files? Otherwise, I 'll have to change it one by one and they are an awful lot!

Thanks again for your help.

---

### Post by clive littlewood on 2008-11-29
Hi

Welcome to the forums.

If you do the same exercise with permissions in the parent folder that you did with an idividual file, at the bottom of the window you will see "apply to all files in folder" Click this and all files will be given your chosen permissions.     :)  :)

Hope this helps

Clive

---

### Post by Pablo W on 2008-11-29
> **clive littlewood said:**
> Hi

Welcome to the forums.

If you do the same exercise with permissions in the parent folder that you did with an idividual file, at the bottom of the window you will see "apply to all files in folder" Click this and all files will be given your chosen permissions.     :)  :)

Hope this helps

Clive

Thanks, clive littlewood. I have done the same in the parent folder as you suggested and the changes were applied to all the files and folders I already had in my Music directory. Nevertheless, when I paste new files and folders in that same parent directory, they get the orange lock icon. In other words, the problem is not with the existent files now, but with the ones I'm pasting there from DVDs.

Question: Is there any way to set the existing full access permission in the Music folder to be applied to new files or should I assume they will always be locked by default and I will have to enter the folder properties every time I paste new files?

Thanks for your patience.

---

### Post by clive littlewood on 2008-11-29
Hi Pablo

You will always get the padlocks when transfering from another OS.

This is for your benefit and security and one of the reasons why Linux is safer than windows.       :lolflag:

I always transfer any data as folders then it,s less work to apply permissions only to the parent folder.

Clive

---

### Post by m_l17 on 2008-11-29
Take a look at this, so you understand permissions in Ubuntu/Linux:

[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by Bölvaður on 2008-11-29
When you move files from one place to the other it matters what type of file system you are moving it from. So files from NTFS (windows) may not give you correct permissions, same goes for DVD. DVDs actually give you read only (just like on the disk).

So the easiest way is to copy it to your computer and then open up the terminal at that location.

Lets assume you copy a DVD and paste it to your desktop

```
cd Desktop
sudo chown -R user dvdfolder/
sudo chmod -R 722 dvdfolder/
```

look up on google the command chmod command for more info about how to set permissions.
chown sets owner of the file/folder
-R means it is done recursivly... that is it happens to every file or folder inside the next one and so on.


also for finding all the .db files
```
cd /absolute_path_to_the/directory_to_be_looked_in
find | grep .db$
```

please correct me if Im wrong, I might remember this wrongly.

---

### Post by bhadotia on 2008-11-29
> **Bölvaður said:**
> When you move files from one place to the other it matters what type of file system you are moving it from. So files from NTFS (windows) may not give you correct permissions, same goes for DVD. DVDs actually give you read only (just like on the disk).

So the easiest way is to copy it to your computer and then open up the terminal at that location.

Lets assume you copy a DVD and paste it to your desktop

```
cd Desktop
sudo chown -R user dvdfolder/
sudo chmod -R 722 dvdfolder/
```

look up on google the command chmod command for more info about how to set permissions.
chown sets owner of the file/folder
-R means it is done recursivly... that is it happens to every file or folder inside the next one and so on.


also for finding all the .db files
```
cd /absolute_path_to_the/directory_to_be_looked_in
find | grep .db$
```

please correct me if Im wrong, I might remember this wrongly.

I think
```
find *.db | rm
```will delete the files though I cannot check as I'm on windows. 
Here is a simple explanation of the permissions etc.:
[http://linuxcommand.org/lts0070.php]("http://linuxcommand.org/lts0070.php")

---

### Post by Pablo W on 2008-11-29
Wow! Thanks bhadotia, Bölvaðurv, m_l17, and clive littlewood for this tsunami of linux lessons!

To summarise, from clive I got that I better transfer everything as a folder and then apply changes to it, since all my files coming from Windows will get the padlocks. So that answers my specific question. 

From bhadotia and m_l17 I got very useful background information that I will take the time to read to learn a little bit more.

And from Bölvaðurv I got... well, I'm not sure I've understood anything ;) To start with, I don't know what "open up the terminal at that location" means, but I'm sure I will understand Bölvaðurv once I have read the background information and his/her instructions will prove very useful too.

All in all, thank you all for a thorough thread of practical advice and background information.

Have a nice weekend.

---

