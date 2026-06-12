---
title: "Help"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by harimphari on 2011-09-30
Dear Beloved and Highly Educated Friends,
   I am novice in LINUX.(Only 6 days exp)
Whenever I try to update or try yo install certain appl ,it shows
"/etc/apt/build  error".How can I solve this(I am with Zorin 5.1)
MP HARI

---

### Post by Rex Bouwense on 2011-09-30
Welcome to the Ubuntu forums.  It would help if you provided a little more information like some computer specs and what you have done trying to update.  I assume that you are running Zorin and Ubuntu.  Is that correct?

---

### Post by harimphari on 2011-09-30
Whenever I try to install or update this message comes
Ignoring file 'apt-build' in directory '/etc/apt/sources.list.d/' as it has no filename extension
Pl give me a solution, as I being a novice ,only 8daye exp with linux,I hope U will explain and discuss it in detail

MP HARI,FRIEND FOR FREEDOM

---

### Post by seawolf167 on 2011-09-30
What is the output of the following commands typed into a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```Please respond and put the response inside [noparse]```
 
```[/noparse] tags

EDIT: Is this the same issue that you posted in a different thread?
[http://ubuntuforums.org/showthread.php?t=1852666](http://ubuntuforums.org/showthread.php?t=1852666)

---

### Post by matt_symes on 2011-09-30
Hi

Open a terminal and copy and paste these commands into it.

```
ls -l /etc/apt/sources.list.d/
```

```
cat /etc/apt/sources.list.d/apt-build
```

Copy and paste the results back into this thread. 

You can copy and paste into a terminal by copying the commands above, right clicking in the terminal and selecting paste.

You can copy the results back by highlighting the text in the terminal, right clicking and selecting copy and paste back into the next post.

Kind regards

---

### Post by sisco311 on 2011-09-30
Please don't create multiple threads on the same subject.

Threads merged.

---

