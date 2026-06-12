---
title: "stdin python"
date: 2012-02-08
forum: Programming Talk
---

### Post by conradin on 2012-02-08
Hi all 
Im learning python, and I want to write a python script that takes input from any number of input files and produces a histogram of all words that appear in the document.

What I have so far works for non filename input. Im not really sure about methodology. Should I combine the files first with a command like cat?
 then read that?

```
#!/usr/bin/python
import re
name = raw_input('File name\n')
def getWordFrequencies(text):
    frequencies = {}
    
    for c in re.split('\W+', text):
        frequencies[c] = (frequencies[c] if frequencies.has_key(c) else 0) + 1
            
    return frequencies


result = getWordFrequencies(name)

for word, freq in result.iteritems():
    print freq, "\t", word
```

---

### Post by Bodsda on 2012-02-08
> **conradin said:**
> Hi all 
Im learning python, and I want to write a python script that takes input from any number of input files and produces a histogram of all words that appear in the document.

What I have so far works for non filename input. Im not really sure about methodology. Should I combine the files first with a command like cat?
 then read that?

```
#!/usr/bin/python
import re
name = raw_input('File name\n')
def getWordFrequencies(text):
    frequencies = {}
    
    for c in re.split('\W+', text):
        frequencies[c] = (frequencies[c] if frequencies.has_key(c) else 0) + 1
            
    return frequencies


result = getWordFrequencies(name)

for word, freq in result.iteritems():
    print freq, "\t", word
```

I would allow the user to enter as many file names as they like, then read them in one by one, appending the contents of each file to a list. I can then close all files and just work on the list contents.

That does assume that the size of all files combined doesn't exceed free memory available though.

Bodsda

---

### Post by conradin on 2012-02-08
Does that involve a temp file or something? How would I do this?

> **Bodsda said:**
> I would allow the user to enter as many file names as they like, then read them in one by one, appending the contents of each file to a list. I can then close all files and just work on the list contents.

That does assume that the size of all files combined doesn't exceed free memory available though.

Bodsda

---

### Post by Bodsda on 2012-02-08
> **conradin said:**
> Does that involve a temp file or something? How would I do this?

No, what I would do is something along the lines of this

```

input = ""
list = []

while input not "done":
    input = raw_input("Enter a filename(enter 'done' when finished): ")
    list.append(input)

list.pop(-1)

contents = []

for file in list:
    handle = open(file, "r")
    contents.append(handle.read())
    handle.close()

#<do stuff with file contents>

```Bodsda

---

### Post by MadCow108 on 2012-02-08
you don't have to open all files at once to get the frequencies, just update the dict as you move from file to file.
thats much more easy on the ram.

you can still keep the logic nice by using generators:

```

def read_files(file_list):
  for fn in file_list:
     f = open(f)
     yield f.read()
     f.close()

from collections import defaultdict
frequencies = defaultdict(int)

for content in read_files([filea, fileb]):
   for c in re.split('\W+', content):
      frequencies[c]+=1

```
defaultdict is just to make the code a bit simpler, if you write to a nonexistant key it will be created as 0 (the result of int()).
(python3 provides a specialization of that called Counter, which pretty much does exactly what you want)

---

### Post by conradin on 2012-02-08
Hi all, 
Im still stuck on this, Ive been reading about the fileinput module which seems like exactly what I want to use, but this (%(*^&*#!) thing wont seem to work.
Heres my script thus far, when I use a string like mary, included, it works fine. When I try to assign a variable like name, it gives me an error about   File "./hist", line 4
    name = fileinput.

```
#!/usr/bin/python
import fileinput, sys, re, os

name = fileinput.input():

def getWordFrequencies(text):
    frequencies = {}
    
    for c in re.split('\W+', text):
        frequencies[c] = (frequencies[c] if frequencies.has_key(c) else 0) + 1
            
    return frequencies

mary = \
"Mary had a little lamb,\
Little lamb, little lamb,\
Mary had a little lamb,\
Its fleece was white as snow"

result = getWordFrequencies(name)

for word, freq in result.iteritems():
    print freq, "\t", word




```

Can some one point out where Im going wrong with this?:confused:

---

