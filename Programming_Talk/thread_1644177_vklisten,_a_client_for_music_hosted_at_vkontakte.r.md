---
title: "vklisten, a client for music hosted at vkontakte.ru"
date: 2010-12-12
forum: Programming Talk
---

### Post by costi_ on 2010-12-12
there is a russian social networking site where users  can upload music, vkontakte.ru
this is where Mulve got its songs...

i wrote a client for linux:  [http://code.google.com/p/vklisten/]("http://www.ubuntu-forum.de/index.php?page=ExternalLink&url=http%3A%2F%2Fcode.google.com%2Fp%2Fvklisten%2F") (deb packages avaibalble...)

it works by building a playlist out of the results and opening it.

```
$ vklisten
usage: vklisten <query>
$ vklisten music instructor hymn
got page #1 (Ctrl-C to break)
got page #2 (Ctrl-C to break)
got page #3 (Ctrl-C to break)
got page #4 (Ctrl-C to break)
got page #5 (Ctrl-C to break)
got page #6 (Ctrl-C to break)
got page #7 (Ctrl-C to break)
got page #8 (Ctrl-C to break)
got page #9 (Ctrl-C to break)
got page #10 (Ctrl-C to break)
opening: /tmp/junk_Te2Ngi music instructor hymn.m3u
$ cat "/tmp/junk_Te2Ngi music instructor hymn.m3u"
#EXTM3U
#EXTINF:303,Music Instructor - Hymn
http://cs4235.vkontakte.ru/u29220995/audio/9884c3b3edc2.mp3
#EXTINF:233,music instructor - hymn
http://cs4512.vkontakte.ru/u34466517/audio/5f060eaa697c.mp3
#EXTINF:320,Music Instructor - Hymn (Go Down Mix)
http://cs5006.vkontakte.ru/u15982768/audio/3dfd75ed3730.mp3
#EXTINF:234,Music Instructor - Hymn (Single Edit)
http://cs1248.vkontakte.ru/u6279376/audio/282c619afa78.mp3
#EXTINF:234,Music Instructor - Hymn (Single Edit)
http://cs1445.vkontakte.ru/u4428372/audio/ec1719834628.mp3
#EXTINF:303,Music Instructor - Hymn
http://cs1099.vkontakte.ru/u559770/audio/02a60de93fc0.mp3
#EXTINF:236,Music Instructor - Hymn (Single Edit)
http://cs4112.vkontakte.ru/u3167926/audio/09352661a762.mp3
#EXTINF:303,Music Instructor - Hymn
http://cs4759.vkontakte.ru/u7848095/audio/251f33b053c3.mp3
#EXTINF:236,Music Instructor - Hymn (Single Edit)
http://cs5006.vkontakte.ru/u4777568/audio/eb1aab3a0761.mp3
<snip>
```
what do you think?

---

### Post by poupougnac on 2011-05-01
Nice script.
However it doesn't work. I hardly know if it's because the account needs to be changed or not. Unfortunately, we need to be invited to create an account on Vkontakte... I don't know any person which have an account...  :-|

```
solve the captcha to register at vkontakte.ru
Traceback (most recent call last):
  File "/usr/bin/vklisten", line 34, in <module>
    val = vk.register(ask_captcha)
  File "/usr/share/pyshared/vkontakte/vkontakte.py", line 127, in register
    captcha_sid = resp['captcha_sid']
KeyError: 'captcha_sid'

```

---

