---
title: "Matching RegExps using grep"
date: 2007-07-25
forum: Programming Talk
---

### Post by Tsuki on 2007-07-25
Hi, I'm probably being really dumb here, but can anyone see why this doesn't work?

I've got a bunch of text (curled from a forum that doesn't support notifications / syndication).  Somewhere in the middle is text like so:
```
09:32, Wed 25 Jul by Tsuki
```
That's surrounded by a bunch of HTML, and I'm trying to extract it by piping it into grep.  Here's my code:
```
egrep --only-matching --regexp=[0-9]+:[0-9]+,\\s\\w+\\s\\w+\\s\\w+\\sby\\s\\w+
```

Any ideas?

---

### Post by stylishpants on 2007-07-25
You're using \w and \s a lot.  These are only available when you're using perl-compatible regular expressions.  egrep uses POSIX regular expressions.  

You could accomplish this with perl:

```
 perl -ne 'print if /[0-9]+:[0-9]+,\s\w+\s\w+\s\w+\sby\s\w+/'
```

Or rewrite your previous regexp to use '[A-Za-z0-9_]' in place of '\w' and a bunch of whitespace chars inside a character class instead of '\s'.

Another option is to install and use pcregrep (it's in the repos.)
```

fhanson@fh:~$ echo "09:32, Wed 25 Jul by Tsuki" | pcregrep -o '\d+:\d+,\s\w+\s\w+\s\w+\sby\s\w+'
09:32, Wed 25 Jul by Tsuki

```
Also, unless you hate yourself, surround your non-trivial regular expressions with single quotes so that they won't get escaped by the shell.  Regular expressions are tricky enough to parse visually without also having to consider shell escaping.

```

# Harder to read:
egrep --only-matching --regexp=[0-9]+:[0-9]+,\\s\\w+\\s\\w+\\s\\w+\\sby\\s\\w+

# Easier to read: (still won't work though due to the problem mentioned above)
egrep -o  '[0-9]+:[0-9]+,\s\w+\s\w+\s\w+\sby\s\w+'
```

---

### Post by Tsuki on 2007-07-26
Thank you!  I didn't realise \s and \w weren't POSIX-compatible.  My script's now working!
(Thanks for the hint about the quotes, too.  Not sure why I didn't think of that...)

---

