---
title: "[SOLVED] Garbage that won't delete"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by philk949 on 2008-06-18
Hi.
As you can tell, I'm a greenhorn, and I'm having trouble trying to delete 3 folders in my garbage bin. They're big suckers and I would really like them gone, but when I try to empty the bin, I am denied permission to do so. Have tried tweaking the permissions on the folders, but to no avail.
I should add that the folders are Office 2007 files with a (D) suffix, as they were left over from a nephew's experimentation with installing Microsoft Office on my dear Ubuntu 8.04. (I have now locked him out). Can someone please advise me?
Thank you,
philk949

---

### Post by k33bz on 2008-06-18
All you need to do is change the folders permission in it, 

Go to the terminal:
Applications-> Accesories->Terminal
and type in this code:
```
sudo chown -R yourusername.yourusername /path/to/trash/files
```
then you can go into the trash bin and delete them

---

### Post by iaculallad on 2008-06-18
Open your terminal and issue the commands below:

If you're using Hardy:

```
sudo rm -rf /home/Your_User_Name/.local/share/Trash/*
```

Or

```
sudo rm -rf /home/share/Trash/files/*
```


In Gutsy:

```
sudo rm -rf ~/.Trash/* 
```

---

### Post by iansane on 2008-06-18
well... come to think of it. I don't know where the trash directory is.

If you know where it is, and you have the root password, you should be able to cd to the directory in terminal and type "sudo rm -r folder" where folder is the name of the one you want to delete

---

### Post by iansane on 2008-06-18
LOL OK now I know where it is. /.trash 

glad these guys brains are working cause mine quit on me

---

### Post by perce on 2008-06-18
Oops, according to the post above, my instructions don't work on Hardy (no time to upgrade yet...). 

If you want remove ALL files in the trashcan, you can open a terminal and give the command:

sudo rm -rf .Trash/*

(be careful with this command: a mistype can result in a disaster, so double check before pressing enter)

If there are files you want to save in the trashcan, tipe:

sudo rm -rf .Trash/filesyouwanttoremove

where of course you must substitute "filesyouwanttoremove" with the name of the files you want to remove.

---

### Post by philk949 on 2008-06-18
Thank you, iaculallad.

A functional code is a joy to behold.

philk

---

### Post by philk949 on 2008-06-18
You must excuse me popping up again and again, but I'm still feeling my way around this forum. I'd like to thank all who posted replies to my problem.

philk

---

### Post by iaculallad on 2008-06-18
You're welcome. That's one way of learning or getting through Ubuntu or Linux in general, getting around the forum. And, be sure to read and analyze other posts aside from the one you authored.

---

