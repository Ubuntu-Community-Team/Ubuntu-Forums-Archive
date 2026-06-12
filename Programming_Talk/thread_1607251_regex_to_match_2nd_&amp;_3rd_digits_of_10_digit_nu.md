---
title: "regex to match 2nd &amp; 3rd digits of 10 digit number"
date: 2010-10-27
forum: Programming Talk
---

### Post by decoherence on 2010-10-27
Hi all,

A quick question for the regex gurus on the forum. I have a number, 0123456789, for example, and I want to pull out "12."  That is, the second and third digits. The number will always be a ten digit long integer but aside from that, it could be anything. Simple, right? Hold on, there are some conditions.

1) no gnu userland. this command has to be extremely portable so no perl-style regex.

2) it's easy enough to do this by telling sed to chop off the front, then chop of the back. we'd like to find the 'perfect regex' tho that will match this without using multiple -e flags.

any takers?

---

### Post by gmargo on 2010-10-27
Simple in sed.
```

$ echo "0123456789" | sed 's/^.\(..\).*/\1/'
12

```Or cut
```

$ echo "0123456789" | cut -c 2-3
12

```

---

### Post by decoherence on 2010-10-27
> **gmargo said:**
> Simple in sed.
```

$ echo "0123456789" | sed 's/^.\(..\).*/\1/'
12

```Or cut
```

$ echo "0123456789" | cut -c 2-3
12

```

I always forget about the cut command!

Nice regex! Thanks for the help!

---

### Post by mo.reina on 2010-10-27
> **decoherence said:**
> Hi all,

A quick question for the regex gurus on the forum. I have a number, 0123456789, for example, and I want to pull out "12."  That is, the second and third digits. The number will always be a ten digit long integer but aside from that, it could be anything. Simple, right? Hold on, there are some conditions.

1) no gnu userland. this command has to be extremely portable so no perl-style regex.

2) it's easy enough to do this by telling sed to chop off the front, then chop of the back. we'd like to find the 'perfect regex' tho that will match this without using multiple -e flags.

any takers?

i don't quite understand what you mean by no perl-style regex... regex symbols are almost universal, e.g. ^ means beginning of a string and $ means end of a string...

anyway in python:
```
>>> astring
'012345679'
>>> import re
>>> re.search(r'\d(\d{2})\d*', astring).groups()
('12',)

```

---

### Post by decoherence on 2010-10-29
> **mo.reina said:**
> i don't quite understand what you mean by no perl-style regex... regex symbols are almost universal, e.g. ^ means beginning of a string and $ means end of a string...

anyway in python:
```
>>> astring
'012345679'
>>> import re
>>> re.search(r'\d(\d{2})\d*', astring).groups()
('12',)

```

Thanks for the python! Unfortunately we can't assume the system running this will have Python. Sorry I wasn't more clear -- basically I meant a BRE or ERE syntax but not PCRE. Anyhoo, problem solved! Marking as such

---

### Post by v8YKxgHe on 2010-10-29
Why did you want to use regex? You can just use Bash directly:

```
$ foo=0123456789
$ echo ${foo:1:2}
12
```

I know this is marked as solved, but this is by far the simplest way.

---

### Post by decoherence on 2010-10-31
> **AlexC_ said:**
> Why did you want to use regex? You can just use Bash directly:

```
$ foo=0123456789
$ echo ${foo:1:2}
12
```

I know this is marked as solved, but this is by far the simplest way.

We used basic regex for portability. Yes the bash method is nice and concise but does that same command work on csh/sh? I don't know for sure (kinda doubt it) but that sed regex gmargo posted seems to work just about anywhere.

What you posted is definitely a method I'd use if I could be assured of a bash environment. It's always fun to see the different ways people solve a problem and I love using built-ins wherever possible.

Thanks!

---

