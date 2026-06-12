---
title: "[SOLVED] flash not working in opera!"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by sujoy on 2008-05-08
I have flash installed and it works fine in firefox3, plays the youtube videos well enough, but in opera 9.27 it just shows me a grey box.

How do i get my opera to use flash?

---

### Post by sharks on 2008-05-08
[http://www.opera.com/linux/docs/plugins/install/](http://www.opera.com/linux/docs/plugins/install/)

This will help u a lot.

---

### Post by subzero316 on 2008-05-08
D/l Flash9 from [this link]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz")
Now you need to extract this file using the following command

```
sudo tar xzvf install_flash_player_9_linux.tar.gz
```

get in the install_flash_player_9_linux directory

```
cd install_flash_player_9_linux/
```

```
sudo cp libflashplayer.so /usr/lib/opera/plugins

sudo cp flashplayer.xpt /usr/lib/opera/plugins
```

install following packages

```
sudo aptitude install ia32-libs ia32-libs-sdl ia32-sun-java5-bin ia32-libs-gtk flashplugin-nonfree sun-java6-plugin sun-java6-jre
```

 install  qt3 libs download qt3 libs from [This link ]("http://mirrors.kernel.org/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb")
install this package 

```
sudo dpkg -i &#8211;force-architecture libqt3-mt_3.3.8really3.3.7-0ubuntu5_i386.deb
```

---

### Post by sujoy on 2008-05-08
thanks for the response, i will try out and report back.

---

### Post by antisocialist on 2008-05-08
did it work?

---

### Post by zvacet on 2008-05-09
Install Opera 9.5 beta or install older flash from [here #13.]("http://ubuntuforums.org/showthread.php?t=745325&page=2")

---

### Post by sujoy on 2008-05-09
> **antisocialist said:**
> did it work?

not yet :(

---

### Post by mr.propre on 2008-05-09
> **zvacet said:**
> Install Opera 9.5 beta or install older flash from [here #13.]("http://ubuntuforums.org/showthread.php?t=745325&page=2")

Confirmed, latest flash plugin only works under the beta.

---

