---
title: "Downloading from Ubuntu Software Center"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-04-02
Hi, I am having trouble downloading software from USC. If I have (for example) file with 100mB. First 80mB goes with 400kBps (which is the maximum speed), but the next part is like 20kBps. How can I fix this?

Xubuntu 12.10 by the way.

---

### Post by Paqman on 2013-04-02
Sound odd. You could try switching to a different server. Open up Software Sources and click on: Download from > other > select best server and it'll switch to the fastest server available.

---

### Post by ViliX64 on 2013-04-02
Yea, I tried this solution, I tried about 20 servers in 5 countries. I even tried to "choose best server" from system, but without any succes. :(

---

### Post by Paqman on 2013-04-02
Does it do the same when you try to install software another way, such as Synaptic, or on the command line? If so it could be something on your network or your ISP.

---

### Post by Bresser on 2013-04-02
> **Paqman said:**
> Does it do the same when you try to install software another way, such as Synaptic, or on the command line? If so it could be something on your network or your ISP.
What he means, if you do not understand is. ```
apt-get install blah blah blah whatever program you want
``` or ```
sudo apt-get install blah blah blah
``` "sudo" if im not mistaken downloads from root which is an equivalent of like windows' use as administrator function.

---

### Post by sccsammy on 2013-04-02
Ya, i had the same problem for a while when i first installed ubuntu. I used command line and it would work. And then after a couple update it worked fine. I wish i knew specifially which ones or which packages.

---

### Post by ViliX64 on 2013-04-02
Downloading via codes doest not work either, it takes more than an hour to download 100mB package.

---

