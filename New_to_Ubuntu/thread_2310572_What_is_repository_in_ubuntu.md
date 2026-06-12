---
title: "What is repository in ubuntu"
date: 2016-01-20
forum: New to Ubuntu
---

### Post by Siddharth_Syal on 2016-01-20
I'm a new user to Ubuntu and many a times while installing some applications in Ubuntu I came across the term repository. Can any one tell me what is it exactly ?

---

### Post by yancek on 2016-01-20
The servers where official Ubuntu software is downloaded from when you use the Ubuntu Software Manager or the apt-get command.

---

### Post by Bucky Ball on 2016-01-20
It's like a designated storage area for specific software. It holds packages users can access from a central location, usually using a package manager (like Software Centre or Synaptics for Ubuntu and Xubuntu). [See here]("https://en.wikipedia.org/wiki/Software_repository").

---

### Post by mastablasta on 2016-01-20
it's basically server (along with it's various mirrors) that hold all the packages (programs). kind of same thing as Apple Store, Google Play, ...

---

### Post by Siddharth_Syal on 2016-01-20
Thank you everyone.

---

### Post by grahammechanical on 2016-01-20
You will also see the term Software Sources = source of software. Our installation of Ubuntu has a list of software sources. It is a text file called sources.list. It contains the URLs to the repositories. This is just one of the repositories in my sources.list

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe

It tells the update manager and the software centre where to fetch software from. Archives is another term that is used.

Regards.

---

