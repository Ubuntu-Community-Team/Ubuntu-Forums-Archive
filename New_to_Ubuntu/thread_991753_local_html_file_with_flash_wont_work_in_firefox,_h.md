---
title: "local html file with flash wont work in firefox, help needed"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by krtica on 2008-11-24
I'll try to explain situation as detailed as I can.
I have html file in local folder which basically runs embeded flash application. It is on wine/c:. (But same thing happen when I move it on any other place.)
It have a button which suppose to open another Firefox window with selected chapter. But when I click on it, nothing is happen.
I installed Firefox under WINE, and opened same file. Everything is fine.
I think that loaded files are some .xml files with defined styles. (?)
Ok, I'm aware of it that I can use Firefox under WINE to see those pages, but I would like to use pure Ubuntu as much as possible.
I compared preferences on both Firefoxes, under Ubuntu and under WIne, and it looks same.
So, does anyone have some advice?

---

### Post by chuckyp on 2008-11-24
Install flash for ubuntu. Basically open add/remove or open a terminal and:
```

$ sudo aptitude install flashplugin-nonfree

```

---

### Post by krtica on 2008-11-24
I forgot to tell - newest version of flash is installed on both Firefoxes. :D

---

### Post by krtica on 2008-11-24
I also tried ***Opera 9.62**, Build 2466, Platform Linux, System i686, 2.6.27-7-generic, Qt library 3.3.8b* which is working quite well and have no flash issues, and I'm still unable to run this page properly.
That's why I'm thinking that maybe it's some kind security issue in Ubuntu... :confused:
Is there anything like this? Some policy for running local flash applications?

---

