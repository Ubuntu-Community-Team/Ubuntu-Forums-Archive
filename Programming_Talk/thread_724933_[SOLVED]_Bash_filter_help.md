---
title: "[SOLVED] Bash filter help"
date: 2008-03-15
forum: Programming Talk
---

### Post by Gen2ly on 2008-03-15
I'm still learning regular expressions so I hope someone doesn't mind helping me.  I've learned a regular expression to filter out everything from the right most hyphen: ${TEXT%-*} here's the input I'm going to be filtering.

```
foobar-0.1.text
foo-bar-0.1.text

```

The format is always name-version.ext.  ${TEXT%-*} works fine for these.   But sometimes these inputs are 

```
foo-bar-0.1-r1.text
```

I'm learning regular expressions at a gradual pace I'd be happy if someone couldhelp.

---

### Post by ghostdog74 on 2008-03-15
what are ALL the possible combinations of file names you may have?

---

### Post by Gen2ly on 2008-03-15
deriviations:

```
foobar-0.1.text
foo-bar-0.1.text
foo-bar-0.1-r1.text
```

I suppose there could be a

```
foo-bar-bar-0.1-r1.text
```

later on so the filter will apply to the hyphen by the version (there will always be a version number).

---

### Post by Trumpen on 2008-03-15
Given that version begins with a number you can exploit this by using something like:

```
 ${text%-[0-9]*}
```

---

### Post by Gen2ly on 2008-03-15
thanks 4 the help.  that did the trick

---

