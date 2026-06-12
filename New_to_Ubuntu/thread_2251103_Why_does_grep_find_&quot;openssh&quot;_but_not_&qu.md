---
title: "Why does grep find &quot;openssh&quot; but not &quot;*ssh*&quot;?"
date: 2014-11-02
forum: New to Ubuntu
---

### Post by adj3 on 2014-11-02
[ATTACH=CONFIG]257691[/ATTACH]

---

### Post by sudodus on 2014-11-02
grep would look for the asterisks literally. So to get what you want, just use

```
grep ssh
```

---

### Post by adj3 on 2014-11-02
> **sudodus said:**
> grep would look for the asterisks literally. So to get what you want, just use

```
grep ssh
```

Thank you! :)

---

### Post by sisco311 on 2014-11-02
You didn't quote the argument so bash will try first to expand it. So if you happen to have a file named foosshbar in you current working directory, then instead of *ssh* foosshbar will be passed to grep.

And as the first character of an entire BRE (after an initial '^', if any) the * has no special meaning. *ssh* will match an asterisk followed by ss and zero or more h.

Check out: 

[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)
[http://mywiki.wooledge.org/RegularExpression](http://mywiki.wooledge.org/RegularExpression)

---

### Post by Lars Noodén on 2014-11-02
Also, the asterisks, unless wrapped in quotes, will get expanded by the shell.  Then on top of that, basic grep does not have regular expression pattern matching, so you'll want to use the -E option or 'egrep' instead.  Even then the asterisks work a little different that you are aiming for being [POSIX regular expressions](http://manpages.ubuntu.com/manpages/utopic/en/man7/regex.7.html) rather than Perl (PCRE).  You can activate PCRE matching in grep on Ubuntu using the -P option.

---

