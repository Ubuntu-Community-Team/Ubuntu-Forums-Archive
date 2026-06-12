---
title: "PHP CHESS ONLINE, how to make it free for all?"
date: 2010-08-01
forum: Programming Talk
---

### Post by frenchn00b on 2010-08-01
Hello, 

I have this code. I would like that one can play without SQL nor sending email, that it only says who played the last, and it is enough, on the page

[http://webscripts.softpedia.com/script/PHP-Clases/PHP-Chess-classes-20084.html](http://webscripts.softpedia.com/script/PHP-Clases/PHP-Chess-classes-20084.html)

---

### Post by Hellkeepa on 2010-08-01
HELLo!

I recommend you start [here](http://no.php.net/manual/en/index.php) then, also  you might want to find yourself a PHP tutorial.
However, do keep in mind that almost none of the tutorials consider security of any kind. The only one I found, was PHP.net's tutorial (which is in the manual), but that was a bit too short to be useful. So, please do everyone (yourself, your users, those that view your site, and *everyone* else online) the favour of making sure your app is secure before releasing it on the internet.

Happy codin'!

---

### Post by iMisspell on 2010-08-01
> **frenchn00b said:**
> ...without SQL nor sending email...
Not looking at the code, you could probably use a text file(s) to save/store the data instead of a data-base-engine.

Being PHP is a server side language, the only way i can think to get around sending off an email would be to (auto) refresh and check if a move has been made.

Ive never look for any thing like this but, it might be easyer to find a java based chess game.

_

---

### Post by frenchn00b on 2010-08-02
> **iMisspell said:**
> Not looking at the code, you could probably use a text file(s) to save/store the data instead of a data-base-engine.

Being PHP is a server side language, the only way i can think to get around sending off an email would be to (auto) refresh and check if a move has been made.

Ive never look for any thing like this but, it might be easyer to find a java based chess game.

_

well, java is less flexible
this php code is very flexible cuz it has already the bitmaps of the chess board + soldiers

it is just to change this class.php file and adapt example.php 
which remains easy for most of u guys that code php usually.

surprinsngly no one publish such easy things cuz all coders want business and make money from their code.

Hence such easy code is not being found on internet without paying

Linux is great man, it is free, and all contribute to that.

---

### Post by frenchn00b on 2010-08-05
**

I foudn a online chess game, without passwords:
[http://webscripts.softpedia.com/script/Games/Two-Players-Chess-22872.html](http://webscripts.softpedia.com/script/Games/Two-Players-Chess-22872.html)

but it seems not to be compatible with linux iceweasel / firefox. Does it work for you? Is it only for windows XP?

---

### Post by simeon87 on 2010-08-06
> **frenchn00b said:**
> well, java is less flexible
this php code is very flexible cuz it has already the bitmaps of the chess board + soldiers

Bitmaps can be loaded in Java as well. Either way that's not an indication that PHP is more flexible than Java.

---

### Post by frenchn00b on 2010-08-06
> **simeon87 said:**
> Bitmaps can be loaded in Java as well. Either way that's not an indication that PHP is more flexible than Java.

I think that hmtl chess game is the best, it has highest comaptibility normally, well, in case php is improved ,but IE4 would be fantastic to have a code:

friend move it 
it save it into the folder
e4d5-r6d7
...
and anyone can follow and play

[http://webscripts.softpedia.com/script/Games/Two-Players-Chess-22872.html](http://webscripts.softpedia.com/script/Games/Two-Players-Chess-22872.html)

---

### Post by interval1066 on 2010-08-06
How come you want fewer features? Just sayin...

---

### Post by frenchn00b on 2010-08-07
> **interval1066 said:**
> How come you want fewer features? Just sayin...

it would be great a higher compatibility for friends:

no login

just click on link and play and no java to be installed

---

### Post by simeon87 on 2010-08-07
> **frenchn00b said:**
> it would be great a higher compatibility for friends:

no login

just click on link and play and no java to be installed

Progress has always been forward, not backward. You probably want to move towards HTML 5 which is the way forward and can also do that: a chess game in HTML without a login, etc.

---

