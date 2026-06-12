---
title: "help installing software already downloaded"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by allarmguy on 2008-10-10
HI! I`m new to Ubuntu stuff...I downloaded a program  and I have no idea how to install it.It is on my desktop I click over but nothing happens.PLEASE!!!!

---

### Post by ronnielsen1 on 2008-10-10
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Recommend reading the link above.

---

### Post by Orange_and_Green on 2008-10-10
First of all, hello. A heartfelt welcome to Ubuntu and to the forums.

Well, that depends on what that "program" file actually is. If it's a binary file, you might try right-clicking it, selecting "Properties"->"Permissions" and check the "allow executing file as program" box.

Perhaps I can tell you more if you post the file's name (specifically, the extension).

Good luck :KS

---

### Post by hyper_ch on 2008-10-10
how did you download it? what did you download?

---

### Post by allarmguy on 2008-10-10
It is <netbeans 6.1>

---

### Post by allarmguy on 2008-10-10
It is netbeans 6.1 and I get it from netbeans site

---

### Post by hyper_ch on 2008-10-10
```

sudo apt-get install netbeans

```

--> it's in the universe repo so you might need to enable that at first.

---

### Post by allarmguy on 2008-10-10
It work but is not installing from the place what i want.He goes out in the internet to dowload.I was asking if there is a command to make him install from a place that I WANT,...desktop,documents folder...etc

---

### Post by hyper_ch on 2008-10-10
you should stick to the software in the repos... those are tested.

---

### Post by niteshifter on 2008-10-10
Hi,

Take hyper_ch's advice and get netbeans from the repositories, it's much easier that way. Hardy repos show netbeans 6.0, once you have 6.0, you can update netbeans from within netbeans.

However, if you are bound and determined to manually install it yourself, follow the instuctions [here.]("http://www.netbeans.org/community/releases/61/install.html") (netbeans.org, installation instructions). _You must have a JDK - of the correct version AND update - installed first!_

FWIW: I've been using netbeans since there's been a netbeans to use. Installing from a distribution's repository is much, much easier than manually installing it. I do this with Linux, I do this with Unix. You've no choice in Windows (typical!). Manually installing tends to clutter up your home folder.

---

