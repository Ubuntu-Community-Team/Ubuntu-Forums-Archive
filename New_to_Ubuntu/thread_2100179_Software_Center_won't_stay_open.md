---
title: "Software Center won't stay open"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by slmehl on 2012-12-31
Ubuntu 12.04

Hello --

I will be in this group for a long time!
I installed Skype.  Now, Software Center won't stay alive.

I tried this sequence:
sudo apt-get purge software-center
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install software-center
sudo dpkg-reconfigure software-center --force

and got
E: Malformed line 5 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

A posting about a similar problem said to post the contents of 
sources.list
# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

Can anyone help me with this?

Thanks in advance,

Larry Mehl

---

### Post by ubudog on 2013-01-01
See if [this]("http://askubuntu.com/questions/78951/how-do-i-remove-a-malformed-line-from-my-sources-list") helps.

If so, run:
```
sudo apt-get update
```

And see if the error goes away.

---

### Post by slmehl on 2013-01-01
Thanks ubudog --

Editing sources.list fixed it.

Question:
What part of Linux does not prefix "partner" with "ubuntu precise"
in
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner  ?

Larry

---

