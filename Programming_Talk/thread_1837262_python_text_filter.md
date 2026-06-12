---
title: "python text filter"
date: 2011-09-01
forum: Programming Talk
---

### Post by Michaël-D on 2011-09-01
hi,
i'm having some trouble writing a python text filter,
this is what i have got so far
```

import sys
a = open('in.txt', "r")
b = open('out.txt', "a")
for line in a.readlines():
    if line.startswith("string i'm looking for"):
        b.write(line)
b.close()
a.close()
sys.exit()

```BUT....if i know want to copy say the 3 lines preceeded by 'line' as well, how would i do that?

thx in advance,


M.

---

### Post by karlson on 2011-09-01
> **Michaël-D said:**
> hi,
i'm having some trouble writing a python text filter,
this is what i have got so far
```

import sys
a = open('in.txt', "r")
b = open('out.txt', "a")
for line in a.readlines():
    if line.startswith("string i'm looking for"):
        b.write(line)
b.close()
a.close()
sys.exit()

```BUT....if i know want to copy say the 3 lines preceeded by 'line' as well, how would i do that?

thx in advance,


M.

Unless you want to maintain the list of all lines read from the file in an array you would need to maintain some sort of circular buffer that would maintain previous 3 lines for you.  And when you match you output the 3 line buffer + the found line and clear the buffer.

---

### Post by Michaël-D on 2011-09-01
> **karlson said:**
> Unless you want to maintain the list of all lines read from the file in an array you would need to maintain some sort of circular buffer that would maintain previous 3 lines for you.  And when you match you output the 3 line buffer + the found line and clear the buffer.

thx for your fast reply, actually my problem is the following, the full string i would like to copy a 'sentence' that is longer then one line (so it continues on the next one).
after the full sentence i'm looking for there is a blank line, i hope that helps making things easier...

thx,

M.

---

### Post by Erdaron on 2011-09-01
If you are going to read all the lines at once, might as well make it an explicit list and then enumerate through it the boring way:
```
lines = a.readlines()
for i in range(len(lines)):
    actions
```
This way when you match what you were looking for you already have the index in the list, and can easily grab the previous three entries.

Is the whole sentence unique, or just the last part? If the whole sentence is unique, then you can do pre-screening by matching only the beginning of a sentence, and once you have a match, confirm by checking the whole sentence (grabbing the next line as well).

If only the last part is unique, then match only that. Once you have a hit, you know to grab the previous line as well.

---

### Post by karlson on 2011-09-01
> **Michaël-D said:**
> thx for your fast reply, actually my problem is the following, the full string i would like to copy a 'sentence' that is longer then one line (so it continues on the next one).
after the full sentence i'm looking for there is a blank line, i hope that helps making things easier...

thx,

M.

For something like this you would need to provide more information:

Are sentences contain within N complete lines?  If so then you would need to save the lines in an array and then dump this array out when blank line is reached or clear it when it is not.

In short analyze your data to determine what needs to be done and how it needs to be done.  You may need to have sentences reassembled from partial lines in order to display sentence only.

---

### Post by Michaël-D on 2011-09-01
> **Erdaron said:**
> 
Is the whole sentence unique, or just the last part?
To be precise, only the middle part is unique :-p
it always begins with the same string end ends with the same string.

"a"sqdjvilkshnv(several lines) "b"
cdcdvsvdvc
vcwvvvcvcv
"a" blabla(several lines) "b"

returns
"a"sqdjvilkshnv(several lines) "b"
"a" blabla(several lines) "b"

so....it starts at "a" and as soon as it reaches "b" (for the first time) it ends (and searches along for the second "a" and so on.....)

i hope i was a little more clear now....

thx



M.

---

### Post by cgroza on 2011-09-01
I don't know if this idea is usable in your case, but why don't you read the whole file in a string and then split it on ".".

This way, will obtain a list of sentences in the file.

---

### Post by David Andersson on 2011-09-01
> **Michaël-D said:**
> actually my problem is the following, the full string i would like to copy a 'sentence' that is longer then one line (so it continues on the next one).
after the full sentence i'm looking for there is a blank line, 

