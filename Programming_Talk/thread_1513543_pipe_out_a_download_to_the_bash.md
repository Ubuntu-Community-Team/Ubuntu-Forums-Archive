---
title: "pipe out a download to the bash?"
date: 2010-06-19
forum: Programming Talk
---

### Post by hakermania on 2010-06-19
wget [http://www.hakermania.t35.com/test](http://www.hakermania.t35.com/test) | sh
doesn't seem to work...
any ideas?

---

### Post by soltanis on 2010-06-19
To the current shell?

Try

```

wget -O - http://example.site.com/url.ext

```

Curl also works

```

curl http://example.site.com/url.ext

```

It generates output to the standard out by default.

---

### Post by hakermania on 2010-06-19
hm, i'll better try this:
wget [http://www.hakermania.t35.com/test;](http://www.hakermania.t35.com/test;) chmod +x test; sh test

...

---

### Post by soltanis on 2010-06-19
How about eval?

```

SCRIPT=`wget -O - http://path/to/script`
eval "$SCRIPT"

```

---

### Post by hakermania on 2010-06-20
No, ok, this I mentioned before work perfectly...See ya.

---

