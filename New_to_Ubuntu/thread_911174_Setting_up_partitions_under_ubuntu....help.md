---
title: "Setting up partitions under ubuntu....help"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by CARLiTO_ on 2008-09-05
Planning to install ubuntu today. Running windows as of now. Have 2 partitions, C: drive = 20 gb's. D: drive = 120 gb's. C: is used for my windows install and D: for music and movies. 

How would I go about getting a similar setup under ubuntu?

---

### Post by overdrank on 2008-09-05
Hi and welcome, you can use the auto partitioning or you can choose a setup manually. You may look here
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Moved to ABT :)

---

### Post by lswest on 2008-09-05
if you want to have a bit more control I recommend this under the manual partitioning option:

20GB ext3 with mountpoint of /

120GB ext3 with mountpoint /home (I'm taking the values you supplied above)

and a 1GB-2GB swap space (just choose swap as the filesystem type)  1GB should be fine unless you have less than 1GB of RAM

If you have any more questions, just ask, and welcome to Ubuntu

---

