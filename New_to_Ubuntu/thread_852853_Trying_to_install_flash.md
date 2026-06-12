---
title: "Trying to install flash"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by highlyevolved on 2008-07-08
Im trying to install flash 10 beta 2 via the terminal but keep encountering errors.
It's getting me really frustrated.

I tried following this
[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

but when I go to paste 
tar -zxvf flashplayer10_install_linux_051508.tar.gz 
the errors begin.

Any help?

---

### Post by iaculallad on 2008-07-08
> **highlyevolved said:**
> Im trying to install flash 10 beta 2 via the terminal but keep encountering errors.
It's getting me really frustrated.

I tried following this
[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

but when I go to paste 
tar -zxvf flashplayer10_install_linux_051508.tar.gz 
the errors begin.


```
Any help?

Error as in "File not Found"? Try to change directory to where the file was downloaded to:

[CODE]cd /tmp
```

then issue back the command to untar the archive:

```
tar -zxvf flashplayer10_install_linux_051508.tar.gz
```

and the remaining commands too:


```
cd install_flash_player_10_linux
./flashplayer-installer
```

---

### Post by highlyevolved on 2008-07-08
The file is downloaded to my desktop so what command should I put in.

Thanks - really basic stuff for you but it really confuses me.

cheers!

---

### Post by iaculallad on 2008-07-08
> **highlyevolved said:**
> The file is downloaded to my desktop so what command should I put in.

Thanks - really basic stuff for you but it really confuses me.

cheers!

```
cd ~/Desktop
tar -zxvf flashplayer10_install_linux_051508.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```

One-Command-At-A-Time

---

### Post by aktiwers on 2008-07-08
Wouldnt it be like this?

```
cd ~/Desktop
tar -zxvf flashplayer10_install_linux_051508.tar.gz
cd install_flash_player_10_linux
sudo chmod +x flashplayer-installer
sudo ./flashplayer-installer
```

---

### Post by isaacj87 on 2008-07-08
> **aktiwers said:**
> Wouldnt it be like this?

```
cd ~/Desktop
tar -zxvf flashplayer10_install_linux_051508.tar.gz
cd install_flash_player_10_linux
sudo chmod +x flashplayer-installer
sudo ./flashplayer-installer
```

No, because it already has permission to be executable...it would be an unnecessary step.

---

### Post by iaculallad on 2008-07-08
> **aktiwers said:**
> Wouldnt it be like this?

```
cd ~/Desktop
tar -zxvf flashplayer10_install_linux_051508.tar.gz
cd install_flash_player_10_linux
sudo chmod +x flashplayer-installer
sudo ./flashplayer-installer
```

I doubt it :) Just followed the procedures from the [link]("http://www.cyberciti.biz/tips/linux-install-flash-player-10.html") posted by the OP.

---

### Post by gandaran on 2008-07-08
if you find it hard to run the installer, do it the easy way, right click the package, extract the contents to desktop and just drag the 'flashplayer.so' file to the hidden home .mozilla/plugins folder.
if there's no plugins folder in .mozilla, just make one.

---

### Post by aktiwers on 2008-07-08
> **iaculallad said:**
> I doubt it :) Just followed the procedures from the [link]("http://www.cyberciti.biz/tips/linux-install-flash-player-10.html") posted by the OP.

Oh I see.. sorry about that ;)

---

### Post by highlyevolved on 2008-07-08
Thanks guys - got it to work.

In case it doesn't run well, what's the easiest way of removing?

cheers

---

### Post by gandaran on 2008-07-08
just delete flashplayer.so file!

---

