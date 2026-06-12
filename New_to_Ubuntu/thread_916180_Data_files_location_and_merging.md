---
title: "Data files location and merging"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by OtterbeinOwl on 2008-09-10
Just starting to learn Ubuntu on what was my husband's computer.  Mine was WXP, but he had shown me a lot on this one, now mine.  I want to merge some data from /backups with some data in the /home/bo directories.  I have found some data in the backups, for instance .alexandria, but cannot fine how to merge it with the /home/bo/.alexandria file.  

Also, I can't identify all the data files.  Where and how are data files named in /home/bo or any directory?  Hope my question is clear and thanks for your help.

---

### Post by bobnutfield on 2008-09-10
Not sure what you mean by "data" files.  If you are simply trying to transfer data or files from a backup medium, you simply copy them to the directory you want them in.  Or, the the data you want to merge is somewhere else already on your computer, you can use a version of the following:

> cp /backups/data /home/bo/data

This is a very simply use of the cp command, and assumes you have a directory in your home folder called "data".

I apologize if I misunderstand your question, but it sounds like you just want to copy files from one place to another.

---

### Post by OtterbeinOwl on 2008-09-10
> **bobnutfield said:**
> Not sure what you mean by "data" files.  If you are simply trying to transfer data or files from a backup medium, you simply copy them to the directory you want them in.  Or, the the data you want to merge is somewhere else already on your computer, you can use a version of the following:

This is a very simply use of the cp command, and assumes you have a directory in your home folder called "data".

I apologize if I misunderstand your question, but it sounds like you just want to copy files from one place to another.

Bob, thanks for the reply and sorry for the lack of answer.  I am in the possible Ike hit zone and ran out to get some more supplies.  Major lines, traffic and other shoppers.  Got back and had problems logging in.  

Ok, copy from one place to another, but first where do I find the files? Where are and/or what are files saved in documents, for instance.  And if I copy them to another file, will they add to what is there or overwrite?  Maybe I am still thinking like WXP.  Guidance or pointing to a tutorial would be appreciated.

---

### Post by bobnutfield on 2008-09-11
> Ok, copy from one place to another, but first where do I find the files? Where are and/or what are files saved in documents, for instance. And if I copy them to another file, will they add to what is there or overwrite? Maybe I am still thinking like WXP. Guidance or pointing to a tutorial would be appreciated.

First of all, what specific files are you looking for?  If you are talking about the documents folder in your home directory that was automatically created when you installed, then that folder is for anything you want to put there.  It can be equated to "My Documents" in Windows, but you are not restricted to documents only.  You can put anything you want there.

Copying files from one location to another (i.e. one directory to another, simply adds that transferred data to the target directory and adds it to what is already there.  It does not overwrite anything. However, if you copy a file with the exact same name to a directory that has a file with that name, it WILL overwrite it unless you use the -i switch (interactive mode).  In that case, you will be asked if you want to overwrite the existing file.  Type:

> man cp

to read all the options that are available for the cp command.  Post back with what specific files you are looking for and maybe we can direct you to them.

---

