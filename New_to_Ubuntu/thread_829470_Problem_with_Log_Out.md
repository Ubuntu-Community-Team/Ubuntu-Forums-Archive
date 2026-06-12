---
title: "Problem with Log Out"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-14
Hello, my ubuntu act weirdly during log out. When i re-login, Ubuntu will ask for my username and password twice; i enter the combination the first time and when press enter, system will go back to login windows once again. when i re-enter the combination, system will login to Desktop as normal. What should be the problem

---

### Post by Absolute-Zero on 2008-06-14
Haha, sounds a like a very famous Trojan Horse, now i am not saying it is, but i knew one before. 

It could be something similar to some sort of survailence software, first time it records your information and gives you an error, and second time it gets back to normal and lets you login. THIS WAS VERY FAMOURS TROJAN BACK 5 YEARS AGO, this is unlikely that you have it on your computer, unless you weere doding or going some where u not sappoused to lol (i ma  just being honest

---

### Post by cariboo on 2008-06-14
CHeck your /etc/hosts file it should look something like this:

```
127.0.0.1	localhost
127.0.1.1	intrepid
```

In your case replace intrepid with your hostname. If you don't know what your hostname is in a terminal type:

```
hostname
```

This is a pretty common problem.

Jim

---

