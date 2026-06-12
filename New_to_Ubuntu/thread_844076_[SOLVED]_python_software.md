---
title: "[SOLVED] python software"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-29
hey,

seems rather strange...I've been tryn to install coupla python based s/w

i type in 

tmp# sudo easy_install -U funkload

before i try the next step which is 
    > cd /tmp/funkload/
    python setup.py build
    sudo python setup.py install
i check if funkload is present in tmp,

tmp#ls
and its not there....

so no surprises....cd /tmp/funkload/ gives me error:funkload is not a valid file/dir


what could be wrong here?

Cheers
David

---

### Post by ghostdog74 on 2008-06-29
it will be in your python installation directory, usually in site-packages, not tmp.

---

### Post by ub007 on 2008-06-29
thanks,could u list me the dir for that particulat site-package...
it was mentioned cd /tmp/funkload/ in funkload documentation...wonder y...

---

### Post by ghostdog74 on 2008-06-29
just do a find
```

find / -iname "*funkload*" -print

```

---

### Post by ub007 on 2008-06-29
that helps,funkload was indeed found in the site-packages!Thanks mate

---

