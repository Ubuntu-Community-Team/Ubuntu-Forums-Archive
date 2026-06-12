---
title: "Script Help: Redirecting output"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by lotharmat on 2012-01-18
Hi All,

Got a bit of a conundrum:

I have a command that outputs a file and a path in the format

'path/to/file'

I want to use that output to feed into the copy command thus:

cp path/to/file ~/Desktop/

How would I go about doing it. I've been thinking along the lines of using xargs but am coming a bit unstuck.

Any help gratefully received.

---

### Post by lotharmat on 2012-01-18
Solved it!

```

cp `[commandName] | xargs` Desktop/

```

Easier than I thought!

---

