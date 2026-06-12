---
title: "posix reg expression"
date: 2007-07-30
forum: Programming Talk
---

### Post by OOzypal on 2007-07-30
How can I search for a complet line and pad it with /* and */. I mean let's say that I have this line


background-color:blue;

I would like to search for the whole line then change it to 

/* background-color:blue; */

The line could be anything

---

### Post by HalcónMaltés on 2007-07-30
If you're editing a text-based file, you may want to try the 'sed' command. Sed is a stream text editor, which has the replacing feature you seem to need. Take a [look]("http://lowfatlinux.com/linux-sed.html"), then use the man pages to get some more. :)

---

### Post by rjack on 2007-07-30
Something like this?
```
echo Hello World | sed 's%^.*$%/* & */%'
/* Hello World */
```

This will comment out all the lines containing "background-color:blue;"
```
sed 's%^background-color:blue;$%/* & */%'
```

---

### Post by Jessehk on 2007-07-30
This would do it:
```

sed -e 's;^\(.*\)$;/* \1 */;'

```

---

### Post by OOzypal on 2007-07-30
Actually, I am trying to use with bluefish custom menu replace.

I want to be able to highlight a text and comment it.

---

