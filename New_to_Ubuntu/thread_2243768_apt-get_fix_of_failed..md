---
title: "apt-get fix of failed."
date: 2014-09-11
forum: New to Ubuntu
---

### Post by arnold7 on 2014-09-11
Hello everyone! I got a kin d of a problem. I got an error message, were was writtrn that I had to use sudo apt-get install -f command to sole it(I got such kind of error on my other machies) BUT now whaen I'm tryeing tu use that command it writes to me

Reading package lists... Done.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en

and than it writes that something can  not be read... What  problem is it? What is it caused by? How can it be solved? (Sorry, maybe I'm making some mistakes, that's because I'm not english native-speaker...)

---

### Post by deadflowr on 2014-09-11
It's a, somewhat normal error people sometimes get.
Here's one answer to a solution for it
[http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err)

---

### Post by arnold7 on 2014-09-16
I did 
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update 
, but i stil have 
####################################################################################################
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
#####################################################################################################
What's wrong?

---

### Post by fantab on 2014-09-16
Change the 'Server' and try again.

If problems persist then post the output of:
```
cat [COLOR=#000000]/etc/apt/sources.list
```[/COLOR]

---

### Post by Bucky Ball on 2014-09-16
Also from that link:

> One individual found he had to do these two steps multiple times, but that it worked eventually.

Unsure if it will work for you, though.

And yes, as fantab alludes to, the repo you are trying to access could be dead or down, because:

```
The package lists or status file could not be parsed or opened.
```

Open Software Updater>Settings in bottom left corner>Other Software tab and untick it. Try updating again.

---

