---
title: "search replace first occurence on each line"
date: 2009-08-27
forum: Programming Talk
---

### Post by monkeyking on 2009-08-27
Hi I got some very long files that looks like

```

hash nam.id.txt
hash nam2.id.txt
...

```

And Id like to change the first punctuation on each line to a slash,such that the file would become

```

hash nam/id.txt
hash nam2/id.txt
...

```

Note that this is not a normal global search replace.

thanks in advance

---

### Post by kaibob on 2009-08-27
Post deleted by Kaibob

---

### Post by Can+~ on 2009-08-27
> **monkeyking said:**
> Note that this is not a normal global search replace.

In what sense?

[PHP]#!/usr/bin/env python

original = open("txtfile.txt", "r")
result = open("outfile.txt", "w")

for line in original:
	result.write(line.replace(".", "/", 1))[/PHP]

---

### Post by johnl on 2009-08-27
This is a perfect place for sed.
```

sed "s/\./\//" input.txt > output.txt

```

---

### Post by ghostdog74 on 2009-08-28
> **Can+~ said:**
> In what sense?

[PHP]#!/usr/bin/env python

original = open("txtfile.txt", "r")
result = open("outfile.txt", "w")

for line in original:
	result.write(line.replace(".", "/", 1))[/PHP]

just for completion, file handles should be closed (explicitly) in the above usage.

---

### Post by monkeyking on 2009-08-28
thanks the sed command is indeed perfect for this,

@can

I was trying to avoid, the first 5 replies beeing a global search replace.


Thanks

---

