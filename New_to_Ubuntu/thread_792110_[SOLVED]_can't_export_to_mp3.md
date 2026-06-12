---
title: "[SOLVED] can't export to mp3"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by DarinB on 2008-05-12
i am using audacity in hardy
want to convert ogg to mp3,,,hit export get error
audacity needs the file /usr/lib/libmp3lame.so.0
i click ok then can't export mp3. 
what do i do????

---

### Post by sdowney717 on 2008-05-12
have you tried convertIT?
[http://www.sciallo.net/ConvertIT/Splash.html](http://www.sciallo.net/ConvertIT/Splash.html)

my program is in english.

[http://ubuntuforums.org/showthread.php?t=707354&highlight=convertit](http://ubuntuforums.org/showthread.php?t=707354&highlight=convertit)
someone else likes convertit

found the .deb here
[http://www.sciallo.net/modules/archivio/archivi/ConvertIT/convertit.deb](http://www.sciallo.net/modules/archivio/archivi/ConvertIT/convertit.deb)

some more info here
[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

here is a link to a lot of file conversions
[http://ubuntuforums.org/showthread.php?t=529759](http://ubuntuforums.org/showthread.php?t=529759)

---

### Post by SunnyRabbiera on 2008-05-12
you need to install the mp3 codec, you can do this easily by editing your repositories.
you do know how to use synaptic right?

---

### Post by avtolle on 2008-05-12
> **DarinB said:**
> i am using audacity in hardy
want to convert ogg to mp3,,,hit export get error
audacity needs the file /usr/lib/libmp3lame.so.0
i click ok then can't export mp3. 
what do i do????
Try installing ubuntu restricted extras from Synaptic, then try it again. I believe that installing that package will install the missing library (make sure you have all the extra ubuntu repositories enabled). HTH.

---

### Post by DarinB on 2008-05-12
i found on the forums that libmp3lame0 is included in the liblame0 package.
now i am up and running. 
thanks everybody

---