What if you re-phrase the problem from "lines" to "paragraphs". 

That is; find and output paragraphs that contains a certain string. Such a program would be easier to make, and less buggy because of less complexity, and the chance that a sentence happens to be longer than 3 lines.

Define a function that reads paragraphs. Either this one

```

def read_paras(f):
    while True:
        while True:  # read empty lines
            line = f.readline()
            if not line:        # eof
                return
            if not line.isspace():
                break

        para = line
        while True:  # read non empty lines
            line = f.readline()
            if not line:        # eof 
                yield para
                return
            para += line
            if line.isspace(): 
                yield para
                break

```

or be inspired by readparagraphs() on [http://code.activestate.com/recipes/408995-a-general-purpose-file-iterator-class/](http://code.activestate.com/recipes/408995-a-general-purpose-file-iterator-class/)

Call it like this

```

for line in read_paras(a):
    if "string i'm looking for" in line:
        b.write(line)

```

_A note about memory efficiency_

The readlines() function reads all lines into an array at once. The whole file is in memory. An advantage with read_paras() and readparagraphs() is that they at most keep one paragraph in memory at any time. The remainder of the file is read when needed.

If you still want to pursuit a line oriented solution, you can use "for line in a:" instead of "for line in a.readlines():" to read lines from the file one at a time.

---

### Post by ofnuts on 2011-09-02
Splitting the files in lines is fairly artificial given the problem. It would be a lot more efficient to read it in whole, and apply regular expressions on that...

Finding a string that starts with "something" and getting that line and the three lines before should be something like
```

([^\n]*\n){3}Something[^\n]*

```Ie:

[LIST]
[*]A bunch of characters that aren't newlines, and a newline, three times (ie three lines...)
[*]followed by a line that starts with "Something" (because it is right after a newline) followed by a bunch of characters tat aren't newlines (ie all chars up to the end of line, newline not included).
[/LIST]


Use as 're.findall(pattern,wholefilecontents)' and you get an array with all your results...

---

### Post by Michaël-D on 2011-09-03
> **David Andersson said:**
> What if you re-phrase the problem from "lines" to "paragraphs". 

That is; find and output paragraphs that contains a certain string. Such a program would be easier to make, and less buggy because of less complexity, and the chance that a sentence happens to be longer than 3 lines.

Define a function that reads paragraphs. Either this one

```

def read_paras(f):
    while True:
        while True:  # read empty lines
            line = f.readline()
            if not line:        # eof
                return
            if not line.isspace():
                break

        para = line
        while True:  # read non empty lines
            line = f.readline()
            if not line:        # eof 
                yield para
                return
            para += line
            if line.isspace(): 
                yield para
                break

```or be inspired by readparagraphs() on [http://code.activestate.com/recipes/408995-a-general-purpose-file-iterator-class/](http://code.activestate.com/recipes/408995-a-general-purpose-file-iterator-class/)

Call it like this

```

for line in read_paras(a):
    if "string i'm looking for" in line:
        b.write(line)

```


thx,
your solution almost did the trick...
except for the fact that it copies the whole paragraph containing the string instead of just copying from where the string is found till the end of the paragraph,
do you think you could make that happen? :)

regards,

M.

---

### Post by cgroza on 2011-09-03
> **Michaël-D said:**
> thx,
your solution almost did the trick...
except for the fact that it copies the whole paragraph containing the string instead of just copying from where the string is found till the end of the paragraph,
do you think you could make that happen? :)

regards,

M.
Or you could tweak it yourself.

---

### Post by Michaël-D on 2011-09-03
> **cgroza said:**
> Or you could tweak it yourself.

that's what i would say as well but i really can't figure it out, 
if someone could put me on the right track i'll try figuring it out myself (i'm quite a beginner)

---

### Post by David Andersson on 2011-09-08
> **Michaël-D said:**
> ... just copying from where the string is found till the end of the paragraph,


String objects have methods that search for a substring and return the position of it if they find one. Use that position to slice the string. Look for the string methods *find* and *index*.

---

