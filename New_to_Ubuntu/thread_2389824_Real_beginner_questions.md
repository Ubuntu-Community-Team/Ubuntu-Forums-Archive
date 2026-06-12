---
title: "Real beginner questions"
date: 2018-04-21
forum: New to Ubuntu
---

### Post by cokuspocus on 2018-04-21
This may be a stupid question
I'm trying to set up ubuntu server and am having several issues. 
1.) I don't really know what it can be used for/ how I'll know when its actually working/ how to use it
2.) Whenever i try to do much of anything it gives me errors
This is what happens when i do:
```
sudo apt-get update
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
   Temporary failure resolving 'us.archive.ubuntu..com'
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
   Temporary failure resolving 'security.ubuntu.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
   Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
   Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/-updates/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.com/ubuntu/dists/xenial-backports/InRelease](http://us.archive.com/ubuntu/dists/xenial-backports/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```
I suspect i may not be connected to a network or something? 
I honestly have no idea what im doing

---

### Post by cruzer001 on 2018-04-21
Here's what it can be used for.

[https://help.ubuntu.com/lts/serverguide/index.html](https://help.ubuntu.com/lts/serverguide/index.html)

The rest of us run a desktop install.

[https://help.ubuntu.com/stable/ubuntu-help/index.html](https://help.ubuntu.com/stable/ubuntu-help/index.html)

---

### Post by mastablasta on 2018-04-23
looks like the updates server is out of action (maybe under maintenance). you can switch it to another one near you.

read this and particularly see the second answer: 
[https://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

---

