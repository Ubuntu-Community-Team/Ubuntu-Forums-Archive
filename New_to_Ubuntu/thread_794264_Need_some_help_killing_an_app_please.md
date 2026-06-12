---
title: "Need some help killing an app please"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by i-like-knives on 2008-05-14
Hi there,
I am a green beginner. I THOUGHT (see what I get for thinking?) I had removed limewire (I'm so sorry, I'm learning. I'm a Windows convert) on a previous remove command from the terminal. I used the remove command:

glenn@Buntu:~$ sudo apt-get remove limewire
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package limewire

Yet, there is still an icon in my apps menu which will not leave. When I click on it, it does start the limewire install wizard. My question is:  How can I remove all traces of limewire and get rid of it's entrails too? I looked but could not find correct procedure. Any help would be great. Should I re-install the app and then kill it??? Thanks, -Glenn

---

### Post by Oldsoldier2003 on 2008-05-14
> **i-like-knives said:**
> Hi there,
I am a green beginner. I THOUGHT (see what I get for thinking?) I had removed limewire (I'm so sorry, I'm learning. I'm a Windows convert) on a previous remove command from the terminal. I used the remove command:

glenn@Buntu:~$ sudo apt-get remove limewire
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package limewire

Yet, there is still an icon in my apps menu which will not leave. When I click on it, it does start the limewire install wizard. My question is:  How can I remove all traces of limewire and get rid of it's entrails too? I looked but could not find correct procedure. Any help would be great. Should I re-install the app and then kill it??? Thanks, -Glenn
since you did not install the application using apt-get and its not in the repositories you cannot uninstall it that way.

since you probably downloaded the file from the limewire web site the way to uninstall it would be

```
sudo dpkg -P limewire-basic
```

---

