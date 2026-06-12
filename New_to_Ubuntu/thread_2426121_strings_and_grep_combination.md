---
title: "strings and grep combination"
date: 2019-09-04
forum: New to Ubuntu
---

### Post by zak100 on 2019-09-04
Hi,

What is the purpose of following command: 

```


strings filename | grep '^@'


```
Can I use just grep command to perform the above task?

Zulfi.

---

### Post by Holger_Gehrke on 2019-09-05
'strings' finds strings of printable characters in files that might contain a lot of other stuff and prints them out one string per line. So the given code gives you readable strings from a binary file that start with '@' ('^' means beginning of line in grep). I don't know how to do that with just 'grep'.

Holger

---

### Post by zak100 on 2019-09-05
Hi,
And what you mean by string "sequence of characters ending with '\n'"?

Zulfi.

---

### Post by geek-n on 2019-09-05
Try this:

```
[FONT=courier new]egrep -ao '[[:print:]]{4,}' filename[/FONT]
```

This extracts printable strings 4 or more characters long. Note the ```
[[:print:]]
``` character class accepts a wider set of characters as printable than 'strings', so it will give a little more output.

---

