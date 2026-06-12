---
title: "google-earth 64 bit"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-12-13
I can't find the 64-bit .deb in [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html) any more. There is only an i386 package. Any idea what happens?

Thanks

---

### Post by vasa1 on 2014-12-13
See if this post helps: [http://ubuntuforums.org/showthread.php?t=2248987&p=13147362#post13147362](http://ubuntuforums.org/showthread.php?t=2248987&p=13147362#post13147362)

---

### Post by monkeybrain20122 on 2014-12-13
Strange. In my firefox (Ubuntu 14.04) the options "please select download packages" don't show up, when clicked it just asks to download the i386.deb . But the choices show up in Chrome and in Firefox (same version) in another Ubuntu install (also 14.04) Maybe because of my Firefox preferences..

---

### Post by CRYy0OKmKpJgc on 2014-12-13
[https://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb](https://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb)

---

### Post by monkeybrain20122 on 2014-12-16
I can get the amd64.deb now. I am just wondering why the list of options doesn't show up in Firefox (it does on another machine also running Trusty with FF34)

---

### Post by mc4man on 2014-12-16
If javascript is disabled then you won't get the options. You may have done so thru an addon or in about:config or some other reason it's not active

---

### Post by monkeybrain20122 on 2014-12-17
I checked about:config and javascript is enabled. I have no problem accessing interactive websites like gmail so I suppose it is indeed enabled. I don't have noscriprt or similar addon either.

---

### Post by monkeybrain20122 on 2014-12-30
Couldn't figured out what's wrong. Started a new profile, copied session.js and the plugins folder over to the new .mozilla folder,  imported all the bookmarks then nuked the old profile. It is working normally in FF now. Took only a few minutes, don't bother trouble shooting it anymore.

---

### Post by monkeybrain20122 on 2015-01-30
Mystery solved! Turns out I have added a general.platform.override string in about:config  to test  unity3d player (via pipelight) on a site and forgot to reset it and goggle got spoofted. :)

---

