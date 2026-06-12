---
title: "echo from X to Y"
date: 2006-03-09
forum: Programming Talk
---

### Post by jaykup on 2006-03-09
How would I go about doing something like this 
echo (start at __X__ , end at __Y__) 

__X__
 a lot of stuff
 goes here
 to be echoed
 even a lot of ' ` { } marks 
__Y__

using Bash or Sh

---

### Post by engla on 2006-03-09
This should work:

```
cat <<END_MARKER
text goes here
here
here
and here
END_MARKER
```
We use *cat* to echo, since the << redirection sends the text to the command's standard input.

Edit: Had to use cat, not echo

---

