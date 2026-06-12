---
title: "[shell script] Clipboard"
date: 2005-08-04
forum: Programming Talk
---

### Post by Ninnghizidha on 2005-08-04
Good morning! 

I got a java-program, that outputs an URI. I'd like to copy that string into the Clipboard (Best) OR open a firefox-Window to this URI OR  show this URI in Zenity. ... but i got no idea how to do that ... 

```
user@Madiel:~$ java -jar PicUploader.jar foto.png
uploaded file: foto.png to url: http://666kb.com/i/10nedtgytt7gg.png

user@Madiel:~$

```

Can someone help me, please - any help is appreciated!  :) 

Ninnghizidha.

---

### Post by Phrawm48 on 2008-01-17
Did you ever find out how to do this?

If not, take a look at *xclip*...

Cheers & hope this helps,
Ric
SFO

---

### Post by naugiedoggie on 2008-01-20
> **Ninnghizidha said:**
> Good morning! 

I got a java-program, that outputs an URI. I'd like to copy that string into the Clipboard (Best) OR open a firefox-Window to this URI OR  show this URI in Zenity. ... but i got no idea how to do that ... 

```
user@Madiel:~$ java -jar PicUploader.jar foto.png
uploaded file: foto.png to url: http://666kb.com/i/10nedtgytt7gg.png

user@Madiel:~$

```

Can someone help me, please - any help is appreciated!  :) 

Ninnghizidha.

Hello,

See:

[Clipboard API]("http://java.sun.com/javase/6/docs/api/java/awt/datatransfer/Clipboard.html")
[The clipboard in use]("http://www.javapractices.com/topic/TopicAction.do?Id=82")

Thanks.

mp

---

