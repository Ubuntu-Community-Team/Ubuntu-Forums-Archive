---
title: "[SOLVED] how do you load launchpad  to source list"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-06-02
I am trying to add launchpad to sources list so I can get firefox 3.0 rc2.  How would I go about doing this?

---

### Post by Het Irv on 2008-06-02
I am marking this for the Unanswered Post team.  Hopefully someone will help you from there.

---

### Post by bobbocanfly on 2008-06-02
I am assuming you want to get the latest Mozilla (Firefox etc.) stuff from the Mozilla Teams launchpad PPA (Personal Package Archive)?

To do this run this command:

```
gksudo gedit /etc/apt/sources.list
```

If you are running Ubuntu Hardy Heron 8.04 add this to the end of the file and press save:

> deb [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) hardy main

If you are running a different version (Gutsy, Feisty or whatever) replace hardy with whatever version you are actually using.

Now you need to update apt so it sees the new packages:

```
sudo apt-get update
sudo apt-get upgrade
```

If this fixes your problem please mark the thread as solved :)

---

