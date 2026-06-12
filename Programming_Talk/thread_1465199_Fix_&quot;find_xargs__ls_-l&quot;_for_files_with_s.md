---
title: "Fix &quot;find xargs | ls -l&quot; for files with spaces in name"
date: 2010-04-29
forum: Programming Talk
---

### Post by dragos2 on 2010-04-29
I have this command:
```

 find /folder -type f -mmin -20 2>/dev/null | xargs ls -l

```

which will fail for files with spaces in their names. Actually ls -l fails.

Any fix for this ?

---

### Post by raffaele181188 on 2010-04-29
[This is a good start ;)]("http://en.wikipedia.org/wiki/Xargs")
You have two alternatives:
[LIST]
[*]use switch -print0 (zero) for find and -0 (zero) for xargs
[*]Use a bash script with a for cycle
```

for f in /path/* do;
  # if is a directory
  ls -l "$f"
done

```
[/LIST]

---

### Post by dragos2 on 2010-04-29
> **raffaele181188 said:**
> [This is a good start ;)]("http://en.wikipedia.org/wiki/Xargs")
You have two alternatives:
[LIST]
[*]use switch -print0 (zero) for find and -0 (zero) for xargs
[*]Use a bash script with a for cycle
```

for f in /path/* do;
  # if is a directory
  ls -l "$f"
done

```
[/LIST]


Thanks :) I think I will go the more secure way with Bash.

---

### Post by dragos2 on 2010-04-30
Any idea of how to make it output only files like

```

find /folder -type f

```

does ?

---

### Post by ntg on 2011-05-10
Try ```
find xargs |sed 's/$/"/'|sed 's/^/"/'| xargs ls -l
``` ;) ....

---

### Post by v8YKxgHe on 2011-05-10
> **ntg said:**
> Try ```
find xargs |sed 's/$/"/'|sed 's/^/"/'| xargs ls -l
``` ;) ....

I'm sorry, but that is just 100% how *not* to do it.

dragos2, the following is all you need to do:
```
find . -type f -exec ls -l {} \;
```

---

### Post by slavik on 2011-05-11
here's a better one in that specific instance ...

```
find /blah/ -ls
```

:)

a more general solution I use on near everyday basis:
```
find /blah | sed 's/ /\\ /g'
```

---

