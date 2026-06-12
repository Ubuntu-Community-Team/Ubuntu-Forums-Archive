---
title: "Spliting a variable"
date: 2014-04-28
forum: Programming Talk
---

### Post by WoodenWalker on 2014-04-28
Hello all,

I'm fairly new to programming and have run into a minor problem on a custom bash script I was writing. I have a variable that I'll call $foo. $foo's value is set at foo-x.y-z.bar. I can't figure out how to capture just the "foo-x.y" part of that variable for use in another variable. I have been searching the web for hours. If anyone could help me, I would really appreciate it.

---

### Post by steeldriver on 2014-04-28
Like this maybe?

```

$ echo "${var%-z.bar}"
foo-x.y

```
or with assignment
```

$ **newvar="${var%-z.bar}"**
$ echo "$newvar"
foo-x.y

```

See [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

---

### Post by ofnuts on 2014-04-29
As above but if 'foo-x.y-z.bar' is a file name, and '.bar' is an extension you know in advance, you can also have a look at the 'basename' command.

---

### Post by WoodenWalker on 2014-04-29
Thank you so much guys. That is exactly what I needed, and I will definitely look into that basename command as well. I had never heard of it prior to now, but it sounds like a useful tool to have in my arsenal. :)

---

