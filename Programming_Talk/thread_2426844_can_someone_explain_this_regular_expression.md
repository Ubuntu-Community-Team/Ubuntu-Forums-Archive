---
title: "can someone explain this regular expression?"
date: 2019-09-14
forum: Programming Talk
---

### Post by Skaperen on 2019-09-14
this regular expression:
```

^(\d+)x(\d+)(?:\+(\d+))?(?:\+(\d+))?$

```
works for the original intention of matching X11 command -geometry= values.  now,i want to change it to match some other strings.  but, i don't understand the extra layering of () and what the ? are doing to it.  can someone who knows this explain it?

---

### Post by The Cog on 2019-09-14
For my own education, I'll have a stab:
```
^               At the start of the line
(\d+)           One or more digits. Remember this as group 1
x               The letter x
(\d+)           One or more digits. Remember this as group 2
(?:             Start a non-capturing group (not remembered), containing:
    \+(\d+)         A plus followed by one or more digits. Remember (I think) the digits as group 3
    )?              End the non-capturing group. The whole group may or may not exist.
(?:\+(\d+))?    A possible second non-capturing group like the last one (digits become group 4)
$               End of line
```
I presume that this is inside a programming language that will then look at the captured groups. I think it will capture 2, 3 or 4 groups of digits if it finds a match at all. The first two groups must be separated by an 'x', and the third and fourth optional groups must be preceded with a '+'. e.g. "123x456+7+89"

I would be grateful if someone more familiar with regex's could confirm or correct me.

---

### Post by &amp;KyT$0P# on 2019-09-14
The Cog is correct.

Depending on the context of that regex, ^ and $ might only match start and end of the **entire string**, respectively, rather than start and end of one line.

---

### Post by Skaperen on 2019-09-15
i'm more curious what the question marks are doing and if the string "600x300" (without the position values) is supposed to be able to match.  i was thinking the ? after that big group makes it an optional match.  i tried to change it and it didn't work at all so i must have messed it up.

i'd like to know how to make 2 or more expressions where exactly one of them, either or any one, must match.

---

### Post by sisco311 on 2019-09-15
What kind of regexen are we talking about?

---

### Post by Skaperen on 2019-09-15
supposedly pcre compatible used by python3's module named re.

---

### Post by The Cog on 2019-09-15
The question marks are in two places. 
The one in (?: starts a group, but the ?: says it's non-capturing, i.e. it doesn't get listed in the list of group contents.
The one after the groups say that the preceding item is just a possibility: it might exist or might not, but either way the match is successful.
This whole piece **(?:\+(\d+))?** describes a group containing a + followed by some digits. Ignore the + (it's a non-capturing group) but remember the digits (an inner group). The trailing question mark says the whole group may or may not exist, and its absence does not cause the match to fail.

"600x300" should match. The two optional groups are not present so the list of groups found will contain some None items. Beware of a index-out-of-range error if you try to read the content of the third or fourth group.

```
#!/usr/bin/python3

import re

match = re.match('^(\d+)x(\d+)(?:\+(\d+))?(?:\+(\d+))?$', '300x600+123+456')
print (match.groups())
match = re.match('^(\d+)x(\d+)(?:\+(\d+))?(?:\+(\d+))?$', '300x600')
print (match.groups())
```
produces
```
('300', '600', '123', '456')
('300', '600', None, None)

```

Thanks to halogen2 for confirming what I thought it meant.

---

### Post by ryansenn on 2019-09-15
I use this tool quite often when dealing with regex. It helps you visualise the result, and if you paste your regex in at the bottom you have a step by step explanation/breakdown: [https://regexr.com/](https://regexr.com/)

---

### Post by Skaperen on 2019-09-15
> **ryansenn said:**
> I use this tool quite often when dealing with regex. It helps you visualise the result, and if you paste your regex in at the bottom you have a step by step explanation/breakdown: [https://regexr.com/](https://regexr.com/)

that is an awesome tool.  thanks very much.

---

