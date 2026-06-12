---
title: "Python Help"
date: 2009-12-30
forum: Programming Talk
---

### Post by HalfEmptyHero on 2009-12-30
I am trying to write a script to help me format some text files that I have. The input would be a plain text file and the output would be a txt. What I want the script to do is: 
First: remove all blank lines from the files

Next: For each line in the file, write that line, and make it indented and add a blank line afterwords.

This is because the files I want to edit have random amounts of blank lines throughout it and I want to standardize this and also make them more like paragraphs. Here is my code so far:

```

import sys

arg_1 = sys.argv[1]
arg_2 = sys.argv[2]

input_file = open(arg_1, 'r')
output_file = open(arg_2, 'w')
running = True;

while running:
    for line in input_file:
        line = line.strip()
        if len(line) == 0:
            running = False
        elif line == '':
            continue
        else:
            output_file.write('\n')
            output_file.write('\t')
            output_file.write(line)

```

This works, except for adding the blank lines. But I can get the adding blank lines to work (without removing the random blank lines of course) by taking out the elif statement.

Any suggestions?

---

### Post by ghostdog74 on 2009-12-30
you can use 
```

if not line:
  # blah

```

---

### Post by The Cog on 2009-12-30
I would probably do the loop like this (untested):
```
for line in input_file.readlines():
    line = line.strip()
    if len(line) > 0:
        output_file.write('\t' + line + '\n\n')
```

If you don't use readlines(), you will read characters rather than lines.

You don't need a running flag in this case - the for loop will end when there are no more lines anyway

The double \n is: one for the end of the line that strip() removed, and one for the blank line you wanted afterwards.

I know they get closed when the program ends, but it would feel more "proper" to me if the two files were explicitly closed before letting the program run off the end. Not technically needed though.

P.S.
**if len(line) > 0:** can be shortened to **if line:**

---

### Post by McNils on 2009-12-30
First you have two statements that test the same thing.

```
if len(line) == 0
```
and
```
if line == ''
```

Second
your first loop  is unnessery.


Add a variable that keeps track of what if you wrote a line or skipped a empty line. when you write a empty you set it to as you skipped a line.

The genaral idea is something like this
```
if line == ''
    if !skipped
        print('')
    skipped = True
else
   print(line)
   skipped = False

```

---

### Post by DaithiF on 2009-12-31
Off-topic (ie. not python), but just for variety heres how to do this using another tool, sed:
```
sed '/./!d;s/^/\t/;G' somefile > newfile
```
(sometimes a 1-liner with the right tool can do what takes many lines in a more general purpose language)

---

### Post by The Cog on 2009-12-31
That reminds me of
```
sed '/./!d;s/^/\t/;G' NO CARRIER
```

---

### Post by ghostdog74 on 2009-12-31
> **DaithiF said:**
> 
(sometimes a 1-liner with the right tool can do what takes many lines in a more general purpose language)
I would read Python code that has "many lines" any time. "Short" code doesn't mean understandable code.

---

### Post by DaithiF on 2009-12-31
> **ghostdog74 said:**
> I would read Python code that has "many lines" any time. "Short" code doesn't mean understandable code.
Sure, sed syntax may not be particularly intuitive, and yes, one of pythons strengths is its clarity.  But still, for straightforward text-processing requirements like the OP raised, some combination of the common unix tools of grep / sed / awk / tr / cut, etc may be the better way to go, rather than rolling your own.  Personal choice of course, but for me I find the brevity of these tools quite elegant, and I don't (personally) find there to be a trade-off between their brevity and their understandability.

---

### Post by HalfEmptyHero on 2009-12-31
Excellent, thanks for all the help guys. One more thing though, I would also like to be able to check the file for 2 or more consecutive spaces and then change them into a single space. I was thinking:

```

multi_space = '  '
line = line.replace(multispace, ' ')

```

