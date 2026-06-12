---
title: "How can I run multiple commands at once to restrict results?"
date: 2015-05-17
forum: New to Ubuntu
---

### Post by pgslmatias on 2015-05-17
Sorry if this a stupid question, but I'm trying to find a file that is human readable, not an executable and 1033 bytes in size. The file is inside a directory with sub directories, and I don't know in which sub directory it is. I was thinking about using du for file size, and file for file type but after lots of googling couldn't find how to do it with them together and the correct options. Any ideas?

---

### Post by sandyd on 2015-05-17
```
find -type f -size 1033c -exec grep -Il . {} \;
```

Breakdown:
[table="width: 500, class: grid"]
[tr]
	[td]-type f[/td]
	[td]only search files[/td]
[/tr]
[tr]
	[td]-size 1033c[/td]
	[td]set size (c for bytes, k for kilobytes, M for megabytes, G for gigabytes)[/td]
[/tr]
[tr]
	[td]-exec grep -Il[/td]
	[td]only non-binaries[/td]
[/tr]
[tr]
	[td].[/td]
	[td]search using current directory as top level[/td]
[/tr]
[/table]

---

### Post by steeldriver on 2015-05-17
It depends a bit what you mean by "human readable" - you could use a combination of the `find` and `mimetype` commands

```

find path/to/dir -type f -size 1033c -exec sh -c 'mimetype "$1" | grep -q text' _ {} \; -print

```

---

### Post by pgslmatias on 2015-05-17
Thanks I got it now!

---

