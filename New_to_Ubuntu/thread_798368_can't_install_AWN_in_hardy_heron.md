---
title: "can't install AWN in hardy heron"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by littleasian on 2008-05-18
im trying to install AWN for hardy

im following the instruction here:  [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

i've added the pacakages, but when i go into the terminal to install (via sudo apt-get install awn-manager-trunk awn-extras-applets-trunk), i get an error message saying " dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. )

what does this mean?  how can i fix this and install AWN?

---

### Post by forestpixie on 2008-05-18
You need to run the command, it assumes that you were root so you need to add sudo to the command

```
sudo dpkg --configure -a
```

---

