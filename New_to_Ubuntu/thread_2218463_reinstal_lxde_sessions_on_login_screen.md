---
title: "reinstal lxde sessions on login screen"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-04-20
i went to usr/share/xsessions and delete lxde. note i only deleted from xsessions not from my computer. how can i get the xsessions option back on my login screen. tks

---

### Post by vasa1 on 2014-04-20
What exact command did you use? 
If you used a file manager, it may be in trash?
What is your OS? 
What is its version?
I have Lubuntu 14.04 but do not see "lxde" in */usr/share/xsessions*:
```
[08:05 AM] /usr/share/xsessions $ ll
total 20
drwxr-xr-x   2 root root 4096 Apr 15 04:19 ./
drwxr-xr-x 209 root root 4096 Apr 17 23:37 ../
-rw-r--r--   1 root root  385 Nov  1 19:10 Lubuntu.desktop
-rw-r--r--   1 root root  238 Nov  1 19:10 Lubuntu-Netbook.desktop
-rw-r--r--   1 root root  198 Dec 22 16:56 openbox.desktop
[08:05 AM] /usr/share/xsessions $ 
```

You could try **sudo apt-get install lxde**. This may restore the missing file.

---

### Post by steeldriver on 2014-04-21
It should be provided by the **lxde-common** package --> [http://packages.ubuntu.com/trusty/all/lxde-common/filelist](http://packages.ubuntu.com/trusty/all/lxde-common/filelist)

---

### Post by rburkartjo on 2014-04-21
steel tks i had already tried sudo apt-get install lxde and that didnt work. your last post worked. i just reinstalled lxde-common from the spm.

---

