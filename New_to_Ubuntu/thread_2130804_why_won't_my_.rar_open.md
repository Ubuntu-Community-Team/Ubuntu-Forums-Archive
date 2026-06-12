---
title: "why won't my .rar open?"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by XenostheBrony on 2013-03-30
I downloaded a torrent of something with Ktorrent and it's finished. I couldn't open it before so I looked up what to do and I did the sudo apt-get install unrar in terminal so I could extract my files and I had tried but whenever I do I get an error saying "Failed to locate program unrar in PATH". What do I do?

---

### Post by carl4926 on 2013-03-30
If right click doesn't offer you > extract here

You may need to install unrar

---

### Post by sudodus on 2013-03-30
```
sudo apt-get purge unrar
``` should uninstall unrar
```
sudo apt-get install unrar
``` should install unrar, and afterwards when you run
```
which unrar
```
the system should respond
```
/usr/bin/unrar
```
which should be found by the system.

Try again, and post the output of those commands! I suggest you should start by purging unrar to start from the beginning.

---

