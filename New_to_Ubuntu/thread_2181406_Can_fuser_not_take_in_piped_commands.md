---
title: "Can fuser not take in piped commands?"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by ouch67 on 2013-10-17
Here is the line I'm trying to run:

nmap localhost | grep -Eo '^[0-9]*/[a-z]*' | tr '\n' ' ' | fuser -uv

Which in my mind work fine but fuser keeps saying: "no process specification given"

the output of:

nmap localhost | grep -Eo '^[0-9]*/[a-z]*' | tr '\n' ' '

returns:

80/tcp 2222/tcp

which should be ideal considering the following works just fine:

fuser -uv 80/tcp 2222/tcp

Any ideas?

---

### Post by drmrgd on 2013-10-17
Maybe try process substitution instead?

```

$ fuser -uv <(nmap localhost | grep -Eo '^[0-9]*/[a-z]*')

```

---

### Post by ouch67 on 2013-10-17
That gives: "Specified filename /dev/fd/63 does not exist."

heh... not even sure what what its doing there...

---

### Post by drmrgd on 2013-10-17
Hmmmm...well I'm a little out of my element as I'm not 100% on what fuser does and what you're trying to get from it (even after reading the man pages).  When I run without fuser, I get:

```

$ nmap localhost | grep -Eo '^[0-9]*/[a-z]*' | tr '\n' ' '
25/tcp 53/tcp 80/tcp 631/tcp 902/tcp

```

And when I run by redirecting that output into fuser, I get:

```

$ fuser -uv <(nmap localhost | grep -Eo '^[0-9]*/[a-z]*' | tr '\n' ' ')
                     USER        PID ACCESS COMMAND
/dev/fd/63:          dave       4148 F.... (dave)bash
                     dave       4152 F.... (dave)tr


```

But I honestly am not too sure on how this is working.

---

