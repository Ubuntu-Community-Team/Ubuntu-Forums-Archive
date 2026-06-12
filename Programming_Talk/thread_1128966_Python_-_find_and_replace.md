---
title: "Python - find and replace"
date: 2009-04-18
forum: Programming Talk
---

### Post by blairm on 2009-04-18
Hi,

Trying to use python to do multiple find and replaces in a text file, and write the changed text to another file; I can do a single find and replace by using re.sub - ie:

import re

fh = open('testtextparse','r')
stuff = fh.read()
fh.close()

new_stuff = re.sub('word',r'replacement\n',stuff)
fh = open('mynewfile.txt','w')
fh.write(new_stuff)
fh.close()

To do a second find and replace, do I need to repeat these seven lines, or can I just add a line to what I have above? 
Have googled but haven't found anything that appears to help. If ayone could point me in the right direction it would be much appreciated.
Have a grand total of about three weeks playing with python over the past three months so still very much a beginner.

Cheers,

Blair

---

### Post by benj1 on 2009-04-18
```
import re

fh = open('testtextparse','r')
stuff = fh.read()
fh.close()

new_stuff = re.sub('word',r'replacement\n',stuff)
**new_stuff = re.sub('word2',r'replacement2\n',new_stuff)**
fh = open('mynewfile.txt','w')
fh.write(new_stuff)
fh.close()
```

this is allowed if thats what youre asking

---

### Post by blairm on 2009-04-18
That's exactly what I was asking! Apologies if I wasn't clear.
Thanks for your help.

Blair

---

### Post by ghostdog74 on 2009-04-18
if its just simple replacement, no need for re
```

word="string"
word = word.replace("text1","repl").replace("text2","repl2")

```

---

### Post by blairm on 2009-04-18
sorry, posted in wrong place

---

