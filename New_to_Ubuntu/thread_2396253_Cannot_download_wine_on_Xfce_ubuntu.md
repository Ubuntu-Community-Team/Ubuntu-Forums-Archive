---
title: "Cannot download wine on Xfce ubuntu"
date: 2018-07-12
forum: New to Ubuntu
---

### Post by iamdantheneedhelp on 2018-07-12
So, i have been doing what everyone says, apt update, that stuff, and sometimes it works, and when I type in 
sudo apt-get install --install-recommends winehq-stable
this is what I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winehq-stable

somebody help please.. i have a acer 15 chromebook aswell..

---

### Post by oldos2er on 2018-07-12
Which version are you on? For 18.04 there is wine-stable. There's no "hq" in any of the wine package names that I see.

---

### Post by iamdantheneedhelp on 2018-07-12
I guess i might be on something else, because im on 18.04, but it says winehq everytime i check.. Is this the right place [https://wiki.winehq.org/Ubuntu?](https://wiki.winehq.org/Ubuntu?)

---

### Post by oldos2er on 2018-07-13
So you added the repo using ```
sudo apt-add-repository [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)
``` ? You would then run ```
sudo apt update
``` followed by ```
sudo apt-get install --install-recommends winehq-stable
``` After you add or make any change to your sources, you always need to run```
sudo apt update
```

Let me know if this works for you.

---

