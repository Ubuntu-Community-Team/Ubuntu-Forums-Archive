---
title: "HOWTO: proper codec support in xine"
date: 2004-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by stateq2 on 2004-11-30
I haven't seen this solution here, so...If xine (gxine, totem, etc) isn't playing all your files and stuff, here's how to fix it....if you've already compiled mplayer and stuff, then just skip the first step

1. get the essential codec package from [here](http://www.mplayerhq.hu/homepage/design7/dload.html#codecs) and unpack them into "/usr/local/lib/codecs".

2. make a symlink....
```

ln -s /usr/local/lib/codecs /usr/lib/win32

```

done.

---

### Post by TravisNewman on 2004-11-30
Will this work with gstreamer as well? I have xine installed, but I want to keep totem as gstreamer. I also have mplayer installed... basically, I want to keep as many options open, because some players play different files reliably, some don't. But I can't get gstreamer to play jack.

---

### Post by amoser on 2004-12-01
I have not been able to get totem-gstreamer to play anything, that is why I apt-get(ed) totem-xine, with the w32 codecs.  All works fine like that.

~Alan

---

### Post by jdodson on 2004-12-01
rember to put howto in the title.

---

### Post by easy_target on 2004-12-01
[QUOTE=amoser]I have not been able to get totem-gstreamer to play anything, that is why I apt-get(ed) totem-xine, with the w32 codecs.  All works fine like that.

~Alan[/QUOTE]

I also heard that installing totem xine removes the ubuntu desktop metapackage. What are the consequences of that? I noticed that when I installed the xine version I couldn't customize my desktop anymore. Is that supposed to be that way? 

Please advise

Thanks!!! 8-[

---

### Post by TravisNewman on 2004-12-01
[QUOTE=easy_target]I also heard that installing totem xine removes the ubuntu desktop metapackage. What are the consequences of that? I noticed that when I installed the xine version I couldn't customize my desktop anymore. Is that supposed to be that way? 

Please advise

Thanks!!! 8-[[/QUOTE]
 No that shouldn't have caused that... ubuntu-desktop is a meta package that depends on all the default packages. If you want to remove a default package, ubuntu-desktop gets removed. Basically, if ubuntu-desktop changes at any point to depend on different packages and not others, if you have removed it, you won't get those changes. Not a huge deal unless you're in hoary or plan on updating to hoary, from what I've seen.

---

### Post by easy_target on 2004-12-01
[QUOTE=panickedthumb]No that shouldn't have caused that... ubuntu-desktop is a meta package that depends on all the default packages. If you want to remove a default package, ubuntu-desktop gets removed. Basically, if ubuntu-desktop changes at any point to depend on different packages and not others, if you have removed it, you won't get those changes. Not a huge deal unless you're in hoary or plan on updating to hoary, from what I've seen.[/QUOTE]
 Thanks for the super fast reply. I istalled totem xine but when I try to play videos there's  no sound! I don't know what happens but I can only hear (eventually) some hints of sound. What should I do?

---

### Post by easy_target on 2004-12-03
Anyone?

---

### Post by aquarichy on 2004-12-05
This lack of sound also affects me.  I thought I broke something :D

---

### Post by aquarichy on 2004-12-05
The solution described [here](http://www.ubuntuforums.org/showthread.php?p=29099&posted=1#post29099) fixed me :)

---

