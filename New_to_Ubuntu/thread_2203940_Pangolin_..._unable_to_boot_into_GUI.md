---
title: "Pangolin ... unable to boot into GUI"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by czgirb on 2014-02-06
[SIZE=2]i face the problem before and helped by **[Mastablasta]("http://ubuntuforums.org/member.php?u=964486")**[/SIZE] and here is the **[thread]("http://ubuntuforums.org/showthread.php?t=2198327&highlight=czgirb")**
but the problem was faced with screen showed:
> 
ubuntu 12.04.[SIZE=4]3[/SIZE] LTS czgirb tty1
czgirb login:
password:

but now it change to:
> 
ubuntu 12.04.[SIZE=4]**4**[/SIZE] LTS czgirb tty1
czgirb login:
password:

according to the following [URL]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"), 
* **12.04.1** is **12.10 = Quantal**
* **12.04.2** is **13.04 = Raring**
* **12.04.3** is **13.10 = Saucy**
so **12.04.4** is should be **14.04** or **trusty**
Do i should change the **release name** into **trusty**
Please guide me ...
Thank you.

---

### Post by czgirb on 2014-02-06
Just trying ... **trusty is unable** ... so I use **saucy**
but it show so many **Failed to fetch** item.
For example:
> Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/x/xorg-lts-saucy/xserver-xorg-video-all-lts-saucy_7.7+1ubuntu6~precise1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/x/xorg-lts-saucy/xserver-xorg-video-all-lts-saucy_7.7+1ubuntu6~precise1_i386.deb)
Could not resolve 'id archieve.ubuntu.com'
Please help me ...

---

### Post by czgirb on 2014-02-06
Dear all
Please tell me to to edit **Failed to Fetch** problem in **Command Line (not GUI, since I unable to boot to GUI)**
Please help ...............

---

### Post by wn1ytw on 2014-02-06
> **czgirb said:**
> Dear all
Please tell me to to edit **Failed to Fetch** problem in **Command Line (not GUI, since I unable to boot to GUI)**
Please help ...............

If the GUI not loading is a problem for you try this thread: [http://askubuntu.com/questions/209845/gui-is-not-displayed-anymore](http://askubuntu.com/questions/209845/gui-is-not-displayed-anymore)

Sorry I can't help with the Fetch Fail - I'm too noob :)

---

### Post by sandyd on 2014-02-06
> **czgirb said:**
> Just trying ... **trusty is unable** ... so I use **saucy**
but it show so many **Failed to fetch** item.
For example:

Please help me ...

try replacing id.archive.ubuntu.com with archive.ubuntu.com in /etc/apt/sources.list and running apt-get update

---

