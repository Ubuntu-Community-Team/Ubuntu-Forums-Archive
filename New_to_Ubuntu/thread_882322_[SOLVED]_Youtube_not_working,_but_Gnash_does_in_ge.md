---
title: "[SOLVED] Youtube not working, but Gnash does in general"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by ghostypaste on 2008-08-06
I installed Gnash on Hardy 64-bit. It seems to work. Sites like [www.homestarrunner.com](www.homestarrunner.com) seem to work for the most part, although some things are messed up like the text on the toons page. Sites like youtube.com and others that stream video don't work. I can right-click on the flash movie, and I get the normal Gnash right-click menu - but the video doesn't load, it just stays white. I don't get a message telling me to install Flash. Maybe there are just some codecs missing? I dunno HELP.





thanks.

---

### Post by mevets on 2008-08-06
Is there a reason you must use gnash instead of adobe's flash plugin? Gnash is GNU's implementation of flash. They are dont have access to all the information adobe does, so naturally it isnt as good.

---

### Post by ghostypaste on 2008-08-06
My understanding is that there isn't a version of flash provided by Adobe for amd64. I'd use it if there is, though.

---

### Post by mevets on 2008-08-06
Apparently not, but there are ways of getting adobe's version to work regardless. Link below describes how.

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&#Flash](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&#Flash)

---

### Post by ghostypaste on 2008-08-06
I'll try this out and report back. Thanks.

---

### Post by Crafty Kisses on 2008-08-06
> **ghostypaste said:**
> I'll try this out and report back. Thanks.

Gnash is a good alternative to Adobe's Flash, but if Gnash isn't working I'd suggest you trying Adobe's Flash.

---

### Post by wolfen69 on 2008-08-06
make sure to remove gnash before installing flash.

---

### Post by ghostypaste on 2008-08-06
So, this line doesn't work:

/usr/local/firefox32/plugins/

In fact, I don't have a firefox32 directory in that location. I searched / for "firefox" and came up with some results, but none of them was a firefox32 directory. I found /usr/lib/firefox/plugins, but I don't have any indication that it would work with a 32-bit plugin. In fact, when I run ./flashplayer-installer it says that the amd-64 architecture is not supported.

Any idea what to do about this?

---

### Post by pi.boy.travis on 2008-08-06
What browser are you using?

---

### Post by ghostypaste on 2008-08-08
It's Firefox 3.0.1
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

---

### Post by st33med on 2008-08-08
Adobe flash will work on x64 hardware. Just install:
```
sudo apt-get install flashplugin-nonfree
```

---

