---
title: "Should-be-simple Python problem"
date: 2010-06-02
forum: Programming Talk
---

### Post by blazemore on 2010-06-02
Hi all; I'm teaching myself Python File IO so I can port a Java project I did to Python.

I've fallen at the first hurdle with file IO.
I want to read a file with filename "filename".
I want to store each line in an array.

I can do this, but at the end of every line is a newline character ('\n'), and it puts in a couple of random line breaks inbetween the lines.

I could probably parse it after and remove this excess noise, but this seems a bit hacky, and hacky is not what I'm going for.

What's the best way to read a file into an array?

ps the current method I'm using is
```

file   = open(filename, "r")
lines  = file.readlines()

```

---

### Post by rrashkin on 2010-06-02
I do:
```
lines=file.readlines().rstrip('\n')
```

---

### Post by raydeen on 2010-06-02
Depending on where your file is coming from, you might also want to check for any '\r' escapes. I was trying to write a script that would generate Google Groups .csv files from a Windows text file and couldn't figure out why I was still getting line breaks in OSX and Linux. Finally ran a visual output and saw the '\r' files which were Windows\DOS carriage returns. Sneaky sneaky sneaky.

---

### Post by trent.josephsen on 2010-06-02
The best way is probably to rewrite your handling code so that it ignores terminal newlines.  Barring that, use

```
lines = [l.rstrip() for l in open('filename')]
```

(rrashkin's suggestion accidentally calls rstrip on the entire list, which is not what you want.)

---

### Post by soltanis on 2010-06-02
Last example is the best (IMO) because list comprehensions are awesome. Also, you should open the file with:

```

open("filename", "U")

```

Using the "U" parameter turns on "universal newlines" which will get rid of those annoying Windows carriage returns ("\r") which can make your interpretation code choke.

---

### Post by blazemore on 2010-06-02
Can someone summarise for a newbie?

pseudocode:

filename = "foo.txt"
file = open_file(filename)
linelist = file.readLines()

I'd really appreciate this.

---

### Post by mo.reina on 2010-06-02
> **trent.josephsen said:**
> The best way is probably to rewrite your handling code so that it ignores terminal newlines.  Barring that, use

```
lines = [l.rstrip() for l in open('filename')]
```

(rrashkin's suggestion accidentally calls rstrip on the entire list, which is not what you want.)

using the above example:

```
lines = [l.rstrip() for l in open('foo.txt')]
```

---

### Post by blazemore on 2010-06-02
Thanks, I've abstracted this. It works perfectly:
```

import os.path

def fileToList(filename):
    lines = []
    if os.path.isfile(filename):
        lines = [l.rstrip() for l in open(filename, "U")]
    else:
        lines.append("Error reading file. File may not exist.")
    return lines

print fileToList("/home/james/test.lin")
print fileToList("/home/james/noexists.lin")

```

```

/usr/bin/python -u  "/home/james/Code/lsystem/lsystem/LSystem.py"
['45', 'xy', 'x:xxy', 'y:yxx']
['Error reading file. File may not exist.']

```

---

### Post by trent.josephsen on 2010-06-02
> **soltanis said:**
> Last example is the best (IMO) because list comprehensions are awesome. Also, you should open the file with:

```

open("filename", "U")

```

Using the "U" parameter turns on "universal newlines" which will get rid of those annoying Windows carriage returns ("\r") which can make your interpretation code choke.

I had no idea!  Thanks for the tip.

---

### Post by blazemore on 2010-06-08
I seem to be having real problems with this, maybe its because I'm coming from a Java background.
My code is as follows:
```
import os

class FileParser():
    
    def __init__(self, filename):
        self.validateFile(filename)
        return self.parseFile(filename)
    
    def validateFile(filename):
        if os.path.isfile(filename):
            print "File exists"
            return 1
        else:
            print "The specified file doesn't exist."
            print "Please check the name and try again."
            return 0
    
    def parseFile(filename):
        lines = []
        if os.path.isfile(filename):
            lines = [l.rstrip() for l in open(filename, "U")]
        else:
            lines.append("Error reading file. File may not exist.")
        return lines

print FileParser("/etc/fstab")
```

Here's the error:
> /usr/bin/python -u  "/home/james/Code/lsystem/lsystem/file_parser.py"
Traceback (most recent call last):
  File "/home/james/Code/lsystem/lsystem/file_parser.py", line 31, in <module>
    print FileParser("/etc/fstab")
  File "/home/james/Code/lsystem/lsystem/file_parser.py", line 11, in __init__
    self.validateFile(filename)
TypeError: validateFile() takes exactly 1 argument (2 given)

---

### Post by Bachstelze on 2010-06-08
Methods of Python classes generally take [font=monospace]self[/font] as first argument, so:

```
import os

class FileParser():
    
    def __init__(self, filename):
        self.validateFile(filename)
        return self.parseFile(filename)
    
    def validateFile(self, filename):
        if os.path.isfile(filename):
            print "File exists"
            return 1
        else:
            print "The specified file doesn't exist."
            print "Please check the name and try again."
            return 0
    
    def parseFile(self, filename):
        lines = []
        if os.path.isfile(filename):
            lines = [l.rstrip() for l in open(filename, "U")]
        else:
            lines.append("Error reading file. File may not exist.")
        return lines

print FileParser("/etc/fstab")
```

---

### Post by Tony Flury on 2010-06-09
> **Bachstelze said:**
> Methods of Python classes generally take [font=monospace]self[/font] as first argument, so:

```
import os

class FileParser():
    
    def __init__(self, filename):
        self.validateFile(filename)
        return self.parseFile(filename)
    
    def validateFile(self, filename):
        if os.path.isfile(filename):
            print "File exists"
            return 1
        else:
            print "The specified file doesn't exist."
            print "Please check the name and try again."
            return 0
    
    def parseFile(self, filename):
        lines = []
        if os.path.isfile(filename):
            lines = [l.rstrip() for l in open(filename, "U")]
        else:
            lines.append("Error reading file. File may not exist.")
        return lines

print FileParser("/etc/fstab")
```

As written this wont work - A constructor can't return anything.

Instead for your print to work define a __str__ method that returns a string version of your list

My version of your code - which does work : 
```

import os

class FileParser():
    
    def __init__(self, filename):
        self._filename = filename
        self.validateFile()
    
    def validateFile(self):
        if os.path.isfile(self._filename):
            print "File exists"
            return 1
        else:
            print "The specified file doesn't exist."
            print "Please check the name and try again."
            return 0
    
    def parseFile(self):
        lines = []
        if os.path.isfile(self._filename):
            lines = [l.rstrip() for l in open(self._filename, "U")]
        else:
            lines.append("Error reading file. File may not exist.")
        return lines

    def __str__(self):
        return str(self.parseFile())

print FileParser("/etc/fstab")

```

Ideally the constructor - should raise an exception if the file does not exist, rather than just print a message.

---

