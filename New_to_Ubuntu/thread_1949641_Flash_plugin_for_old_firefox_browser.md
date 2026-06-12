---
title: "Flash plugin for old firefox browser"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by Euboon2 on 2012-03-30
For some reasons, I would like to have an old browser (in addition to chromium which i use for normal web surfing). I installed the old firefox browser using the link from dennyhalim's minimal desktop page. But flash player is not working in that firefox.

How do I link my current flash player to that firefox installed into /opt? Or are there more steps I need to take to get flash to work? Somehow the pluginreg.dat is different for my current firefox settings compared to the old firefox for a new user I created specifically to use the old browswer.

---

### Post by idoitprone on 2012-03-30
> **Euboon2 said:**
> For some reasons, I would like to have an old browser (in addition to chromium which i use for normal web surfing). I installed the old firefox browser using the link from dennyhalim's minimal desktop page. But flash player is not working in that firefox.

How do I link my current flash player to that firefox installed into /opt? Or are there more steps I need to take to get flash to work? Somehow the pluginreg.dat is different for my current firefox settings compared to the old firefox for a new user I created specifically to use the old browswer.


what you have to do is symlink flashplugin to the proper folder

this thread may help

[http://support.mozilla.org/en-US/questions/724490](http://support.mozilla.org/en-US/questions/724490)

to see if firefox see the plugin

type 
```
about:plugins
```
in firefox url bar
if flash is listed, then it is installed

---

### Post by Euboon2 on 2012-03-30
Thanks, but it isn't working.

"about:plugins" shows that nothing is enabled. The firefox browser version 1.5 is for 32bit while I use amd64 OS. I tried copying flashplugin directly into /usr/lib/mozilla/plugins/ but youtube still don't can't play a flash video.

---

### Post by d4m1r on 2012-03-30
Google search "flash aid ubuntu firefox" and install the plugin from the Mozilla plugin site.

---

### Post by Euboon2 on 2012-03-30
That link don't work for firefox 1.5, which probably doesn't recognize the file extension. I tried for a number of hours already, but just can't seem to get flash to work in that firefox version :confused:. I'll just give up and get back to work. Nevertheless, thanks a lot.

---

### Post by idoitprone on 2012-03-30
> **Euboon2 said:**
> Thanks, but it isn't working.

"about:plugins" shows that nothing is enabled. The firefox browser version 1.5 is for 32bit while I use amd64 OS. I tried copying flashplugin directly into /usr/lib/mozilla/plugins/ but youtube still don't can't play a flash video.


yeaaa about that. you cannot use 64 bit plugins for 32 bit browser, and you copied it to the wrong location.....

you have to copy it to i believe ```
/opt/usr/lib/mozilla/plugins
```if it exist. 

if you give up, you can put it on ```
~/.mozilla/plugin/
```~/ - means your home dir.

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)
download 32 bit flash

if i were you, i wouldnt use firefox 1.5, its too dawm old. try another small broswer like midori, which will cream firefox 1.5 in benchmarks.

---

