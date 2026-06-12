---
title: "[SOLVED] Installing a Bin file"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by hufferd on 2008-08-30
I was going [Here]("http://www.real.com/linux/?pageid=unagi.13578321.wrapper&pageregion=footer&src=linux&pcode=rn&opage=linux") to download the helix real player ......  and It seems to be a bin file that downloads I am not sure once I download it what to do from there I would love any help thanks :)

---

### Post by gmxgeek on 2008-08-30
open a terminal and cd to the folder that contains the bin file, then type
```

chmod +x filename.bin
sh ./filename.bin

```

that should run it

---

### Post by Elfy on 2008-08-30
assuming it has donwloaded to the desktop, 

```
cd Desktop
chmod a+x filename.bin
sudo ./filename.bin
```
should do it.

---

### Post by Tom--d on 2008-08-30
Make the file executable (right click > Permissions > Tick 'Make executable (something liek that))

and in terminal, do:
```
cd /home/username/path/to/file/
```
```
 sudo ./filename.bin
```


Dang. Was too late!

---

### Post by billgoldberg on 2008-08-30
Here you go buddy, this will help you.

[http://linuxowns.wordpress.com/2008/04/15/real-player-11/](http://linuxowns.wordpress.com/2008/04/15/real-player-11/)

You can do it all doing the GUI, there isn't a need to use the terminal for this

---

### Post by hufferd on 2008-08-30
> **billgoldberg said:**
> Here you go buddy, this will help you.

[http://linuxowns.wordpress.com/2008/04/15/real-player-11/](http://linuxowns.wordpress.com/2008/04/15/real-player-11/)

You can do it all doing the GUI, there isn't a need to use the terminal for this

THanks everyone for the info

---

