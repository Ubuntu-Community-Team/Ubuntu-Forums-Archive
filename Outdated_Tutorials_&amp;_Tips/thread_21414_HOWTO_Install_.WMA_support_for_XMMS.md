---
title: "HOWTO: Install .WMA support for XMMS"
date: 2005-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Strid on 2005-03-22
HOWTO get .WMA support for XMMS?
-----------------------------------------------------------

XMMS is not able to play .WMA files by default. If you want .WMA support, you need to install a plugin. This is a HOWTO on how to do that.

We're assuming, that you've already installed XMMS. If you need help on installing XMMS, have a look at [www.ubuntuguide.org](www.ubuntuguide.org).
Now, lets get .WMA support for XMMS. First, get the xmms-dev package. Then download this file, 

[http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.tar.bz2](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.tar.bz2)  .

Unpack the downloaded file, make and install it.


These are the commands you should give in the terminal. 
```
$ sudo apt-get install xmms-dev

 ...
 (go to the directory where you placed the file you've just downloaded)
 ...

$ tar -xjf xmms-wma-1.0.4.tar.bz2
$ cd xmms-wma-1.0.4
$ make
$ sudo make install
```

If everything goes well, XMMS should be able to play .WMA files now.


/Anders Christensen

---

### Post by bored2k on 2005-03-22
[QUOTE=Strid]HOWTO get .WMA support for XMMS?
-----------------------------------------------------------

XMMS is not able to play .WMA files by default. If you want .WMA support, you need to install a plugin. This is a HOWTO on how to do that.

We're assuming, that you've already installed XMMS. If you need help on installing XMMS, have a look at [www.ubuntuguide.org](www.ubuntuguide.org).
Now, lets get .WMA support for XMMS. First, get the xmms-dev package. Then download this file, 

[http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.tar.bz2](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.tar.bz2)  .

Unpack the downloaded file, make and install it.


These are the commands you should give in the terminal. 
```
$ sudo apt-get install xmms-dev

 ...
 (go to the directory where you placed the file you've just downloaded)
 ...

$ tar -xjf xmms-wma-1.0.4.tar.bz2
$ cd xmms-wma-1.0.4
$ make
$ sudo make install
```

If everything goes well, XMMS should be able to play .WMA files now.


/Anders Christensen[/QUOTE]
 This is a very very newcomer guide ^_^ .

I still don't get it .
21st Century --> XMMS .

That will most likely work on beep-media-player .

---

### Post by Bomper on 2005-04-11
bmp-wma ([http://bmp-plugins.berlios.de/](http://bmp-plugins.berlios.de/)) -  A WMA decoder --- Originally based on xmms-wma ([http://mcmcc.bat.ru/xmms-wma/)](http://mcmcc.bat.ru/xmms-wma/)), with lots of improvements

beep-media-player -->  21st Century --> Thank you  XMMS --> 20st Century

---

### Post by kuleali on 2005-04-12
Nice, :) ! It worked

---

### Post by karmah on 2005-06-22
doesnt work for me :O !!!
Everything worked fine until i tried to open a .wma file..xmms doesn't wanna play it !  :-?   :neutral: 
somebody help? :/

Edit: made thread here instead [http://ubuntuforums.org/showthread.php?p=224845#post224845](http://ubuntuforums.org/showthread.php?p=224845#post224845)

---

### Post by tomwell on 2005-11-22
I try this but i get error 1 when i do the make command and then error 2 when i do make install command...

Anyone know whats happening?? It would be really cool if i could play wma in xmms....

Peace 

Tom

---

### Post by AlexMartinius on 2005-12-15
The link in the first post doesn't work anymore. Version 1.0.5 is the newest release, you can find it here: [http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/)

Installing with make and make install didn't work here, so I converted the rpm ([http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm)) to deb using alien and installed the deb with:
```

$ sudo dpkg -i xmms-wma_1.0.5-2_i386.deb

```
And it works. :)

---

### Post by cvmostert on 2006-01-30
[QUOTE=AlexMartinius]The link in the first post doesn't work anymore. Version 1.0.5 is the newest release, you can find it here: [http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/)

Installing with make and make install didn't work here, so I converted the rpm ([http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5-1.i386.rpm)) to deb using alien and installed the deb with:
```

$ sudo dpkg -i xmms-wma_1.0.5-2_i386.deb

```
And it works. :)[/QUOTE]


i tried this but at first attempt xmms did not want to pay a wma file... 

i will play around with it...

---

### Post by cvmostert on 2006-01-30
Ok, great... it works... probably needed to be restarted twice?

bottom line -> it works... wierd that it is not installed with w32codecs...

EDIT: probably because xmms is not a default app..

---

### Post by Cris(c) on 2007-12-03
It totally worked for me. Instead of xmms-wma-1.0.4, I used version 1.0.5...thanks a lot!

---

### Post by wjgeorge on 2007-12-18
sudo apt-get install xmms-wma

and yes you should exit xmms BEFORE running this!

---

### Post by Strid on 2008-01-03
Yes, you'd probably be better off using the xmms-wma from the repo nowadays. :)

Good catch!

---

### Post by ItalOz on 2008-02-06
BUMP

I installed the plug-in, just now, but I can't jump to a time into the WMA file like I can do in the MP3.
If I move the slider forward it makes me jump to the next file rather them moving into the WMA time

Any idea?

---

