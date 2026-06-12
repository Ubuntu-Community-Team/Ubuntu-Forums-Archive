---
title: "AOC 15&quot; CRT black monitor"
date: 2009-09-13
forum: Philippine Team
---

### Post by frustphil on 2009-09-13
sino po nagmamay-ari ng ganitong monitor sa inyo? nagkaroon ako ng prob sa screen resolution ko eh at gusto iedit ang xorg.conf. problema d ko alam ang monitor name, HorizSync, VertRefresh kc nawala ang manual nito tagal na kac. kung pwede sana malaman ang settings ng xorg.conf if meron kau... =)

---

### Post by aljoriz on 2009-09-13
to edit screen resolution.  run the following in the command (under the assumption that the video card drivers is NVIDIA)

Dehins kasama yung '$' pagsulat sa terminal ah.
@Terminal:
$ gksudo nvidia-settings
(enter password)

Then change the resolution and make sure to SAVE to XCONFIG.  Para pag start ng pc mo nasa desired resolution yan.

---

### Post by frustphil on 2009-09-13
intel sakin eh.. pano ba?=)

---

### Post by ache109 on 2009-09-14
sir pagkakaalam ko eh ganito:

sa terminal:

sudo gedit etc/x11/xorg.conf

lalabas po ung gedit na naglalaman ng xorg config tapos po i-check nyo dun sa "screen" section kung naka set sa tama ung resolution nyo. 

post ule ako if nakabalik na ako sa ubuntu... :D

@add.

sir would you mind post your xorg.config file?

---

### Post by frustphil on 2009-09-14
> **ache109 said:**
> sir pagkakaalam ko eh ganito:

sa terminal:

sudo gedit etc/x11/xorg.conf

lalabas po ung gedit na naglalaman ng xorg config tapos po i-check nyo dun sa "screen" section kung naka set sa tama ung resolution nyo. 

post ule ako if nakabalik na ako sa ubuntu... :D

@add.

sir would you mind post your xorg.config file?

Sadly, walang xorg.conf na ngaun by defualt I think. So I have to create it myself... :(

---

### Post by ache109 on 2009-09-14
> **frustphil said:**
> Sadly, walang xorg.conf na ngaun by defualt I think. So I have to create it myself... :(
sir try mo ung liNK na ito:
[http://www.cyberciti.biz/tips/create-a-xorgconf-file.html](http://www.cyberciti.biz/tips/create-a-xorgconf-file.html)

maybe that will help..:D

---

