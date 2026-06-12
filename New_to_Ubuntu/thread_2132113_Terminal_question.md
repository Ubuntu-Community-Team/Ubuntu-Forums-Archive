---
title: "Terminal question"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by richpants on 2013-04-03
Hello,
this is stupid, but is there anyway to make bash return "you are welcome" to typing the statement "thanks" I hope that make sense, I just am wondering how it could be done.
Thanks
Rich

---

### Post by steeldriver on 2013-04-03
probably the easiest way is using a shell alias

 ```
$ alias thanks='echo "you are welcome"'
$ thanks
you are welcome
$
$ alias thanks='echo "you are welcome, $USER"'
$ thanks
you are welcome, steeldriver
```

---

### Post by richpants on 2013-04-03
Awesome,
that makes sense, and worked. Thank you 
Rich

---

### Post by Impavidus on 2013-04-04
Put it into your .bashrc or .bash_aliases to make it permanent.

---

