---
title: "using ppa purge"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-11-06
what command would i use to purge the following

xubuntu-dev-xfce4_12-quantal.list

tks just unsure

---

### Post by Elfy on 2012-11-06
sudo ppa-purge ppa:*nameofppa*

For example I used it to purge the tomahawk ppa with 

sudo ppa-purge ppa:tomahawk/ppa

---

### Post by rburkartjo on 2012-11-06
so would this be right then

sudo ppa-purge ppa:xubuntu-dev-xfce4_12-quantal.list/ppa

should be colon where angry face appears

---

### Post by NikTh on 2012-11-06
Hi , 

you have to know the name of the ppa.
see ```
man ppa-purge
``` for more info. 

If I guessed correctly the ppa name is this : ppa: xubuntu-dev/xfce-4.10 

So the correct command is 
```
sudo ppa-purge ppa:xubuntu-dev/xfce-4.10 
sudo apt-get update
sudo apt-get dist-upgrade
``` 

Thanks

---

### Post by rburkartjo on 2012-11-07
ni tks that was what i was looking for

---

### Post by fyfe54 on 2012-11-07
I have been using Y-PPA-Manager for this.
It's in the Software Center.

---

### Post by NikTh on 2012-11-07
> **rburkartjo said:**
> that was what i was looking for

[Do not forget to mark the thread as solved.](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

:)

---

