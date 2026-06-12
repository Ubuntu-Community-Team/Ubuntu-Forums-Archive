---
title: "Flash player"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by wacbiarf on 2012-09-08
I installed flash before on ubuntu with firefox. It did not work properly so i uninstalled it and now i cannot install again. It gets stuck when applying changes. So i killed the process.

Firefox redirects loadings to software center.
Adobe itself does the same.
Flash aid is dead.

So is there any way to install flash  for me?

---

### Post by vasilbelarus on 2012-09-08
So, what is the problem? why you don`t want to download it with software manager?

---

### Post by wacbiarf on 2012-09-08
Because it gets stuck when applying changes every time i try.

---

### Post by Epodx64 on 2012-09-08
From a terminal try 
sudo apt-get install flashplugin-installer

---

### Post by wacbiarf on 2012-09-08
```
ibrahim@ibrahim-MS-7585:~$ sudo apt-get install flashplugin-installer
[sudo] password for ibrahim: 
Paket listeleri okunuyor... Bitti
Ba&#287;&#305;ml&#305;l&#305;k a&#287;ac&#305; in&#351;a ediliyor.       
Durum bilgisi okunuyor... Bitti       
Önerilen paketler:
  x-ttcidfont-conf ttf-mscorefonts-installer ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
A&#351;a&#287;&#305;daki YEN&#304; paketler kurulacak:
  flashplugin-installer
Yükseltilen: 0, Yeni Kurulan: 1, Kald&#305;r&#305;lacak: 0 ve Yükseltilmeyecek: 29.
&#304;ndirilmesi gereken dosya boyutu 0 B/8.102 B
Bu i&#351;lemden sonra 139 kB ek disk alan&#305; kullan&#305;lacak.
Paketler önyap&#305;land&#305;r&#305;l&#305;yor ...
Selecting previously unselected package flashplugin-installer.
(Veritaban&#305; okunuyor... 144699 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.238ubuntu0.12.04.1_i386.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.238.orig.tar.gz



```
some of it is in Turkish but that's what i see. it stopped.
edit: it's stuck again.

---

### Post by tienlbhoc on 2012-09-08
- install from ubuntu software center
- go to adobe web, download deb file.
- using another browser like chrome

---

### Post by wacbiarf on 2012-09-08
everything came to start. 

&#304; do not know how to download .deb file, i couldn't find it.  
Chrome browser is too big for my internet connection. (18 kb/sec and often breaks)
man, i need help.

---

