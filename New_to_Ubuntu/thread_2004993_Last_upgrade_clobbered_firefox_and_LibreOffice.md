---
title: "Last upgrade clobbered firefox and LibreOffice"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by RH9R on 2012-06-16
Since the last upgrade, my firefox launcher failed to open firefox. I went to Synaptic and marked for reinstallation. It reinstalled, all is fine. 
 
Now, I try to open a word doc in LibreOffice and it fails to open the application and the doc. I tried synaptic reinstall, complete removal and install, and get the following:
E: /var/cache/apt/archives/libreoffice-common_1%3a3.5.4-0ubuntu1~lucid1_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libreoffice/share/template/common/layout/lyt-paper.otp')
E: /var/cache/apt/archives/libreoffice-core_1%3a3.5.4-0ubuntu1~lucid1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libreoffice/program/libcharttoolslo.so')

'Tried to reinstall OpenOffice after uninstalling Libre and it could not install either. 
 
Any help would be appreciated.

---

### Post by drpjkurian on 2012-06-17
Hi try this tip
1) Close any package manager, this includes Synaptic, Update Manager and Software Center.
2) Open terminal and execute the following commands (press Enter after every line to execute):
Code:

```
sudo pkill apt
sudo apt-get clean
sudo pkill apt
```

3) Start Update Manager and hit "Check".
3a) If you have any updates, install the updates.
4) Close Update Manager.

Please read this file if you are interested to know the meaning of the error message
[http://raphaelhertzog.com/2011/06/27/deciphering-one-of-dpkgs-weirdest-errors-short-read-on-buffer-copy/](http://raphaelhertzog.com/2011/06/27/deciphering-one-of-dpkgs-weirdest-errors-short-read-on-buffer-copy/)

---

### Post by RH9R on 2012-06-17
Dr. Kurian, its wonderful! Thank You!
 
 I sure appreciate your kind help. It worked well and Libreoffice loaded normally from the Ubuntu Software Center. Wish I could be similarly helpful for you.

---

### Post by drpjkurian on 2012-06-18
Hi
You are most welcome

---