But that only removes 1 space. Could I somehow work in a while loop (in combination with The Cog's example) to check if there is a place with 2 spaces, or am I looking at this in the wrong way?

---

### Post by DaithiF on 2009-12-31
you could use a regular expression:
```
import re

line = re.sub('  +', ' ', line)

```

---

### Post by snova on 2009-12-31
> **The Cog said:**
> If you don't use readlines(), you will read characters rather than lines.

Iterating over a file object produces lines, not characters. The readlines() call is not necessary and, in the case of a large file, rather inefficient.

---

### Post by HalfEmptyHero on 2009-12-31
> **DaithiF said:**
> you could use a regular expression:
```
import re

line = re.sub('  +', ' ', line)

```

That worked perfectly, thanks.

---

### Post by ghostdog74 on 2009-12-31
> **HalfEmptyHero said:**
> That worked perfectly, thanks.

no need to use regex. Just split and join back with a space
```

>>> s="string with     many              spaces"
>>> ' '.join(s.split())
'string with many spaces'


```

also, even if you want to use regex, compile it first. 
```

pat=re.compile('  +')

```

---

### Post by HalfEmptyHero on 2009-12-31
Sweet, that works too. I think I understand what it is doing, please correct me if I am wrong. .split() takes the string and separates the words from everything else, thus removing the spaces. Then ' '.join() puts this words together, with a space separating. Correct?

Also, how does one go about learning python, beyond the beginner? So far I have read through A Byte of Python and, while it is a very good tutorial, it is very basic.

---

### Post by The Cog on 2010-01-01
> **snova said:**
> Iterating over a file object produces lines, not characters. The readlines() call is not necessary and, in the case of a large file, rather inefficient.

Doh! 
Thanks for sorting my head out.

---

### Post by HalfEmptyHero on 2010-01-04
Now I've got a new problem with a different script I am writing to count the number of words, sentences, and lines in a document or string. This is what I have so far:

```

#!/usr/bin/env python

example = open('example.txt', 'r')
#example = "This is a string."
def wCount(x):
    count = 0
    if isinstance(x, str):
        x = x.split()
        for item in x:
            count += 1
    elif isinstance(x, file):
        for line in x:
            line = line.strip()
            if line:
                line = line.split()
                for item in line:
                    count += 1
    else:
        print 'Unknown data type for input file.'
    print count, 'words.'
#wCount(example)

def lCount(x):
    count = 0
    if isinstance(x, file):
        for line in x:
            line = line.strip()
            if line:
                count += 1
    elif isinstance(x, str):
        count = x.count('\n')
    else:
        print 'Error Message'           
    print count, 'lines.'
#lCount(example)

def sCount(x):
    count = 0
    for line in x:
        if line:
            count += line.count('.') + line.count('?') + line.count('!')
            ellipsis = line.count('... ')
            nailbiter = line.count('....')
            count -= ellipsis * 3
            count -= nailbiter * 3
    print count
sCount(example)
wCount(example)
lCount(example)

```

This works if I only want to use one of the functions, however if I want to use more than one it won't work because of the changes the previous function made to it. Is there any way to 'Undo' the changes that are made to a string or file, besides closing the file and reopening it?

---

### Post by akvino on 2010-01-04
> **DaithiF said:**
> Off-topic (ie. not python), but just for variety heres how to do this using another tool, sed:
```
sed '/./!d;s/^/\t/;G' somefile > newfile
```
(sometimes a 1-liner with the right tool can do what takes many lines in a more general purpose language)

DaithiF can you explain your one liner.... I am more interested in why use !d  than the rest, but it would be helpful to understand it all.

---

### Post by DaithiF on 2010-01-04
> **akvino said:**
> DaithiF can you explain your one liner.... I am more interested in why use !d  than the rest, but it would be helpful to understand it all.
sure:
```
/./!d
```
/./ would match a line which begins with any character.  Adding ! after the match expression negates it ... so /./! matches lines which **don't** begin with 'any character' ... the only lines which don't begin with 'any character' are blank lines.  An equivalent (without the negating) would be /^$/.  And of course 'd' deletes what has been matches (and also triggers the start of a new cycle for sed, so the subsequent expressions don't get executed on this line).

```
s/^/\t/

```matches the start of lines (^) and inserts a tab character (in order to indent)

```
G

```The sed G command appends a newline and the contents of the hold buffer onto the pattern space.  Since we haven't put anything into the hold buffer it is empty, so we're effectively just adding a newline character after each line.  (Theres a famous sed 1-liner to double-space a file ... *sed G filename*)

The ; characters between each piece chain these commands together sequentially.

---

### Post by DaithiF on 2010-01-04
> **HalfEmptyHero said:**
> This works if I only want to use one of the functions, however if I want to use more than one it won't work because of the changes the previous function made to it. Is there any way to 'Undo' the changes that are made to a string or file, besides closing the file and reopening it?
You haven't actually changed the file, you've just read it.  When a file has been read you need to reposition the pointer to the beginning of the file if you want to read it again 
so you could add 
```
example.seek(0)

```before the 2nd and 3rd function calls.
I won't risk going off-topic a second time by mentioning *wc*  :)

---

### Post by HalfEmptyHero on 2010-01-04
Thanks a bunch.

---

