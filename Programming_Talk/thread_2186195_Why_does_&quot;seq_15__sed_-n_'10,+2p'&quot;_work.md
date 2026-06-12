---
title: "Why does &quot;seq 15 | sed -n '10,+2p'&quot; work?"
date: 2013-11-06
forum: Programming Talk
---

### Post by vasa1 on 2013-11-06
If I run **seq 15 | sed -n '10,+2p'**, I get
10
11
12
as the output.

I thought I'd get an error because I didn't use the **-r** option. According to [http://www.gnu.org/software/sed/manual/html_node/Extended-regexps.html](http://www.gnu.org/software/sed/manual/html_node/Extended-regexps.html) , **+**, **?**, parentheses and braces need to be escaped.

If I try **seq 15 | sed -nr '10,+2p'**, I get the same output but if I try **seq 15 | sed -n '10,\+2p'**, I get **sed: -e expression #1, char 7: unterminated address regex**

So why does omitting **-r** work just fine and why does trying to escape **+**, give an error?

---

### Post by steeldriver on 2013-11-06
Because in this case the + is part a numeric address range, not a regex?

---

### Post by vasa1 on 2013-11-06
> **steeldriver said:**
> Because in this case the + is part a numeric address range, not a regex?

Just to be clear then, only **+**, **?**, **()** and **{}** between **/** and **/** need to be escaped if **-r** isn't used?

---

### Post by Vaphell on 2013-11-06
you can add | to that list. Also depends what you mean by between / and / - 's' doesn't have to look like this: s///
```
sed '/escape here/s:escape here::'
```

i prefer to use -r because regexes are much cleaner and more consistent (without -r some quantifiers have to be escaped but some don't). Yeah yeah, not posix compliant ;-)

---

### Post by vasa1 on 2013-11-06
> **Vaphell said:**
> you can add | to that list. Also depends what you mean by between / and / - 's' doesn't have to look like this: s///
```
sed '/escape here/s:escape here::'
```

i prefer to use -r because regexes are much cleaner and more consistent (without -r some quantifiers have to be escaped but some don't). Yeah yeah, not posix compliant ;-)

Okay so the list becomes +, ?, |, () and {}?

But, as you say, using -r will make the expression cleaner.

And by ** 's' doesn't have to look like this: s///**, are you referring to the picket fence business?

---

### Post by Vaphell on 2013-11-06
> And by 's' doesn't have to look like this: s///, are you referring to the picket fence business?

It's somewhat related, but what i meant was that if you say "between / and /" then thechnically *s* doesn't fall in this category because there is nothing that says you have to use / to delimit its parts (same deal with *y*). The only part that requires use of / is the regex that filters lines (***/regex/**cmd or **/regex/**{block of cmds}*).

If you said [+?|{}()] need to be escaped in regular expressions wherever they are, there would be no ambiguity

---

### Post by sha1sum on 2013-11-07
> **vasa1 said:**
> Okay so the list becomes +, ?, |, () and {}?


Correct. The characters:
[FONT=courier new]
^ $ . [ ] *[/FONT]

are part of POSIX basic and do not need to be backslash escaped.

The characters

[FONT=courier new]( ) { } ? + |[/FONT]

are part of extended regular expressions and need to be backslash escaped in sed and grep, unless you add the option -r and -E respectively. However in this case '10,+2p' is not a regular expression so you don't need to backslash escape anything, but you already figured that out.

---

### Post by vasa1 on 2013-11-08
@sha1sum, thanks! Updated my notes :)

---

