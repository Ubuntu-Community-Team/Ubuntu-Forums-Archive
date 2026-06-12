---
title: "Newbie Question: What is the full path to the share I just mounted?"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by blairnic on 2012-04-01
I am running Ubuntu 11.04 and mounted a Windows network share drive via the Places > Connect To Server...  menu option.  The share mounted fine, creates a folder on my desktop and I can read and write to the share fine.  Example share name: 192.16.1.2/mp3_files

Q: I would like to do some shell work on the share folders and don't know the path. I poked all over my file system using Nautilus and can't find the path from root to the share.  There are shortcuts displayed in Nautilus but that is still GUI access does not address my need; I am looking for the full path. 

Thanks in advance for your help.

---

### Post by mastablasta on 2012-04-01
try

smbtree

command

---

### Post by Cheesemill on 2012-04-01
Have a look in the hidden folder .gvfs in your home folder:
```
cd ~/.gvfs
```

---

### Post by blairnic on 2012-04-01
The smbtree command returned something that looks like this:

\\SERVER\mp3_files   MP3 files

which is essentially an enumeration of mounted shares without showing the path. 


Poking into the .gvfs does show the subfolders.  From the command line, doing an 'ls' command shows something like this:

[stuff deleted] ... mp3_files on 192.168.1.2


I was a little confused over how I would 'cd' to that but by using quotes, e.g.

cd "mp3_files on 192.168.1.2"

I was able to get into the folders and subfolders. 
:popcorn:
PROBLEM SOLVED !! THANK YOU.

---

