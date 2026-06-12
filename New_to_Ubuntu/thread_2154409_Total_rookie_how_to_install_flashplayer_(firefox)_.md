---
title: "Total rookie: how to install flashplayer (firefox) step by step"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by HelmuthS on 2013-06-14
Hey folks,

just tried to install flashplayer on ubuntu. So entered the command **sudo apt-get install flashplugin-nonfree. **Totally worked. Then downloaded .tar.gz. file. But tried to unpack the file, but what next? Can someone help me? Would be awesome. Thanks in advance!

---

### Post by deadflowr on 2013-06-14
change your command and use installer instead of non-free
so it be
```
sudo apt-get install flashplugin-installer 
```

or if you want a larger package of codecs and extras
```
sudo apt-get install ubuntu-restricted-extras
```

Note if installing the restricted packages, during the install a EULA for microsoft comes up. To select use the tab button and left right buttons to choose yes or no.

---

### Post by slickymaster on 2013-06-14
> **HelmuthS said:**
> Hey folks,

just tried to install flashplayer on ubuntu. So entered the command **sudo apt-get install flashplugin-nonfree. **Totally worked. Then downloaded .tar.gz. file. But tried to unpack the file, but what next? Can someone help me? Would be awesome. Thanks in advance!
?!
All you have to do is to open Ubuntu Software Center and type **Adobe Flash plugin** in the search box. The first option given to you should be _Installer for the Adobe Flash plugin for Mozilla_. Just click on the 'Install' button on the right and you're good to go.

You should always install software using Ubuntu Software Center, particularly when you don't have a solid knowledge of Ubuntu/Linux.

---

### Post by Cheesemill on 2013-06-14
Once you've run the apt-get command then unless you get any errors it's all done. There's no need to download anything else.

---

