---
title: "Firefox 3 problem"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by singetak on 2008-05-06
I have problem in the Firefox 3 in ubuntu 8.04 slower than Firefox 2
Moreover the version 3 suddenly close with no warning.
Any idea

---

### Post by kestrel1 on 2008-05-06
FF3 is still a Beta version.
I was having problems myself & posted here: [http://ubuntuforums.org/showthread.php?t=775816](http://ubuntuforums.org/showthread.php?t=775816)
I am going to stick with FF2 for the time being. I would suggest that will be your best bet.

---

### Post by singetak on 2008-05-06
i think your right thanks .Any idea of how to install FF2 and uninstall FF3

---

### Post by justifier on 2008-05-06
to remove 

```
sudo apt-get remove firefox-3.0
```

to install FF2 download from the mozilla website will be your best bet, 

This its [www.getfirefox,com](www.getfirefox,com) for a direct link

---

### Post by xjb2003x on 2008-05-06
Something you may want to do before the removal is export your bookmarks.

:guitar:

---

### Post by Tatty on 2008-05-06
firefox 2 is still in the repos, after uninstalling FF3, do:

```
sudo apt-get install firefox-2
```


If you want to try to trace the problem with FF3, try running it from a terminal and see if it outputs an error when it crashes.

---

