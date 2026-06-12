---
title: "need a guide for .tar.gz or &amp; .tar.bz2"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by jonaphant on 2008-04-30
hi! i'm new to ubuntu and linux and i love it a lot but i have this problem, i don't know how to unzip and install programs and archives that come in .tar.gz and .tar.bz2, could someone please help me posting a detailed guide on how to do it?

thanks in advance:)

---

### Post by aheckler on 2008-04-30
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Of course, you should check to see if the program you want to install is available in the Add/Remove Programs application first.

---

### Post by Thelasko on 2008-04-30
The reason there isn't a guide is because we want to encourage installations from the repositories. (Applications>add/remove software).  What application are you trying to install?

---

### Post by pedro_orange on 2008-04-30
Tarballs are just zipped files.
You can right-click it and unpack the file that way.

If you want to do it from the command line....

For .tar.gz:

```
tar -zxvf filename.extension
```

For .tar.bz2:

```
tar -jxvf filename.extension
```

Still....I'd use synaptic/apt-get if I were you.

---

### Post by jonaphant on 2008-04-30
thank you very much to all of you, that's right maybe i should check first synaptic or add/remove programs.

thanks for the help:)

---

