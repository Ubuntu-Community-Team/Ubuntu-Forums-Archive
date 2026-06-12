---
title: "pipe file names from pdfgrep to a file"
date: 2013-08-27
forum: Programming Talk
---

### Post by vahaboglu on 2013-08-27
I can search a pattern inside pdf files and copy files those having the string pattern to another directory by means of the code offered  below:

"Thank you Vaphell"

```
while read -r ln; do f=${ln%:*}; c=${ln##*:}; [ "$c" -gt 0 ] &&  cp -t "/home/yyy/zzz" "$f"; done < <( pdfgrep -cr xxx . )

```

My I copy file names to a file ie "match.txt" instead of copying them to another directory.

Appreciate any help

---

### Post by Bucky Ball on 2013-08-27
*Thread moved to **Programming Talk**.*

---

### Post by steeldriver on 2013-08-27
You could modify your existing expression

```
while read -r ln; do f=${ln%:*}; c=${ln##*:}; [ "$c" -gt 0 ] &&  **echo "$f"**; done < <( pdfgrep -cr xxx . ) **> match.txt**
```

or try

```
pdfgrep -cr xxx . | awk -F: '$2 > 0 {print $1}' > match.txt
```

---

### Post by vahaboglu on 2013-08-27
Steeldriver thank you,
your code is working perfectly
```

```while read -r ln; do f=${ln%:*}; c=${ln##*:}; [ "$c" -gt 0 ] &&  **echo "$f"**; done < <( pdfgrep -cr xxx . ) **> match.txt```

```**

---

### Post by steeldriver on 2013-08-27
You're welcome - it's still really Vaphell's ;)

---

