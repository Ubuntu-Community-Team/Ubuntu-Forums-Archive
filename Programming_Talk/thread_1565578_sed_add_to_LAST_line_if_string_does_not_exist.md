---
title: "sed: add to LAST line if string does not exist"
date: 2010-09-01
forum: Programming Talk
---

### Post by PryGuy on 2010-09-01
Good day!
Well, I'm new to sed and want a quick solution now. The line below adds 'string2' if 'string1' does not exist.
```
sed -i '/[.]*string1[.]*/!a\string2\' file
```
But how do I add it only once in the end of the file? I know I should use '$' but where do I put it?
Thanks in advance!

---

### Post by Some Penguin on 2010-09-01
Please don't open duplicate threads.

[http://ubuntuforums.org/showthread.php?t=1565533](http://ubuntuforums.org/showthread.php?t=1565533)

---

