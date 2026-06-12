---
title: "can't figure out quodlibet"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by chucky chuckaluck on 2008-06-19
right after installing it from synaptic, i chose 'add file', clicked on play and got *gstreamer encountered a general resource error*. i can't even figure out how to use it. the quodlibet site's instructions amount to what appears to a frustrated new user as bragging about tagging.

---

### Post by cozmicharlie on 2008-06-19
Have you installed all the music codecs (mainly the gstreamer plugins)?  

Basic use menu>music then you can add a file a folder or browse your library.  To set your library up go to menu>music>preference> go to the library tab and set up the folder that contains the library.  You can also add plug ins (if you installed them) in preferences.

---

### Post by chucky chuckaluck on 2008-06-20
i had installed the ubuntu-restricted-extras package, but in another thread, some suggested reinstalling the libraries for gstreamer. i didn't have much hope in that idea, but i did it anyway. good thing i didn't listen to my instincts (maybe that's why mrs. chuckaluck doesn't either). so now, it appears to work. thanks for the response. 


for reinstalling the gstreamer libraries:

```
sudo aptitude reinstall gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x
```

---

### Post by chucky chuckaluck on 2008-06-20
holy crap, batman! when you get this thing working, it's a nice piece of work.

:guitar:

---

