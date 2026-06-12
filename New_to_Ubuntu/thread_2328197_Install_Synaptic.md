---
title: "Install Synaptic?"
date: 2016-06-18
forum: New to Ubuntu
---

### Post by dannyk2 on 2016-06-18
I decided to try out Ubuntu-16.04 LTS and have been trying without any luck to install Synaptic Package Manager. Have tried:

$ sudo apt-get install synaptic and $ sudo apt install synaptic

Speaking for myself i would much rather use Synaptic than Software boutique or Ubuntu Software

---

### Post by Dennis N on 2016-06-18
And what is the result when you use those commands?

---

### Post by Linuxratty on 2016-06-18
Synaptic is installed. You get a little icon you can click to use it. I've always used Synaptic and I like it.

---

### Post by dannyk2 on 2016-06-18
When i open a terminal and type $ apt-get install synaptic 
I get the following:

danny@my-ubuntu:~$  apt-get install synaptic
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
danny@my-ubuntu:~$

If synaptic is installed by default in Ubuntu-16.04 i can't find it?

---

### Post by jimmy-frydkaer on 2016-06-18
You need to be root in order to install synaptic

```
sudo su
```

then type your login code

then

```
apt install synaptic -y
```

---

### Post by Dennis N on 2016-06-18
> **dannyk2 said:**
> When i open a terminal and type $ apt-get install synaptic 
I get the following:

danny@my-ubuntu:~$  apt-get install synaptic
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
danny@my-ubuntu:~$

If synaptic is installed by default in Ubuntu-16.04 i can't find it?

Well, it's because you forgot to use sudo before your command. I did the same here (forgot sudo) and you see what happens:

```
dmn@Sydney:~$ apt-get install synaptic
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

Use **sudo apt-get install synaptic** like you had it in post #1.

---

### Post by grahammechanical on 2016-06-18
> If synaptic is installed by default in Ubuntu-16.04 i can't find it?

I cannot speak for Ubuntu Mate but Synaptic has not been part of the default Ubuntu install for a couple of years.

---

### Post by vasa1 on 2016-06-19
> **jimmy-frydkaer said:**
> You need to be root in order to install synaptic

```
sudo su
```

then type your login code

then

```
apt install synaptic -y
```

Please, **sudo apt install ...** or **sudo apt-get install ...** will be good enough. Let's not complicate things :)

---

### Post by jimmy-frydkaer on 2016-06-19
Sorry my bad

---

### Post by pfeiffep on 2016-06-19
> **dannyk2 said:**
> I decided to try out Ubuntu-16.04 LTS and have been trying without any luck to install Synaptic Package Manager. Have tried:

$ sudo apt-get install synaptic and $ sudo apt install synaptic

Speaking for myself i would much rather use Synaptic than Software boutique or Ubuntu SoftwareResponses thus far are right on the money...
For completeness Synaptic Package Manager is available to install from both Software Boutique, and Ubuntu Software.

@grahammechanical *"I cannot speak for Ubuntu Mate but Synaptic has not been part of the default Ubuntu install for a couple of years."*

Synaptic is not installed by default in Ubuntu MATE 16.04

---

