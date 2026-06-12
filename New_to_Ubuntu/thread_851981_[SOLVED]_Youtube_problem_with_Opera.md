---
title: "[SOLVED] Youtube problem with Opera"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Vossibear on 2008-07-07
Hi @all

I've got a problem with Opera ... I can't open any video in youtube. With Firefox it works very well, but Opera shows any videowindow (screenshot)

[IMG]http://img300.imageshack.us/img300/808/youtubebw0.png[/IMG]

I've got the shockwave plugins for Opera :

[IMG]http://img300.imageshack.us/img300/4103/pluginub9.png[/IMG]

[http://img300.imageshack.us/my.php?image=pluginns0.png]("http://img300.imageshack.us/my.php?image=pluginns0.png")


Thx

---

### Post by acidsolution on 2008-07-07
Can You specify the version of opera 
Opera 9.5 works perfectly with new flash version while opera (9.23 or 9.22) i can't actually rememberthe version, doesnot work well with latest flash version.

---

### Post by Vossibear on 2008-07-07
I had the version 9.5 ... actually everything was fine, but now with the 9.51 there is the problem I described in top of the thread.

---

### Post by mykaDragonBlue on 2008-07-08
I just fixed this myself.It seems to be the duplication of the plugin thats the problem.

I just renamed the 'flashplugin-alternative' link as a temporary measure.

like so (in terminal):
```

cd /usr/lib/mozilla/plugins
sudo mv flashplugin-alternative.so flashplugin-alternative.so.2

```

---

### Post by Vossibear on 2008-07-08
I've done it, but there is still the problem.

There is only one flashplugin now, but the videowindow doesn't open like before

---

### Post by zenzizenzizenzic on 2008-07-08
After comparing your plugins page to mine (I'm also using 9.51), I see that I have libflashplayer.so as well in the /usr/lib/opera/plugins/ directory, so you might try copying the plugin to there from /usr/lib/flashplugin-nonfree/ and see if that fixes the problem.

---

### Post by Vossibear on 2008-07-08
Thank you it is fixed :)

---

