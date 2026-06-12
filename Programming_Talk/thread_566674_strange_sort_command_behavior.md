---
title: "strange sort command behavior"
date: 2007-10-03
forum: Programming Talk
---

### Post by fuzzywombat on 2007-10-03
I ran into a strange sort command result by accident and I thought I'd share this with you.

Here is an example to demonstrate this oddity.  Create a file with follow five lines and name it as test.txt:

```
a-bc
a-cd
abc
acd
ade
```

It look like they are sorted correctly right?   However when you run sort command against test.txt you get this instead:

```
abc
a-bc
acd
a-cd
ade
```

Of course this just doesn't look right.  It's almost as if sort command ignores the hyphen when sorting.  If searched and found out that I had to set environment variable LC_ALL to C.  I added export LC_ALL=C to ~/.bashrc and restarted the shell.  After that sort command seems to confirm that test.txt is indeed sorted correctly.  It appears locale setting affects sort command.  Is this a bug or is it a "feature"?

---

### Post by yabbadabbadont on 2007-10-03
It is by design.  Sorting lexicographically is dependent upon language and locale.  One of the first things that I do when I reinstall is to add ```
LC_COLLATE="POSIX"
``` to /etc/default/locale.

---

### Post by dgologanov on 2007-12-04
Hi there... I hit similar issue and LC_COLLATE="POSIX" in /etc/default/locale didn't help me...

The issue (on Ubuntu 7.04 and 7.10):

```
$ sort
[COLOR="Red"]='ls
l='ls
s='ls[/COLOR]
Control-D
[COLOR="Red"]l='ls
='ls
s='ls[/COLOR]
```

I tried it on Debian and there it worked fine. The output stream was the same as the input one. The sort utility version is 5.97 on both of them.

I put LC_COLLATE=... on 7.04 and restarted the machine. The result still was "=" in between "l" (lower case "L") and "s".

HELP and thank you in advance!

---

### Post by dgologanov on 2007-12-04
I put

```
export LC_ALL=POSIX
```

in /etc/profile and everything works fine right now.

---

