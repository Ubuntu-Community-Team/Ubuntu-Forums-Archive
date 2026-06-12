---
title: "Python - replace a line in a file?"
date: 2006-12-07
forum: Programming Talk
---

### Post by Tomosaur on 2006-12-07
Hi guys, maybe someone can help me out. I need to do a search and replace on text in a file, but I'm having some difficulty. If the replace string is shorter than the found string, then all of the characters are not replaced. Here's an example:

Original text:
```

goodbye
hello
see you later!

```

Search for "hello", replace with "hi":
```

goodbye
hillo
see you later!

```

Basically, the trouble is that I can't seem to flush out the rest of the line. Please note that I'm actually trying to write this to the file, rather than just print out the replaced text. Is there no other way to do this than to overwrite the entire file with the modified text?

---

### Post by maubp on 2006-12-07
What does your code look like?

>>> text = """goodbye
hello
see you later!"""
>>> print text
goodbye
hello
see you later!
>>> print text.replace("hello","hi")
goodbye
hi
see you later!

---

### Post by Tomosaur on 2006-12-07
Not like that :P

I want it to _write_ the modified text to a file. The original file looks like the first example in the OP, and the modified file looks like the second. Everything works, except I don't know how to get rid of the redundant characters. If I use the file.write(text) method, then the file gets replaced completely, whereas if I use the file.writelines(text) after seek() ing to the right position, then characters are only overwritten rather than the entire line being replaced, which is what I need to do. All I need is confirmation of whether this is possible, or whether I need to buffer the entire file and overwrite it.

---

### Post by maubp on 2006-12-07
Oh. I should try and read more carefully.  Sorry.

If the search and replace strings are the same length, then yes, you should be able to edit the file in read/write mode by moving to the correct location with seek, and overwritting the old text.  This should be fast on big files.

I'm almost 100% sure that if the search and replace strings are different lengths, you can't do an in place update to the file.

The simple solution is to load the entire file into memory as a string, edit the string, and re-write the entire file.

---

### Post by Tomosaur on 2006-12-07
Ok, thanks, I'll do that then :)

---

### Post by Ramses de Norre on 2006-12-07
Sed is probably better at this than python.

```
#!/bin/bash
sed -i -e 's/hello/hi/g' $1
```

Give the filename as argument to the script when launching.

EDIT: it works indeed better with the -i option (as mentioned below)

---

### Post by ghostdog74 on 2006-12-07
Python alternative:
```

#!/usr/bin/python
import fileinput
for lines in fileinput.FileInput("inputfile", inplace=1): ## edit file in place
    lines = lines.replace("hello","hi")
    print lines ## although this prints the line, the file will be modified.

```

---

### Post by Tomosaur on 2006-12-07
I wish you guys would read more :P
I'm not trying to print the altered lines, I'm trying to write the modified line into the file.

It's ok now anyway, got it sorted.

---

### Post by Arndt on 2006-12-08
> **Tomosaur said:**
> I wish you guys would read more :P
I'm not trying to print the altered lines, I'm trying to write the modified line into the file.

It's ok now anyway, got it sorted.

Note that several tools have the ability to do editing "in place". The 'sed' solution is fine if you also supply the -i option. Perl also has that option.

"In place" is not literally in place, which you tried to do, but writing to a temporary file and then renaming it. This is a good idea also when programming the code oneself, since what the user most often expects if the operation fails in the middle is to be told about it, and have the original file as it was.

---

### Post by Shay Stephens on 2006-12-08
> **Tomosaur said:**
> It's ok now anyway, got it sorted.

You could help others by mentioning how you got it to work.

---

### Post by Tomosaur on 2006-12-08
Well, since what I actually need to do is to replace multiple lines in the file, I used the following method:
```

mod = []
try:
  file = open("/path/to/myfile", "r")
  for line in file:
    mod.append(line)
  file.close()
except IOError:
  print "Couldn't open file"

```
I then did my regex matching on the mod array, before commiting back to a file using
```

try:
  file = open("/path/to/myfile", "w")
  file.writelines(mod)
  file.close()
except IOError:
  print "Couldn't save file"

```

The reason I open the file twice rather than opening it just once with r+ (read and write), is because the program's inital state is decided by the file. Modifications to it are optional, and it isn't worthwhile keeping it hanging around unless the user changes stuff.

Also note, that isn't my actual code, since I have a bunch of other stuff which is app-specific.

---

### Post by ghostdog74 on 2006-12-08
> **Tomosaur said:**
> 
```

mod = []
try:
  file = open("/path/to/myfile", "r")
  for line in file:
    mod.append(line)
  file.close()
except IOError:
  print "Couldn't open file"

```


the above can be done using:

```

...
mod = open("/path/file").readlines()
...

```

Just FYI.

---

### Post by Tomosaur on 2006-12-08
Sweet, thanks :)

---

