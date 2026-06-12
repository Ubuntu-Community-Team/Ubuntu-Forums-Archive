---
title: "[SOLVED] Desktop vs Server packages"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by acilate on 2008-12-01
I have not yet installed ubuntu on my server, I am only now making decisions about what I want to install.

My system will be used 90% of the time as a server: ftp, smb, mail, http, dns, etc.  However, I also would like to be able to use it as a remote desktop somewhat often.

I am trying to make the decision between the server and desktop flavors.  After reviewing some threads here, it seems as though the easiest choice would be the desktop, as all of those functions are installed by default.  However, the server optimized kernel has the geek in me leaning back towards the server.  It seems as though I want the best of both worlds.

My question is this, is there a document or web page that details the exact package differences between the server and desktop flavors?

I've seen the suggestion to run "sudo apt-get install ubuntu-desktop."  Does that install all of the packages normally installed in the desktop version that are omitted in the server version?

---

### Post by nhasian on 2008-12-01
yes.  you'll want to install the gdm as well.

first update software sources:

```
sudo aptitude update
```

then update your software:

```
sudo aptitude full-upgrade
```

finally install the desktop and its dependencies:

```
sudo apt-get install ubuntu-desktop gdm
```

---

