---
title: "Youtube troubles"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-06-18
Hey

youtube videos seem to load but they only play like 2 seconds and no sound then stop.

I'm using firefox 3.

---

### Post by aktiwers on 2008-06-18
I had this problem too on my other computer.
It was because I had an old version of Flash installed.

Go install the latest version of Flash, download the tar.gz from here:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash)

to your desktop and right-click and extract it.

Then open terminal (applications=>accessories=>Terminal)
And type:
```
cd Desktop/install_flash_player_9_linux/
```To go to the newly extracted folder.

Then make the install file executable:
```
sudo chmod +x flashplayer-installer 
```

And lastly run it to install:
```
sudo ./flashplayer-installer
```Now restart Firefox and see if it works :)

---

