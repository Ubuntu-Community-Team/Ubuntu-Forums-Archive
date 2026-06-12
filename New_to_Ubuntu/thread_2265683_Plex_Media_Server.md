---
title: "Plex Media Server"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by mdavis1231 on 2015-02-16
I'm totally clueless to things like this.  Plex Media Server is out of date in the Ubuntu 14.04 LTS Software Center.  I was just wondering if anyone knows if Plex has any intention or interest in upgrading to the latest versions anytime in the near future.  How do things like this work?

---

### Post by grier-devon on 2015-02-17
I believe it is on the plex team to submit the app to Canonical for review which I have heard to be a pain and a long process, not sure if that is true or not though. However if you are needing the latest version of an application many development teams are using "ppa" system. Here is the official plex ppa

[https://launchpad.net/~plexapp/+archive/ubuntu/plexht](https://launchpad.net/~plexapp/+archive/ubuntu/plexht)

If you have never installed a ppa this is how you would install the ppa for plex

```
sudo apt-add-repository ppa:plexapp/plexht
sudo apt update
sudo apt install plexhometheater
```

EDIT: I am not sure if you have ever used ppa's but remember these are not official repositories, many of them are maintained buy the official development team's. I am not one to say "Don't use ppa's" as I use a few myself just remember to be cautious.

---

### Post by andrew203 on 2015-02-22
Or you can go to their site and download the deb  file for Linux.  Depends if u want to run the server or the home theater box  really.  Currently no auto update ppa for plex  server

---

### Post by mooreted on 2015-02-22
I just downloaded it from the Plex website. Currently running Plex Server Version 0.9.11.7, though it shows I have an update available.

---

