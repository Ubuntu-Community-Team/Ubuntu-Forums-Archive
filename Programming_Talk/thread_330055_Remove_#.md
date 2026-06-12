---
title: "Remove #"
date: 2007-01-02
forum: Programming Talk
---

### Post by christhemonkey on 2007-01-02
Evening,

I am writing a script that parses a configuration file and my problem is this,

I want to get sed to delete a # if it finds one on lines containing an expression "foo".
The "foo" wants to be replaced with a "bar" also, just to simplify things :D

I know that if i want to delete all lines starting with a #:
```
sed '/^\#/d' 
```

Or replace something with something else if it containing another thing:
```
 sed '/baz/s/foo/bar/g' 
```

I just need to sort of combine the two...

After much googling i am still unable to find a solution!
The documentation on sed seems to leave me even more perplexed than before...

So any help greatly appreciated.

---

### Post by tomchuk on 2007-01-02
Something like this should work for removing a '#' from lines with 'test' in them:
```

sed 's/^\#\(.*test.*\)/\1/g'

```

---

### Post by pmasiar on 2007-01-02
This is why I like python: 

```
for line in open("file.name"):
    if line.startswith('#'):
        if line.index('foo') > -1:
             # your magic here 
```

---

### Post by christhemonkey on 2007-01-03
In matter of fact this is in a python script, but i couldnt think of a way of changing one line (of a position that varies) in a file so it is uncommented.

So was just cheating my way round calling commands.getoutput("sed bla").

---

### Post by pmasiar on 2007-01-03
> **christhemonkey said:**
> I but i couldnt think of a way of changing one line (of a position that varies) in a file so it is uncommented.

Read file, rename it (backup), write all lines to new file (named as original) and change lines you need. As side effect, you have original file too. :-)

---

### Post by christhemonkey on 2007-01-03
But i couldnt think of a way of only changing one line which is of indefinite position?

```
config_file = open(file)
while True:
        line = config_file.readline()
        if line.__contains__("foo"):
                line.somereplacefunctionorother("foo", "bar")
                line.strip("#")
                config_file.write(line+alltherestofthefile...)
                break

```

Obviously this example wouldnt work but you might catch the drift of what im trying to do.

---

### Post by pmasiar on 2007-01-03
Your code reads like C :-) Without diving into file handling/renaming etc

```
for line in open("file.name"):
    changed = ""
    if line.startswith('#'):
        if line.index('foo') >-1:
             # your magic here
             changed = line.replace('foo', 'bar')
    if changed:
        print changed
    else:
        print line     
```    

when runing, redirect output to a file, like: python prog.py >file.new

---

### Post by christhemonkey on 2007-01-03
Or, on further reading, i could use the string module and just do this:

```
import string

config = open(config_file, "rw")
new_config = string.replace(config, "foo", "bar")
config.write(new_config)
config.close()

```

Something like that?

---

### Post by pmasiar on 2007-01-03
Do you want also to uncomment a line? Or make sure you changing only lines which are not commented? Your last solution does neither.

---

### Post by ghostdog74 on 2007-01-03
```

import fileinput
for line in fileinput.FileInput("file.name", inplace=1): #do inplace editing..
    if line[0] == '#' and "foo" in line:
         line = line.replace("foo","bar")
         print line

```

---

### Post by fadder on 2007-01-03
Here's a perl solution (don't know how to keep indents, sorry..):

while(<>){                                  # Loops over standard input
 if (/^# .* foo .*/x) {
                s/foo/bar/;
                s/^#//;
        }
        print;
}

---

### Post by christhemonkey on 2007-01-03
Ok, ignore the removing of #'s sorted that with another function.

Just need to know how to replace foo with bar on a random line.


> import fileinput
for line in fileinput.FileInput("file.name", inplace=1): #do inplace editing..
    if line[0] == '#' and "foo" in line:
         line = line.replace("foo","bar")
         print line
This sounds like what i want, but i want to save this change to file which im not sure this does...

---

### Post by pmasiar on 2007-01-03
Google is your friend:

[http://pydoc.org/2.4.1/fileinput.html](http://pydoc.org/2.4.1/fileinput.html)

Optional in-place filtering: if the keyword argument inplace=1 is passed to input() or to the FileInput constructor, the file is moved to a backup file and standard output is directed to the input file. This makes it possible to write a filter that rewrites its input file in place.  If the keyword argument backup=".<some extension>" is also given, it specifies the extension for the backup file, and the backup file remains around; by default, the extension is ".bak" and it is deleted when the output file is closed.

This is why I love python - often used functionality is neatly packed, ready to be used.

Thanks ghostdog74, I learned another neat library function.

---

### Post by ghostdog74 on 2007-01-03
> **pmasiar said:**
> 
Thanks ghostdog74, I learned another neat library function.

No problem:)

---

