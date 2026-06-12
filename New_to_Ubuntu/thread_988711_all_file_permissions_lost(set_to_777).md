---
title: "all file permissions lost(set to 777)"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by boblemur on 2008-11-20
hey all, i recently upgraded my ubuntu and now all of my file permissions have be lost.

when i run ```
ls -la /
```

i have drwxrwxrwx for all the folders...

i have taken the following action so far:
```

cd /
chmod go-w -R * 
chmod go-rwx -R /home/nick/*

```

also: my ownership + group ownership has not changed. is there anything else i need to worry about??

any help is much appreciated, thanks in advance

---

### Post by RealPSL on 2008-11-23
Based on reading the man pages for ```
dpkg-reconfigure -all
``` you would think that would solve this problem but I have no supporting evidence that it will. There are also a couple of entries in brainstorm about the lack of a tool to address this exact problem. Most solutions I have come across involve reinstalling. Note that the man pages also say that dpkg-reconfigure --all will run for a very long time so be prepared if you decide to go that route. Again I have no supporting evidence that it will work.

---

