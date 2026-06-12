---
title: "How to install a fresh version of eclipse?"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by chirag403 on 2012-01-30
Hey guys,

I'm new to linux in general and I'm using ubuntu 11.10. I'm trying to work in Eclipse using the android sdk.

I was initially having a lot of problems trying to get android sdk to install properly and I finally got it to work after installing the ia32-libs.

But now I'm having problems with the eclipse update. It says it has dependency conflicts. If I uninstall eclipse and reinstall it from the software centre nothing changes and I don't know why. All the problems stay as it is which is really annoying.

I tried looking it up and I found a thread where everyone agreed that the best thing to do would be to re download the latest version from the eclipse site. But if I do that I have no idea where to extract it, it doesn't automatically show me a location like it would in windows. I read somwhere that I could put it in opt but then it doesnt show up in the start menu and now I cant even delete it from that folder.

I just want to install a fresh version of eclipse like how it was when I first installed it ever. It is okay if I have to install the ADT plugin and android sdk again because I now know how to do that properly. 

Also I have attached a screen shot of the dependency conflict in case anyone knows a way to resolve it without having to reinstall eclipse. Here's the link: [http://s9.postimage.org/9bmz08snj/Screenshot_at_2012_01_30_15_18_07.png](http://s9.postimage.org/9bmz08snj/Screenshot_at_2012_01_30_15_18_07.png)

Please Help. Thanks in advance.

---

### Post by lechien73 on 2012-01-30
Hi and welcome to the forums,

I also had a lot of problems installing the Android SDK, I followed this tutorial here, and it eventually seemed to work ok: [http://developer.android.com/sdk/installing.html](http://developer.android.com/sdk/installing.html)

I also installed Eclipse from the software centre, and it works ok.

---

### Post by chirag403 on 2012-01-30
Yeah now I know what to so I don't mind starting from scratch. But the problem is my current version of eclipse is messed up. And if I uninstall eclipse for the software center and re install from there, it doesn't change at all! It's the exact same eclipse with the exact same problem.

---

### Post by rgreener25 on 2012-01-30
try running ```
sudo dpkg --purge eclipse
``` then installing it again from the software center

---

### Post by lechien73 on 2012-01-30
I was doing a bit of research and it seems that the "Conflicting dependency" error sometimes isn't a dependency error at all, but a permissions issue.

If you open a terminal window and run:

```
gksu eclipse
```

Does the update work?

---

### Post by wolfen69 on 2012-01-30
I always *completely remove* apps from synaptic, then
```
sudo apt-get clean && sudo apt-get autoremove
```
Reinstall eclipse, and you should then have a fresh install of eclipse.

---

