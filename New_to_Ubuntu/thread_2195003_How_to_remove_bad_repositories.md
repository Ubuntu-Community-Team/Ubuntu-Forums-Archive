---
title: "How to remove bad repositories"
date: 2013-12-21
forum: New to Ubuntu
---

### Post by abhishes on 2013-12-21
When I do a 

sudo apt-get update.

I can see

Err [http://archive.canonical.com](http://archive.canonical.com) [distro]/partner amd64 Packages                                                           
  404  Not Found [IP: 91.189.92.191 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-backports/multiverse Translation-en                                                 
Err [http://archive.canonical.com](http://archive.canonical.com) [distro]/partner i386 Packages                                                            
  404  Not Found [IP: 91.189.92.191 80]


How can I remove these two bad repositories

---

### Post by raja.genupula on 2013-12-21
You have two ways

Method 1: Open your Software sources and from the Other software Tab you can disable them by unselecting the checkboxes of these particluar repos.

Method 2 : Install Y PPA Manager

---

### Post by ian-weisser on 2013-12-21
Do try a few more times. If you hit the repository while it is updating, a 404 is possible.

Edit the sources.list file.
```
sudo nano /etc/apt/sources.list
```
Comment out the offenders by putting a hashtag (#)  at the front of the relevant lines.

---

### Post by abhishes on 2013-12-22
Thanks. editing the sources.list resolved the issue for me.

---

### Post by CitadelUniversal on 2013-12-22
If the issue is solved please remember to mark this as [solved] at the title heading, Thank you.

---

