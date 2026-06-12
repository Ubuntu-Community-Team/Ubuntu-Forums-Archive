---
title: "colorizing &quot;$&quot; in PS1 if $? not equal to 0"
date: 2009-05-01
forum: Programming Talk
---

### Post by retrovertigo on 2009-05-01
Currently my PS1 prompt is:

```
\[\033[00;32m\]\u@\h\[\033[00m\]:\[\033[00;34m\]\w\[\033[00m\]\[\033[${?/[^0]/31}m\]\$\[\033[00m\]
```

I got the part around the "$" from a website while looking for ways to show an indicator in my PS1 prompt when the last command failed/exited with nonzero. If the command fails with status 1 (or, I guess, with any single-digit nonzero value), then the variable expansion **${?/[^0]/31}** will successfully evaluate to 31, turning the "$" red.  However, many commands, when unsuccessful, exit with status 127 rather than 1.  In these cases, the variable expansion above will evaluate to 3127, which bash will ignore since it's not a valid color code, and the "$" will stay white.

---

### Post by geirha on 2009-05-01
Interesting. Didn't know you could do that. Try with ${?/[^0][0-9]*/31}, to also cover the other digits.

Actually, ${?/[^0].*/31} should be enough.

EDIT: Tested myself. The pattern is not treated like a regular expression, so ${?/[^0]*/31} is my final offer :)

---

### Post by Arndt on 2009-05-01
> **geirha said:**
> Interesting. Didn't know you could do that. Try with ${?/[^0][0-9]*/31}, to also cover the other digits.

Actually, ${?/[^0].*/31} should be enough.

An arithmetic expansion should work too:

```
$(($?==0?0:31))
```

---

### Post by retrovertigo on 2009-05-01
> **Arndt said:**
> An arithmetic expansion should work too:

```
$(($?==0?0:31))
```

YES.  This is exactly what I needed.  Here's my new PS1, in case anyone wants to try it:

**\[\033[00;32m\]\u@\h\[\033[00m\]:\[\033[00;34m\]\w\[\033[00m\]\[\033[$(($?==0?0:31))m\]\$\[\033[00m\]**

Remember to put a space after it when exporting, unless you want the command to butt up against the "$".

I had no idea you could do arithmetic expansions like that.  Awesome.  Learn something new every day.

---

### Post by Arndt on 2009-05-01
> **retrovertigo said:**
> YES.  This is exactly what I needed.  Here's my new PS1, in case anyone wants to try it:

**\[\033[00;32m\]\u@\h\[\033[00m\]:\[\033[00;34m\]\w\[\033[00m\]\[\033[$(($?==0?0:31))m\]\$\[\033[00m\]**

Remember to put a space after it when exporting, unless you want the command to butt up against the "$".

I had no idea you could do arithmetic expansions like that.  Awesome.  Learn something new every day.

And I didn't know the pattern $ / / thing. I learn a lot by trying to answer questions here :-)

---

