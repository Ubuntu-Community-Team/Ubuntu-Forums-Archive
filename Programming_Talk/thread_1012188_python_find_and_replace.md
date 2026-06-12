---
title: "python find and replace"
date: 2008-12-15
forum: Programming Talk
---

### Post by drizzle on 2008-12-15
I am new to python scripting and this doesn't sound like it should be difficult, but I've spent several hours trying to figure it out with no luck.  I want to:

open a text file
search for a string and replace with another string
write it back out to the same file name

I've seen lots of suggestions on how to read a string and replace text but never on how to write the file back out.  With bash scripting I used sed, but I don't know what to do in python.

Thanks in advance.

---

### Post by mssever on 2008-12-15
Assuming the file is open for writing, just use ```
the_file.write(your_modified_string)
```

---

### Post by drizzle on 2008-12-15
Using what I know right now, here's what I'm trying to do:

```
f=open('testfile','r+').read()
m=f.replace('text','new_text')
print m
m.write()
```

print m writes out what I want to be in the file, but I get an error when I try to write m to a file like that.  I'd rather just write back out to my original file name, but I'll take what I can get at this point.
 
Thanks.

---

### Post by mssever on 2008-12-15
> **drizzle said:**
> Using what I know right now, here's what I'm trying to do:

```
f=open('testfile','r+').read()
m=f.replace('text','new_text')
print m
m.write()
```print m writes out what I want to be in the file, but I get an error when I try to write m to a file like that.  I'd rather just write back out to my original file name, but I'll take what I can get at this point.
 
Thanks.
You don't have your file object available. Try this instead:```
from __future__ import with_statement

with open('testfile','r+') as f:
    m = f.read().replace('text','new_text')
    print m
    f.write(m)
```EDIT: When writing files, be sure to close them when your finished, unless you're using the with statement as in my example.

---

### Post by drizzle on 2008-12-15
I get a syntax error on the with open(....) line.

EDIT: I expected "with" to highlight and it didn't and a little googling makes me think that with statements weren't added until Python 2.5.....and I'm using Python 2.4.  This is a work computer and I don't have root privileges either.  Sorry.

---

### Post by bobbocanfly on 2008-12-15
> **drizzle said:**
> I get a syntax error on the with open(....) line.

EDIT: I expected "with" to highlight and it didn't and a little googling makes me think that with statements weren't added until Python 2.5.....and I'm using Python 2.4.  This is a work computer and I don't have root privileges either.  Sorry.

Make sure you include the "from __future__ import with_statement" line if using the with statement with Python 2.5 or less. It has become standard in Python 2.6 and above, but is still available in 2.5 if you import it that way.

---

### Post by mssever on 2008-12-15
> **drizzle said:**
> I get a syntax error on the with open(....) line.

EDIT: I expected "with" to highlight and it didn't and a little googling makes me think that with statements weren't added until Python 2.5.....and I'm using Python 2.4.  This is a work computer and I don't have root privileges either.  Sorry.
In 2.4, you'll have to do something like this, since the with statement isn't available: ```
f = open('testfile','r+')
m = f.read().replace('text','new_text')
print m
f.write(m)
f.close()
```

---

### Post by drizzle on 2008-12-15
> **mssever said:**
> In 2.4, you'll have to do something like this, since the with statement isn't available: ```
f = open('testfile','r+')
m = f.read().replace('text','new_text')
print m
f.write(m)
f.close()
```


We're getting close.  That made a copy of my text file and appended it to the 'testfile' with the appropriate replacements.  So basically I have my original lines and new lines in the same file.  How can I overwrite the original text with the replacement text?  Thanks.

---

### Post by mssever on 2008-12-15
> **drizzle said:**
> We're getting close.  That made a copy of my text file and appended it to the 'testfile' with the appropriate replacements.  So basically I have my original lines and new lines in the same file.  How can I overwrite the original text with the replacement text?  Thanks.
Look in the official Python tutorial for confirmation, but you need to open in write mode, not append mode. There's probably a better way, but this should work, and I'm too lazy to look it up:
```
f = open('testfile')
m = f.read().replace('text','new_text')
print m
f.close()
f = open('testfile', 'w')
f.write(m)
f.close()
```

---

### Post by pp. on 2008-12-15
> **mssever said:**
> open in write mode, not append mode.

Unless, of course, you write the changed text to a new file and swap the files when done. That way, you can repeat the process as often as you like, even unto the time when your program actually works.

I'm still lazier and don't even think of offering any bits of code. That's left to the kind reader.

---

### Post by ghostdog74 on 2008-12-15
you can use fileinput
```

import fileinput
for line in fileinput.FileInput("file",inplace=1):
  line=line.strip().replace("blah,"change")
  print line

```

---

### Post by drizzle on 2008-12-15
I just wanted to say thanks to everyone for their input.  Unfortunately (or fortunately, depending on how you look at it) I'll be away from my desk for a few days and won't get a chance to try anything else.  I'll follow up when I get back in town. Thanks again.

---

### Post by iQuizzle on 2008-12-16
this kind of thing is typically done with the "regular expression" (or regex for short) module. take a look here:

[http://www.python.org/doc/2.5.2/lib/re-objects.html]("http://www.python.org/doc/2.5.2/lib/re-objects.html")

if you wanted to replace all instances of a string you would do this:

```

import re

fh = open('myfile.txt','r')
stuff = fh.read()
fh.close()

new_stuff = **re.sub**('old_text','new_text',stuff)
fh = open('mynewfile.txt','w')
fh.write(new_stuff)
fh.close()

```


i haven't checked that, but it should work or be close. hope that helps!

---

### Post by pmasiar on 2008-12-16
> **iQuizzle said:**
> if you wanted to replace all instances of a string

Why use regex if lists are enough?

new_string = 'new'.join(old_string.split('remove'))

I use regex only when I need the regex matching functionality.

---

### Post by mssever on 2008-12-16
Regexes are awesome, but they're not always the best solution. For one thing, regexes are inherently slower (because they have to do more advanded processing) than string modification methods. For another thing, they're awkward to use in Python (I'm speaking as a Ruby programmer here). So when other methods suffice, it doesn't make a whole lot of sense to use the re module.

---

### Post by ghostdog74 on 2008-12-16
> **mssever said:**
>  For one thing, regexes are inherently slower (because they have to do more advanded processing) than string modification methods. 

not true
> 
For another thing, they're awkward to use in Python (I'm speaking as a Ruby programmer here). 


not true.

---

### Post by mssever on 2008-12-16
> **ghostdog74 said:**
> not trueI should have clarified that I don't know the details of regexes in Python. In some languages (such as PHP), the documentation clearly states that they're slower. I must admit that I don't know what optimizations Python uses.

> not true.Compared to Ruby, my statement was 100% true.

---

### Post by ghostdog74 on 2008-12-16
> **mssever said:**
> 
Compared to Ruby, my statement was 100% true.
i said its not 100% true, because as always, its down to the individual.

Also, with regards to PHP regexs, i do know of cases where its regex are faster than using its string functions. I am not sure about the docs that you mentioned though.

---

### Post by iQuizzle on 2008-12-16
well there's a lot of ways of accomplishing the same goal. i was just offering a solution with regex because it's easy and i've never run into speed issues with it...though i haven't used it all that extensively.

---

