---
title: "Python regular expressions"
date: 2010-01-28
forum: Programming Talk
---

### Post by modernminerva on 2010-01-28
Is there a way to match a character multiple times, without knowing what the character is?

For example, something that will match any 6-letter word that starts and ends with the same letter?  Or any word that has the same first and third letters?

Additionally, is it possible to match a word whose letters are all different?  Or whose first 5 letters are all different?

I'm relatively new to regular expressions in python, so I'm not sure if this is easy/possible.

---

### Post by myrtle1908 on 2010-01-28
> **modernminerva said:**
> Is there a way to match a character multiple times, without knowing what the character is?

For example, something that will match any 6-letter word that starts and ends with the same letter?  Or any word that has the same first and third letters?

Additionally, is it possible to match a word whose letters are all different?  Or whose first 5 letters are all different?

I'm relatively new to regular expressions in python, so I'm not sure if this is easy/possible.

Most of those examples would be better served using length and substring functions and some equality operators.

---

### Post by diesch on 2010-01-29
> **modernminerva said:**
> Is there a way to match a character multiple times, without knowing what the character is?

For example, something that will match any 6-letter word that starts and ends with the same letter?  


```
r'(.).{4}\1'
```

> **modernminerva said:**
> 
Additionally, is it possible to match a word whose letters are all different?  Or whose first 5 letters are all different?


I don't think so

---

### Post by croto on 2010-01-29
I would add that if you need to match "words" you'd need something like
```

#!/usr/bin/python

import re
import sys

text = sys.stdin.read()
print "six letter words starting and ending with same letter:"
for match in re.findall(r"(\b(\w)\w{4}\2\b)", text):
        print match[0]

```

---

### Post by croto on 2010-01-29
for words with different letters, I guess you'd need to add some logic to the regexps. For instance:
```

#!/usr/bin/python

import re
import sys

text = sys.stdin.read()
print "five letter words with all different letters:"
matches = re.findall(r"\b\w{5}\b", text)
matches = filter( lambda s: len(set(s)) == 5, matches )
for match in matches:
        print match

```

---

