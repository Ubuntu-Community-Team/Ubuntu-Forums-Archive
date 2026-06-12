---
title: "Terminal command for copying 1 file multiple times"
date: 2014-03-25
forum: New to Ubuntu
---

### Post by sashhhh on 2014-03-25
Hello! As the title says, is there a command that can copy one file multiple times in a given directory?

---

### Post by TheFu on 2014-03-25
I must be missing some understanding, but ...
```

cp path-to-file/file target-directory/
```
If the file is large, using something like **rsync** might be better.

---

### Post by sashhhh on 2014-03-25
Yeah, but that is to just copy the file, right? Here's my case, more precisely;

I have a 1 file, and from it I want to make a 1000 copies. How do I do that?

---

### Post by Lars Noodén on 2014-03-25
Maybe something like this:

```

for i in {1..999};do cp x x$(printf '%03d' $i);done

```

If it's going to be the same file you can hard link it instead of copying it.  See the manual page for cp for that.

---

### Post by steeldriver on 2014-03-25
You could also do something like

```
tee < *source* *target*{000..999} > /dev/null
```

---

### Post by frankmorris2 on 2014-03-25
> **Lars Noodén said:**
> Maybe something like this:

```

for i in {1..999};do cp x x$(printf '%03d' $i);done

```

If it's going to be the same file you can hard link it instead of copying it.  See the manual page for cp for that.

Hello,
Not to disagree with Lars Noodén, I would like to suggest this version of the command:
```

for i in $(seq -w 1 999) ; do cp x x$i ; done

```
The "-w" option will use padding in the sequence.

Just my 2 cents.

Have a nice day.

---

### Post by steeldriver on 2014-03-25
^^^ fyi you can pad the sequence natively (i.e. without seq) using {000..999}

---

### Post by frankmorris2 on 2014-03-25
Thank you steeldriver!

I didn't know about this syntax. My code will be even simpler :-)

---

### Post by sashhhh on 2014-03-27
Thank you very much :)

---

