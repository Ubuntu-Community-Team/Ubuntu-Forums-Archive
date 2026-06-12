---
title: "Opera Browser super slow in 8.04"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by frank002 on 2008-08-31
Due to some Flash problems with FF 3  I downloaded and installed Opera 9.52. While Opera seems to handle Flash better, it is extremely slow. I disabled IPv6 in /etc/modprobe.d/aliases but Opera is still very slow. Has anyone else run into this  problem? By the way, FF 3 is very fast.  Any suggestions will be appreciated. Thanks.

---

### Post by jemate18 on 2008-08-31
> **frank002 said:**
> Due to some Flash problems with FF 3  I downloaded and installed Opera 9.52. While Opera seems to handle Flash better, it is extremely slow. I disabled IPv6 in /etc/modprobe.d/aliases but Opera is still very slow. Has anyone else run into this  problem? By the way, FF 3 is very fast.  Any suggestions will be appreciated. Thanks.

just use firefox and to enable flash player
check my post here.. it is installing adobe flash player 9 when you download the tbz from the adobe website
> [http://ubuntuforums.org/showthread.php?t=905806](http://ubuntuforums.org/showthread.php?t=905806)

__________________________________________
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by frank002 on 2008-08-31
Thank you for your quick reply but I already have Flash enabled. About:plugins shows flash 9.0 . It is not all the Flash sites just some. I read somewhere it is a Firefox problem.

---

### Post by jemate18 on 2008-08-31
> **frank002 said:**
> Thank you for your quick reply but I already have Flash enabled. About:plugins shows flash 9.0 . It is not all the Flash sites just some. I read somewhere it is a Firefox problem.

Try to reinstall opera. Did you install it using apt-get?

OR you can also try to download the .deb installer of OPERA,
remove your current OPERA, 
CD to the directory where you have stored your downloaded [yourOPERADownload].deb and execute this
```
dpkg --install [yourOPERADownload].deb
```

____________________________
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by jemate18 on 2008-09-01
> **frank002 said:**
> Thank you for your quick reply but I already have Flash enabled. About:plugins shows flash 9.0 . It is not all the Flash sites just some. I read somewhere it is a Firefox problem.

Did you try my suggestion in my post above? Did it worked?

____________________________
Mark this thread SOLVED
"https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are
able to do what you intend to do and DONT FORGET to THANK the people
who HELPED YOU by clicking the "thanks" button on the lower right
"medal icon" for their help and useful post

jemate18

---

### Post by Swenghk on 2008-09-01
I sympathize for you. Mine was slow as a Windows Computer on upgrade day :(

---

### Post by tuxxy on 2008-09-01
> **frank002 said:**
> Due to some Flash problems with FF 3  I downloaded and installed Opera 9.52. While Opera seems to handle Flash better, it is extremely slow. I disabled IPv6 in /etc/modprobe.d/aliases but Opera is still very slow. Has anyone else run into this  problem? By the way, FF 3 is very fast.  Any suggestions will be appreciated. Thanks.

Thats strange as my FF handles Flash sites better but Opera is quick at HTML

---

### Post by jemate18 on 2008-09-01
> **tuxxy said:**
> Thats strange as my FF handles Flash sites better but Opera is quick at HTML

I agree.. Opera best works with HTML

---

### Post by k3lt01 on 2008-09-01
Opera wont work at all for me. I tried it last week when I was having a problem with FF3 but it wouldn't open anything so I ditched it.

---

### Post by jemate18 on 2008-09-01
> **k3lt01 said:**
> Opera wont work at all for me. I tried it last week when I was having a problem with FF3 but it wouldn't open anything so I ditched it.

Did you get it via repositories? Or the Opera Website?

---

### Post by jemate18 on 2008-09-01
I have installed the new Opera which I have downloaded from the Opera website

File> opera_9.52.2091.gcc4.qt3_i386.deb
It works faster now. And no problems with flash


I have uninstalled my previous which I installed via repositories

---

### Post by k3lt01 on 2008-09-01
> **jemate18 said:**
> Did you get it via repositories? Or the Opera Website?The repository.

---

### Post by jemate18 on 2008-09-02
> **k3lt01 said:**
> The repository.

I have uninstalled the version which I got from the repository

and download the .deb file from the OPERA website - > This works better and faster...

---

