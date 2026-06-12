---
title: "Python - Remove empty lines from text file"
date: 2006-11-19
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-19
Hey all

Yet another Python related question (sorry about this). Basically I would like to know if it is possible to search through a text file and remove empty lines without damaging the rest of the content. I have a function that reads through a file and assigns variables in a predefined order based on the lines in the file. If it encounters a blank line then the whole order gets messed up. 

I have only just started learning about reading and writing to files today so I am really not sure how to approach this.

Thanks

Ironfistchamp

---

### Post by po0f on 2006-11-19
ironfistchamp,

```

# Get file contents
fd = open(file)
contents = fd.readlines()
fd.close()

new_contents = []

# Get rid of empty lines
for line in contents:
    # Strip whitespace, should leave nothing if empty line was just "\n"
    if not line.strip():
        continue
    # We got something, save it
    else:
        new_contents.append(line)

# Print file sans empty lines
print "".join(new_contents)
```

---

### Post by DaveBorealis on 2006-11-19
This is essencially PoOf's method, but instead I treat the loaded file as one long string, which makes for a little briefer coding by getting the job done in three lines. Also, rather than reading in a file, I assigned a string with multiple '\n' to keep the example simple:
```
#!/usr/bin/env python
old_string = """two tabs:

three tabs:

space tab space tab:
         
emtpy line:

"""
new_string = ''
for line in old_string.split('\n'):
        if line.strip():
                new_string += line + '\n'
print old_string,
print new_string,

```

---

### Post by ghostdog74 on 2006-11-19
```

#!/usr/bin/python
import fileinput
for lines in fileinput.FileInput("test.txt", inplace=1): 	
 	lines = lines.strip()
 	if lines == '': continue
 	print lines

```

---

### Post by tomchuk on 2006-11-19
And with a list comprehension:
```

f = open('test.txt')
l = [l for l in f.readlines() if l.strip()]
f.close()
print l

```

---

### Post by DaveBorealis on 2006-11-19
> **tomchuk said:**
> l = [l for l in f.readlines() if l.strip()]
[/code]

Nice! :) 

The file has to be read in anyway, so check for 'if I.strip()' on the fly.

Now if the file is wanted in a list: 
mylist = l.split('\n')
can anyone  think of a way to merge that with tomchuk's single line?
(Not that it has to be...just playing around here!)

Dave

[edit]  Besides, this'll be a useful line (or two) to keep handy when processing text files.

---

### Post by ironfistchamp on 2006-11-20
wow lots of replies. Thanks very much I am going to get on with my coding once I get to college.

Thanks again

Ironfistchamp

---

### Post by Steveire on 2006-11-20
```

import re
f=open("somefile", "r")
fileString = f.read()
f.close()
processedString = re.sub("\n\s*\n*", "\n", fileString)
f=open("somefile", "w")
f.write(processedString)
f.close()

```

---

### Post by fadder on 2006-11-21
I couldn't resist this, but in perl I'd write:

#!/usr/bin/env perl
while(<>){
        print unless /^ \s* $/x;   
}

The above uses the conventions <> = standard input, ^ = start of line, $ = end, \s* = any number of whitespace characters.

(Could also add "open(IN,"<somefile");" first and then "while(<IN>)" if wanting to specify the file name.

Is there a similar way in python (Ive also just started trying to learn python)?

---

### Post by dwblas on 2006-11-22
In Python you could would use 
if each_line.isspace() :  --> returns one if it only finds whitespace characters, and zero otherwise.

---

### Post by Steveire on 2006-11-22
> **dwblas said:**
> In Python you could would use 
if each_line.isspace() :  --> returns one if it only finds whitespace characters, and zero otherwise.
```

print ''.join(line for line in open("somefile").readlines() if not line.isspace())

```

---

### Post by durand on 2008-05-07
Thanks for the code!

---

### Post by ssd.dan on 2010-03-13
Dear ironfistchamp,

Unless you are inclined to learn Python scripting, you could remove all the blank lines from a text file using vim by simply typing **:g/^\s*$/d** at the normal mode. ':g'=global command; '^'=the first character of a line; '\s'=space character; '*'=as many space characters; '$'=last character of the line; 'd'=delete command.

Best wishes,
ssd.dan (BTW, This is my first post in the forums)

---

