---
title: "How To Undelete a Folder?"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by brantpadams on 2014-01-12
I've looked up a few methods, but I can't seem to find any that have helped so far.

I must have accidentally deleted a large folder from my desktop while deleting some other files. I've checked through my hard disk and can't seem to find the folder anyway. It was large with a lot of text documents, ROMS, and cbr files. I refer to it a lot and I'm sweating a little over trying to find it. 

I'm hoping its still hanging around somewhere in freespace, but I don't know if the folder itself still exists. It happened just earlier today, so if I saw the details of I could probably pin point it, but I simply don't know what software or terminal commands can get me to find and recover it. 

I would appreciate any help available. Very big folder!

---

### Post by whitesmith on 2014-01-12
Open a terminal and type```
du -a ~ | sort -nr | head -n 5
```This will give you the 5 largest directories on your system. Feel free to change that to 10 or whatever. If you can't find it, you're up the proverbial creek because it is notoriously difficult in *nix to recover files that have been removed. Good luck!

---

### Post by llamabr on 2014-01-12
Sometimes you can find what you've deleted by looking in ~/.local/share/Trash

it may help if you told us a bit more about how it might have been deleted.

---

### Post by kajoky on 2014-01-12
I successfully un-deleted a number of files using extundelete
I think the file system has to be ext4 or ext3
The more you use the drive the less likely you will be to recover all files.

---

### Post by brantpadams on 2014-01-12
> **llamabr said:**
> Sometimes you can find what you've deleted by looking in ~/.local/share/Trash

it may help if you told us a bit more about how it might have been deleted.
Basically I was just deleting a few things off my desktop and I must have accidentally selected the folder without realizing it and removed it from trash. 

I tried your line in terminal but nothing popped up.

---

### Post by brantpadams on 2014-01-12
> **whitesmith said:**
> Open a terminal and type```
du -a ~ | sort -nr | head -n 5
```This will give you the 5 largest directories on your system. Feel free to change that to 10 or whatever. If you can't find it, you're up the proverbial creek because it is notoriously difficult in *nix to recover files that have been removed. Good luck!
Didn't see the folder in the list. I upped it to 20 and no dice.

---

### Post by llamabr on 2014-01-12
> **brantpadams said:**
> Basically I was just deleting a few things off my desktop and I must have accidentally selected the folder without realizing it and removed it from trash. 

I tried your line in terminal but nothing popped up.

"Basically" I was asking if you deleted these items using the command line, or drag and drop, or what.

When you say you tried my line and nothing popped up, what does that mean?  Paste the output of:

```
ls ~/.local/share/Trash/files/
```

---

### Post by Bashing-om on 2014-01-12
brantpadams; Hi !

Depending on how you deleted the files from the desk top, have you looked in root's trash ?
```

sudo ls -la /root/.local/share/Trash

```
[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by brantpadams on 2014-01-12
> **llamabr said:**
> "Basically" I was asking if you deleted these items using the command line, or drag and drop, or what.

When you say you tried my line and nothing popped up, what does that mean?  Paste the output of:

```
ls ~/.local/share/Trash/files/
```
Literally nothing comes up after inputing that command. Just a new command line. Does it refer to what would currently be in the trash bin? 

And when I deleted it it was highlighted and I hit delete. And I did in fact remove it from trash after that.

---

### Post by brantpadams on 2014-01-12
> **Bashing-om said:**
> brantpadams; Hi !

Depending on how you deleted the files from the desk top, have you looked in root's trash ?
```

sudo ls -la /root/.local/share/Trash

```[INDENT][INDENT]hope this helps
[/INDENT]
[/INDENT]

I get a no such file or directory prompt after that command

---

### Post by Kevin McCready on 2014-01-13
sudo ls -la ~/.local/share/Trash

---

### Post by llamabr on 2014-01-13
So you accidentally deleted the directory, and then followed up by highlighting the directory, and then removing the directory from your trash folder?  Yes, it's gone forever.

In future, note: you can leave stuff in your trash folder forever.  That way, if you change your mind, it's not gone forever.  Unless you're strapped for disk space, there's no urgent reason to delete the contents on your trash folder. Ubuntu puts in there for just this reason.

---

### Post by brantpadams on 2014-01-13
> **Kevin McCready said:**
> sudo ls -la ~/.local/share/Trash
```
total 28drwx------  5 brant brant  4096 Aug 11  2011 .
drwxr-xr-x 30 brant brant  4096 Jan 13 01:20 ..
drwx------  2 brant brant  4096 Jan 12 19:25 expunged
drwx------  2 brant brant  4096 Jan 12 19:25 files
drwx------  2 brant brant 12288 Jan 12 19:25 info
```

---

