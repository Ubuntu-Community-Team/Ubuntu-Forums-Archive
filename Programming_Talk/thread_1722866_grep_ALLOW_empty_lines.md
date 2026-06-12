---
title: "grep ALLOW empty lines"
date: 2011-04-06
forum: Programming Talk
---

### Post by mahy on 2011-04-06
Hello,

I've got an unusual problem, I need to filter out matching lines of a file, but ALLOWING empty lines. Grep is behaving a little strange

```
cat file | grep '^$'
```
This works and of course ONLY prints empty lines. That's not what I want.

```
cat file | grep '^$ \| PATTERN'
```
This DOES NOT work and ONLY prints lines matching the "PATTERN", ignoring empty lines. Again, not what I want. I want BOTH the matching lines AND empty lines.

Many thanks in advance for any help!

---

### Post by gmargo on 2011-04-06
Use **grep(1) **with **-E** option, or just use **egrep(1).**
```

cat file | egrep '^$|PATTERN'

```

---

### Post by Vaphell on 2011-04-06
```
echo $'abc PATTERN def\nsomething\n\nabc PATTERN def' | grep -E '^$|PATTERN'

result:
abc **PATTERN** def

abc **PATTERN** def
```

btw, drop cat, grep can read the file on its own just fine
```
grep <stuff> file
```

---

### Post by mahy on 2011-04-07
Thx a lot, egrep worked! :guitar:

---

