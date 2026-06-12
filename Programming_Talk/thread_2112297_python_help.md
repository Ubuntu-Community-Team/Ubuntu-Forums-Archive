---
title: "python help"
date: 2013-02-04
forum: Programming Talk
---

### Post by wingnut2626 on 2013-02-04
Hello all, I am working on a python script and this is what i have

```
from sys import argv

script, filename = argv

print "We're going to erase %r " % filename
print "If you don't want that, hit Ctrl -C (^C)."
print "If you do want that, hit RETURN."

raw_input("?")

print "Opening the file..."
target = open(filename, 'w')

print "Truncating the file. Goodbye!"
target.truncate()

print "Now I'm going to ask you for three lines."

line1 = raw_input("line 1: ")
line2 = raw_input("line 2: ")
line3 = raw_input("line 3: ")

print "I'm going to write these to the file."

file1 = line1 "\n" line2 "\n" line3 "\n"

target.write(file1)


print "And finally, we close it."
target.close()
```

What im trying to do is combine line1, line 2 and line 3 with the newlines into one variable to pass to target.write().  How do i do that so that I don't need to write 6 target.write() commands?

Thank you guys in advance for your assistance.  I really appreciate it!

---

### Post by ofnuts on 2013-02-04
```

file1 = '\n'.join([line1,line2,line3])

```
or 
```

file1 = '\n'.join([line1,line2,line3,''])

```
if you want a final linefeed.

---

### Post by wingnut2626 on 2013-02-04
thank you so much!  I dont know what i would do without you guys!

---

