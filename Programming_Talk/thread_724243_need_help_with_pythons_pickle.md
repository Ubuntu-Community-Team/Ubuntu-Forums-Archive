---
title: "need help with pythons pickle"
date: 2008-03-14
forum: Programming Talk
---

### Post by rob1101 on 2008-03-14
well im trying to make a simple program that will open a text file, let me edit it, and save it and close it. I was told that pickle was the best way to do this.

however i cant get pickle to work

the error:

```
Traceback (most recent call last):
  File "/home/robert/safe_edit.py", line 14, in <module>
    p = pickle.Pickler(in_flile)
NameError: name 'pickle' is not defined
```

the code:

```
# Get filepath
filepath = raw_input("Enter file path: ")

# Read file
in_file = open(filepath, "r")
text = in_file.read()

import pickle as p
p = pickle.Pickler(in_flile)
p.dump(text)

print text
```

any help or push in the right direction would be greatly appreciated.

---

### Post by luisromangz on 2008-03-14
If you import pickle as p, then the name pickle is not defined. p is defined instead of pickel. You should either remove the "as p" part, or use p instead of pickle in the right side of the assignement instruction, and rename the p variable you are using.

Meanwhile, pickle is a serialization library, useful to persist objects as a file, but not for treating text files.

---

### Post by mssever on 2008-03-14
You're doing ```
import pickle as p
``` So you can't call pickle.Pickler. Call p.Pickler, instead.

---

### Post by pmasiar on 2008-03-14
luisromangz and mssever are right about why you are getting the error message.

But let me question your need for pickle. Why such tricky way? You cannot believe all the advice you get on internet! :-) 

Pickle is to store whole object in some magical way so you can restore it later as it was, in single operation. If all you have is a text file, why you need to save it's content pickled? You cannot edit a pickled object. Just save file as text, after some transformation, it is more flexible. IMHO, YMMV.

---

### Post by rob1101 on 2008-03-14
thx guys, that fixed it :p duh

@pmasiar thats what i was thinking and was going to do it that way but could not think of a way to edit the file from within the program. i can read and write but how would i edit?

---

### Post by pmasiar on 2008-03-14
> **rob1101 said:**
> but could not think of a way to edit the file from within the program. i can read and write but how would i edit?

- To edit file in interactive mode: open it in any editor and do it
- to edit file in "programmatic" mode: read it, possibly line by line, or bigger chunks, depending on file structure; then process chunks with your code, and save (write) to another file. When done, rename files.

---

