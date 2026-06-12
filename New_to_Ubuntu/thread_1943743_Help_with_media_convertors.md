---
title: "Help with media convertors"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by munezz on 2012-03-20
I was wondering if there are any tools that convert .ogg to mp3. I used sound convertor but it doesn't seem to be working. Any Help.................;)

---

### Post by raja.genupula on 2012-03-20
[http://superuser.com/questions/15327/how-to-convert-ogg-to-mp3](http://superuser.com/questions/15327/how-to-convert-ogg-to-mp3)

---

### Post by gordintoronto on 2012-03-20
First install the Restricted Extras for your version of Ubuntu.

---

### Post by flurospar on 2012-03-20
Get ffmpeg.

```

sudo apt-get install ffmpeg ubuntu-restricted-extras

```

Conversion then is quite easy:
```

ffmpeg -i patas_de_trapo.ogg patas_de_trapo.mp3

```

---

### Post by IWantFroyo on 2012-03-20
I support the use of ffmpeg.

---

### Post by HermanAB on 2012-03-20
sox

---

### Post by raja.genupula on 2012-03-20
> **HermanAB said:**
> sox

[http://sourceforge.net/projects/sox/files/sox/14.4.0/sox-14.4.0.tar.bz2/download](http://sourceforge.net/projects/sox/files/sox/14.4.0/sox-14.4.0.tar.bz2/download)

---

### Post by munezz on 2012-03-22
> **gordintoronto said:**
> First install the Restricted Extras for your version of Ubuntu.

I tried installing the Restricted Extras,it was working fine till 70% installation but after that it got cancelled..I tried doing it again but again the same problem occurred. Help:confused:

---

### Post by jerome1232 on 2012-03-22
> **munezz said:**
> I tried installing the Restricted Extras,it was working fine till 70% installation but after that it got cancelled..I tried doing it again but again the same problem occurred. Help:confused:

copy and paste the output of these commands so we can better understand the error. (ctrl+alt+t) to open a terminal

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

ctrl+shift+c to copy from a terminal, wrap the output in code tags by going advanced, highlighting all output and clicking the # symbol on the toolbar.

---

