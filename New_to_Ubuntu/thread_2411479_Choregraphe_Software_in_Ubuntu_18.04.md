---
title: "Choregraphe Software in Ubuntu 18.04"
date: 2019-01-30
forum: New to Ubuntu
---

### Post by mmalware on 2019-01-30
Hello everyone , 
i'm trying to install the choregraphe software for robotics purposes .
I downloaded the tarball from the official website And then :

tar xzvf  choregraphe-suite-2.5.10.7-linux64.tar.gz

cd  choregraphe-suite-2.5.10.7-linux64

sudo ./choregraphe

And after that i'm getting this error :

/home/yassine/Téléchargements/choregraphe-suite-2.5.10.7-linux64/bin/choregraphe-bin: /home/yassine/Téléchargements/choregraphe-suite-2.5.10.7-linux64/bin/../lib/../lib/../lib/libz.so.1: version `ZLIB_1.2.9' not found (required by /usr/lib/x86_64-linux-gnu/libpng16.so.16)


How can i fix it please ?Thank you

---

### Post by wildmanne39 on 2019-01-30
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by davidbaumert on 2019-04-18
I can't vouch for backwards compatibility, but was able to get the app to launch by addressing the reported error and adding a library link:

$ sudo ln -sf /usr/lib/x86_64-linux-gnu/libz.so /opt/'Softbank Robotics'/'Choregraphe Suite 2.5'/lib/libz.so.1

---

### Post by monkeybrain20122 on 2019-04-19
Why do you run it with sudo?? Can you at least provide a download link if you want help for some software not in the standard repo?

---

