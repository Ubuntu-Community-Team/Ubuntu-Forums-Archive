---
title: "need bash script login help - how to create a folder with login script"
date: 2015-06-08
forum: Programming Talk
---

### Post by sam_baker2 on 2015-06-08
hi,

In my login script, I want to create a folder ~if~ it does not exist.
Can someone post the code?

Thanks

---

### Post by Lars Noodén on 2015-06-08
You'll probably want to use [test](http://manpages.ubuntu.com/manpages/trusty/en/man1/test.1.html) and [mkdir](http://manpages.ubuntu.com/manpages/trusty/en/man1/mkdir.1.html) for that.

```

test -d /path/to/some/directory || mkdir -m 750 /path/to/some/directory

```

The || means that if the first program fails, then the second will be run.

```

true || echo running
false || echo running

```

---

### Post by sam_baker2 on 2015-06-08
thanks Lars

---

### Post by Habitual on 2015-06-08
if [[ -d /path/to/directory  ]]  ; then exit ; else mkdir /path/to/directory ; fi

You could put that in **your** ~/.bashrc...

Reference:
[http://tldp.org/LDP/abs/html/fto.html](http://tldp.org/LDP/abs/html/fto.html)
[http://stackoverflow.com/questions/59838/check-if-a-directory-exists-in-a-shell-script](http://stackoverflow.com/questions/59838/check-if-a-directory-exists-in-a-shell-script)

---

### Post by ofnuts on 2015-06-09
> **Habitual said:**
> if [[ -d /path/to/directory  ]]  ; then exit ; else mkdir /path/to/directory ; fi

You could put that in **your** ~/.bashrc...

And make your .bashrc exit too early if the directory exist :)

---

