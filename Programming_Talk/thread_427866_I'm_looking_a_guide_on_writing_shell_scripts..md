---
title: "I'm looking a guide on writing shell scripts."
date: 2007-04-29
forum: Programming Talk
---

### Post by zetsumei on 2007-04-29
I'm looking for a guide on writing a backup shell script.  Does anyone know of a guide or a site I can go to for help on writing a backup script?  Thanks for the replys.

---

### Post by earobinson on 2007-04-29
Shell scripts are just terminal command so any tutorial should do since I assume all your going to be doing is copying from one location to another.

any on google should be good

Unless I dont understand your Q

---

### Post by zetsumei on 2007-04-29
Well, what should I have in a backup script?  Just tar like say my home dir and backup?  And is there a way to have it run like once a month or something?

---

### Post by bashologist on 2007-04-29
#Use crontab to do it monthly maybe? The crontab wiki is very well done.
[http://en.wikipedia.org/wiki/Crontab](http://en.wikipedia.org/wiki/Crontab)

#Then maybe make a script for your crontab to execute like this:
```
#!/bin/bash
rsync -avF /data/ /backup/
```
Make sure to test whatever command you're gonna use if you plan on using crontab because you wouldn't want sometime to fail a month from now. n_n

Or if you want you could just execute this script on startup:
```
#!/bin/bash
if [ "$(date +%d)" == "01" ]; then
	rsync -avF /data/ /backup/
fi
```
Just replace the rsync command with one that works for you.

---

### Post by zetsumei on 2007-04-29
So what does the rsync -avF /data/ /backup/ do?  I'm trying to learn.

---

### Post by earobinson on 2007-04-29
```
man rsync
``` should give you all the info you need

---

### Post by bashologist on 2007-04-29
> **zetsumei said:**
> So what does the rsync -avF /data/ /backup/ do?  I'm trying to learn.

What I always do is test it on a random folder like this:
```
dirname=$RANDOM$RANDOM; mkdir $dirname; cd $dirname; for ((n=0;n<5;n++)); do mkdir -p $RANDOM/$RANDOM; done; find . -type d | while read dir; do for ext in .jpg .png .exe .sh .py .pl .rb .cpp .txt; do echo "0101011101" > $dir/$RANDOM$ext; done; done; cd ..; echo "Created \"$dirname\""
```
After executing the above commands you'll have a folder with a random name that looks like this:
```
10945.exe  1279.txt  13282  13454  22350.cpp  2652.png  27370.sh  29309  30941.jpg  31270.py  4570  6027.rb  7580.pl  8190
```Which is just a folder with a bunch of random filenames each with some text in them!

Then you can play around by trying to move those files with rsync or whatever. Just be careful.

---

### Post by BRAXS69 on 2007-04-29
this site has helped me allot, i hopes it serves you well also.. [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

as for the backup script looking on what has already been poseted i couldn't add anything new to it.

---

### Post by trak87 on 2007-04-29
The reason rsync is good is because once you've backed up your files, it won't keep backing up the same files unless they have changed. This is enormously time saving.

The reason tar is good is because it does compression in combination with compression (the z option in gzip).

If you have the space, go with rsync.

---

