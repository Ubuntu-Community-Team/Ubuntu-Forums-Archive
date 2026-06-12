---
title: "shell script for backups"
date: 2005-11-28
forum: Programming Talk
---

### Post by Houman on 2005-11-28
Hi there;
I do some small coding for a project, and I would like to be able to quickly backup everything, what i have so far is this: (i know almost nothing of shell scripting, so please forgive me)
```

#! /bin/bash
cd prog1
make clean
cd ..
save_name=prog1`date +%F`.tar.gz
echo $save_name
tar -zcvf $save_name prog1

```

so this way i get a compressed file which has the date in it, but now the problem is that i would like to send this file to my gmail account automatically and i dont have any idea how to do that;

I found out that Evolution lets you compose an email with an attachment, but you have to "click" the send thing, so thats out of questions, i did some googling and i found a program called "mutt" which is in ubuntu repop too, this program can automatically send mime attachments, BUT it needs sendmail to be installed which is not the case in breezy, so does anyone know of anyway to send an attachment automatically?

regards;
Houman

---

### Post by amohanty on 2005-11-28
afaik you will need the following at the very least to do this:

1. Mail server: postfix, qmail or sendmail 
    If you dont have a static ip this can get tricky, fortunately the forums are full of help on this.
2. the mail program or something similar to it. Again search the forums for help. A decent discussion of using mail is here:
[http://ubuntuforums.org/showthread.php?t=91366&highlight=mail+command+line](http://ubuntuforums.org/showthread.php?t=91366&highlight=mail+command+line)

HTH
AM

---

### Post by Houman on 2005-11-28
thank you amohanty for your response;

It looks like too much trouble :???:  so ill just add this to my miniscript:
```

evolution "mailto:?to=address@gmail.com&attachment=/home/houman/t.txt"

```
I have to press "send" and i cant have it run automatically (since obviously it wont work if im not at the machine) but still beats messing with qmail and postfix and all that stuff :) 

anyways thank you for your response ;

Houman

---

