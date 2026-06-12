---
title: "Changing elementary to Lubuntu"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by ary_samsura on 2014-06-09
Hi, is there anyone can help me to explain how can I change my elementary to Lubuntu? I already have elementary OS in my old laptop but I think I have a more lightweight OS. so I&#7743; thiking to change it to Lubuntu. Can anyone help me how to do it? Thanks.

---

### Post by sudodus on 2014-06-09
It is possible but difficult and risky to change one desktop environment to another. So before trying you should ***backup*** your data.

Often you can get along simply by installing the desktop environment for Lubuntu into your present Elementary system

```
sudo apt-get install lubuntu-desktop
```

There might be some problems, maybe small. However, it is not easy to create a pure Lubuntu (removing everything from the other desktop environment); trying to do that might create big problems.

I think it is faster and easier to make a fresh installation or a dual boot system.

---

### Post by Vladlenin5000 on 2014-06-09
Hi, welcome.

Lubuntu is Ubuntu with LXDE instead of Unity; Elementary is Ubuntu with their own desktop environment (I don't remember exactly how it's called) instead of Unity. 
Bottom line: There aren't so many differences, just the desktop enviroments (GUI). Some are indeed 'lighter' than others and the one Lubuntu uses is known for being really 'light' (I don't know about Elementary, never used it). You actually don't change one into another - they are the roughly the same already. You can install/add LXDE (or lubuntu-desktop) to your current OS but that alone won't remove the DE Elementary uses and if you intended to remove that one it'll be much harder and time consuming than just doing a simple backup of your contents and then install what you really want. Also the chances of conflicts and/or redundant or duplicated features - ie, a total mess - are quite high whenever you install more than one DE.

---

### Post by ary_samsura on 2014-06-10
Thank you very much for the comments. I think I will try to do the fresh installation of Lubuntu to my computer.

---

