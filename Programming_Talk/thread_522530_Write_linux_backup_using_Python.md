---
title: "Write linux backup using Python"
date: 2007-08-10
forum: Programming Talk
---

### Post by tc101 on 2007-08-10
I want to write a backup program using linux.  This is mostly a learning exercise.  The best way for me to learn a language is to start doing things with it.  I wrote a simple web crawler in python and learned a lot.  This is the next step.

I have a linux shell script now that does some backup:

```
sudo mkdir /home/backup/wkbackup

sudo tar -cf /home/backup/wkbackup/D_backup$(date +"%Y%m%d").tar /home/tomcarr/D

```

I would like to just translate this into python to start.  I am having trouble with just the first line, trying to make a work directory.  Can someone point me to where in the online references it shows how to use mkdir, or better yet, some example code showing how to do things similar to this.

---

### Post by keifer on 2007-08-10
Have you had a look at the [Python Library Reference](http://docs.python.org/lib/lib.html)? Sections 11 and 12 should be helpful for working with directories and file compression.

[A Byte of Python](http://swaroopch.info/text/Byte_of_Python:Problem_Solving) uses creating a backup utility as one of it's examples, so it might be worth a look. :)

---

### Post by tc101 on 2007-08-10
Thanks, that's just what I needed.  I looked at the reference but somehow those sections, skimming over it too fast I guess.

---

### Post by tc101 on 2007-08-10
If anyone else is working on this, take a look at this example code

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/299412](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/299412)

these examples also taught me some useful things, depending on what you are trying to do:

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/440626](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/440626)
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/435904](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/435904)
[http://aspn.activestate.com/ASPN/Cookbook/Python?kwd=Files](http://aspn.activestate.com/ASPN/Cookbook/Python?kwd=Files)
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52277](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52277)
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/191017](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/191017)

---

### Post by scooper on 2007-08-12
[This Python script]("http://wijjo.com/file_download/11") (gzipped) does exactly what you're trying to do.  I use it every day to make timestamped compressed or uncompressed backups.  If it's cheating don't look at it, otherwise if you can use it see if it's useful.:)

---

