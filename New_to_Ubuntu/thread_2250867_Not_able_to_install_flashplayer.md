---
title: "Not able to install flashplayer"
date: 2014-10-31
forum: New to Ubuntu
---

### Post by silverbear2 on 2014-10-31
I'm new here and new to the world of Ubuntu, so forgive my lack of knowledge.  I'm also new to Openshot video editor and have signed in to their forum.  In attempting to look at member's videos I receive a prompt saying that in order to view them I need to install flash (or maybe it said flashplayer)... at any rated I clicked on that and it took me to a firefox page saying that I would need to wait for an update in Ubuntu.  I don't really know where to go from here, but can't do much with openshot without being able to view videos.  Is there a solution to this?  Would another browser such as Google chrome work better and is that even compatible with Ubuntu?  Thank you for your patience with a newbie.  
Silverbear

---

### Post by oldos2er on 2014-10-31
You can install flash from the Software Center: [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by Alireza_Zamani on 2014-10-31
Hello Dear !
from [this page]("http://mirror.sito.ir/Adobe/Flash%20Player/") download appropriate package for your hardware platform and install that .
for example :

> $ rpm -i Flash_Player_11.2_for_other_Linux_(.rpm)_64-bit.rpm

cheers .

---

### Post by grahammechanical on 2014-10-31
If you are using Firefox then go to the Ubuntu Software Centre and search for flashplugin installer. That should do it for FireFox.  The installer will install the plugin. It is a little bit more complicated for Chromium. We need something called pepper flash.

Chrome is compatible with Ubuntu but it is not in the Ubuntu Software Centre because it is proprietary software.

Regards.

---

### Post by Bucky Ball on 2014-10-31
> **grahammechanical said:**
> ... go to the Ubuntu Software Centre and search for flashplugin installer. That should do it for FireFox.  The installer will install the plugin. It is a little bit more complicated for Chromium. We need something called pepper flash.

Chrome is compatible with Ubuntu but it is not in the Ubuntu Software Centre because it is proprietary software.

Regards.

^^^
This. flashplugin-installer is all you need to install flash for Firefox. 

> **Alireza_Zamani said:**
> Hello Dear !
from this page download appropriate package for your hardware platform and install that .


^^^
This ... is the long way round and maybe not the best or easiest place to start for a newcomer. ;)

---

### Post by 3246251196 on 2014-10-31
Maybe I am missing something, but why not just: 

bring up a terminal (cntl + alt + t) [[[ i think it is this combination, i always change them to my own preference ]]] and type "sudo apt-get install flashplugin-installer" ?

---

### Post by Bucky Ball on 2014-10-31
> **3246251196 said:**
> ... why not just: 

bring up a terminal (cntl + alt + t) [[[ i think it is this combination, i always change them to my own preference ]]] and type "sudo apt-get install flashplugin-installer" ?

Because the Software Centre is the absolute easiest way to go if you've posted in **New to Ubuntu **and you're 

> **silverbear2 said:**
> ... new here and new to the world of Ubuntu

Please take user experience and the forum section into consideration when giving support. Of the two users that have posted code here, neither has actually mentioned how to open a terminal (at least ctl+alt+t doesn't work for me but I'm using xfce4). ;)

---

### Post by Alireza_Zamani on 2014-10-31
> **Alireza_Zamani said:**
> Hello Dear !
from [this page]("http://mirror.sito.ir/Adobe/Flash%20Player/") download appropriate package for your hardware platform and install that .
for example :

[COLOR=#000000]*$ rpm -i Flash_Player_11.2_for_other_Linux_(.rpm)_64-bit.rpm*[/COLOR][COLOR=#ff0000]
[/COLOR]
cheers .


edited !

---

