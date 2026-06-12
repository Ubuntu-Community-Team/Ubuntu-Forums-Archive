---
title: "[python || shell] Comparing text files, creating patches, etc."
date: 2009-02-04
forum: Programming Talk
---

### Post by imbuto on 2009-02-04
Hi,

I am comparing two text files and a want to display the differences in a meaningful and possibly minimal way.
Suppose I want to compare:
text1
```

Text:
This is a string.


```
text2
```

Text:
This is again a string.


```
I started with the shell command diff. This only compares line by line (as far as I know), so it is not very useful in case of long lines with little differences (IMO very useful for source code, but not for text documents)
```

import os
os.system('diff -n text1 text2')

```
Output:
```

d2 1
a2 1
This is again a string.

```
The Python standard library difflib provides a sequence matcher which almost does what I want, finding the differences inside a line.
```

import difflib
text1 = open('text1', 'rb').read()
text2 = open('text2', 'rb').read()

s = difflib.SequenceMatcher(None, text1, text2)
m = s.get_matching_blocks()

for oc in s.get_opcodes():
    print "%8s %s <=> %s" % (oc[0], repr(text1[oc[1]:oc[2]]), repr(text2[oc[3]:oc[4]]))

```
Output:
```

   equal 'Text:\nThis is a' <=> 'Text:\nThis is a'
  insert '' <=> 'gain a'
   equal ' string.\n' <=> ' string.\n'

```
But, the output is not the most natural: the comparison is done character by character, and not word by word. So it tells me: you inserted 'gain a' after 'This is a'. Obviously what I want is: you inserted 'again ' after 'This is ' (the position of the spaces doesn't bother me).

So, the question is: is there a ready-to-use way to obtain a word by word comparison or do I have to write the function myself?

Thanks!

Note that:
```

d = difflib.Differ()
result = list(d.compare(text1.splitlines(), text2.splitlines()))
print '\n'.join(result)

```
displays the differences in the desired way:
```

 Text:
- This is a string.
+ This is again a string.
?        ++++++


```
...so in the worst case I will try to use this output to get the opcodes.

---

### Post by Reiger on 2009-02-04
You may want to look into diff & patch ?

---

### Post by scooper on 2009-02-04
If you don't mind a QT-based graphical tool, kdiff3 has some flexibility about how the comparison is done.  I'm not sure whether or not there's an option for word diff, but it definitely shows sub-line changes in useful ways.  Worth a look anyway.

---

