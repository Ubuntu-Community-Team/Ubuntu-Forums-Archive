---
title: "wine on 7.10"
date: 2007-11-19
forum: Philippine Team
---

### Post by treion on 2007-11-19
i'm new to ubuntu, no knowledge but would like to try it out.installed 7.10

na-download ko na yung wine its currently in my deskstop but can't install it

sudo apt-get install wine at terminal then i get this message: "E: Couldn't find package wine"

hwat did i do wrong

---

### Post by loell on 2007-11-19
try mo munang mag update,

```
sudo apt-get update
```

then install wine again.

---

### Post by kopinux on 2007-11-19
ang galing na ng wine ngayon, isang taon na nakaraan ng huling subukan ko, ang laki ng improvement.

isang beses ko lang sinubukan tumakbo na agad yung photoshop cs, starcraft at warcraft3.

ngayon kung may magtatrabaho lang para gumana yung onlinegames...........................................

---

### Post by pinoyskull on 2007-11-20
for future reference sa mga newbies :)
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by treion on 2007-11-20
updated, wine installed,,next up starcraft installation

---

### Post by business.geek on 2007-11-20
> **treion said:**
> updated, wine installed,,next up starcraft installation

If you ever need help, I can help, I got starcraft running on my system.

cheers!

---

### Post by treion on 2007-11-21
@b.geek: thanks bro. i got it installed now. pwede ba i-network ito with a windowsxp pc? 
basic problem ko.: i cn't connect tis ubuntu pc in the network i have here at home. i can see the other pc and get files from its shared folder but this pc does not appear in the network, which means i can't play network game with other pc

---

### Post by treion on 2007-11-22
> **business.geek said:**
> If you ever need help, I can help, I got starcraft running on my system.

cheers!


bro. i installed samba now starcraft won't work . treid to re-install but nothing happens just blank screen

---

### Post by kopinux on 2007-11-22
kung mag re-reinstall ka baka pwede uninstall mo muna wine tapos burahin mo muna yung .wine directory sa home folder mo, hidden yun.

---

### Post by treion on 2007-11-22
pano uninstall ang wine and delete the hidden folders

---

### Post by loell on 2007-11-22
to uninstall wine. type the command

```
sudo apt-get remove wine
```

to erase / delete the **.wine** directory , type

```
rm -r .wine
```

---

### Post by kopinux on 2007-11-23
tapos install mo ulit wine, parang brand new na!.

---

### Post by roychoco on 2007-11-25
to:  pinoyskull

thank you pre.  na update ko na yung wine ko.  maganda na yung graphics sa civ4

---

