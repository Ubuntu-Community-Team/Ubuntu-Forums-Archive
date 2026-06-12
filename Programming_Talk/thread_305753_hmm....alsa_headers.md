---
title: "hmm....alsa headers"
date: 2006-11-23
forum: Programming Talk
---

### Post by Absurd on 2006-11-23
So I want to start using LAMIP. I grabbed the sources I needed (input plugins, core, control, output, etc). In order to compile the alsa output, I need alsa headers (it told me so when I ./configure'd).

Which edgy package contains alsa headers? I downloaded the alsa-source and ./configure isn't satisfied.:-k

---

### Post by po0f on 2006-11-23
Absurd,

You'll need to unpack the source after you "install" it via apt-get.  [Here](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=alsa-source&version=edgy&arch=all) is a list of the files installed with [alsa-source](http://packages.ubuntu.com/edgy/sound/alsa-source), one of which is /usr/src/alsa-driver.tar.bz2 (the file you need to unpack).

---

### Post by Absurd on 2006-11-25
Ok. Where do I exactly unpack the files? 

I looked into the source and it shows 

```
#include <alsa/asoundlib.h>
#include <plug_out.h>
```

in /usr/include? Which folder do I add to /usr/include/ ?

---

### Post by kroppek on 2008-12-20
Installing libasound2-dev pack fixes problem of lack of alsa headers.

---

### Post by ceefour on 2010-11-29
> **kroppek said:**
> Installing libasound2-dev pack fixes problem of lack of alsa headers.

Thank you kroppek !

You've helped me write this blog post:

[http://qt-mobility.blogspot.com/2010/11/fatal-error-alsaasoundlibh-no-such-file.html](http://qt-mobility.blogspot.com/2010/11/fatal-error-alsaasoundlibh-no-such-file.html)

---

