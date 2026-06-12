---
title: "problem in dpkg configure"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by Mythili Vishalini A on 2012-01-10
hey guys,
i was installing some s/w in ubuntu through terminal. when i tried to install the 3rd s/w, it said 
"administrator directory cannot be unlocked, because it is used by another process".
so i killed the **dpkg** process forcefully and performed
[B]sudo dpkg --configure -a.

[/B]i got the following output,

dpkg: too many errors, stopping
Errors were encountered while processing:
 man-db
 libc6:i386
 libsm6:i386
 libpng12-0:i386
 libpixman-1-0:i386
 libxcursor1:i386
 libstdc++6:i386
 libglib2.0-0:i386
 libasyncns0:i386
 libxt6:i386
 libwrap0:i386
 libkrb5-3:i386
 libxau6:i386
 libxdmcp6:i386
 libfreetype6:i386
 libxcb-shm0:i386
 libssl1.0.0:i386
 flashplugin-downloader:i386
 libdbus-1-3:i386
 libflac8:i386
 libffi6:i386
 libcairo2:i386
 libgcrypt11:i386
 libxinerama1:i386
 libuuid1:i386
 libtasn1-3:i386
 libjpeg62:i386
 libgssapi-krb5-2:i386
 nspluginviewer:i386
 libgpg-error0:i386
 libsamplerate0:i386
 libgdk-pixbuf2.0-0:i386
 libk5crypto3:i386
 libfontconfig1:i386
 libxext6:i386
 libogg0:i386
 libxrender1:i386
 libthai0:i386
 libgtk2.0-0:i386
 zlib1g:i386
 libxrandr2:i386
 libxcb1:i386
 libgcc1:i386
 libxcomposite1:i386
 libasound2:i386
 libasound2-plugins:i386
 libsqlite3-0:i386
 libcups2:i386
 libnspr4:i386
 libkeyutils1:i386
 libvorbisenc2:i386
Processing was halted because there were too many errors.

Is the error because dpkg crashed? how to recover it? how to install s/w after this?

thanks in advance

---

### Post by jerrrys on 2012-01-11
"Used by another process" usually just means that you have more than one package manager open and need to close the other(s).

---

### Post by cortman on 2012-01-11
```

ps -ef | grep apt
ps -ef | grep dpkg
```

will show you the package handling processes to kill. Stop them with

```
kill -9 pid
```

---

