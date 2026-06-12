---
title: "[SOLVED] Changing files with python"
date: 2008-09-03
forum: Programming Talk
---

### Post by cardboardtoast on 2008-09-03
Hi,

I have been trying to figure out how to remove lines in a text file, but can't figure out how...

ie- if I have this:
    
   line1here
   line2here
   line3here

I am trying to remove, say, line 2 in the file, and place an edited line2 at the end of the file like this:

   line1here
   line3here
   newline2here

How do I do this?

If it involves creating a new file(must have the same name), then how do I delete the old one?

Thanks!:popcorn:

---

### Post by damoxc on 2008-09-03
Something like this would do the trick

Of course you might want to do a little more checking than just a line index on which one to remove.

```
#!/usr/bin/python

lines = open('file').read().splitlines()
del lines[1]
open('file', 'w').write('\n'.join(lines))

```

That help at all?

---

### Post by ghostdog74 on 2008-09-03
for big files you do not have to read all into memory. The basic way is to print to stdout what you want, and don't print what you don't want
```

for num,lines in enumerate(open("file")):
 if num==1: continue #skip line 2
 print lines.strip()
print "last line"
 

```
and on command line:
```

# python script.py > newfile ; mv newfile file

```
you can also use the fileinput module to edit files in place, but i leave it to you to find that out yourself

---

### Post by cardboardtoast on 2008-09-03
damoxc:  Unfortunatly, that seems to have the same problem as I am having:

when I go look in the file, I see this:

line1here
line2here
line3here
newline2here

leaving the old line 2 in the text file..

ghostdog74: ah, I am looking to change the file in place, and have spent the last 20 min staring at the fileinput module description...

> Optional in-place filtering: if the keyword argument inplace=1 is passed to input() or to the FileInput constructor, the file is moved to a backup file and standard output is directed to the input file (if a file of the same name as the backup file already exists, it will be replaced silently). This makes it possible to write a filter that rewrites its input file in place. If the keyword argument backup='.<some extension>' is also given, it specifies the extension for the backup file, and the backup file remains around; by default, the extension is '.bak' and it is deleted when the output file is closed. In-place filtering is disabled when standard input is read. 
so far I've gotten this:
[php]
import fileinput
badline = 'line2here'
for line in fileinput.input('file.txt',inplace=1):
    if line == badline:
        ###What goes here?
[/php]
(the loop is because 'line2here' is not always on line 2 of the file)

But what goes there???? (look in code)

Thanks:popcorn:

---

### Post by ghostdog74 on 2008-09-03
> **cardboardtoast said:**
> 

ghostdog74: ah, I am looking to change the file in place, and have spent the last 20 min staring at the fileinput module description...


so far I've gotten this:
[php]
import fileinput
badline = 'line2here'
for line in fileinput.input('file.txt',inplace=1):
    if line == badline:
        ###What goes here?
[/php]
(the loop is because 'line2here' is not always on line 2 of the file)

But what goes there???? (look in code)


Thanks:popcorn:

because you want to skip bad lines, you should just do a continue, or use not
```

for line in fileinput.input('file.txt',inplace=1):
  if not badline in line: print line.strip()
  # if badline in line : continue

```
just use the the print statement, and let fileinput do the inplace edit.

---

### Post by cardboardtoast on 2008-09-03
```

for line in fileinput.input('mtgcollection.txt',inplace=1):
    if not newcardlist.split('_')[0] in line.split('_')[0]:
        print line.rsplit()
fileinput.close()
```
why is this always printing lists and not strings??? (and then a list of the list, of that list, of that list, etc, until theres more brackets than writing)
ie:
['["[\'10th - wolf - 7\']"]']
['["[\'eventide - boggart - 9\']"]']
['morningtide - goblin - 5']

^ick!

---

### Post by ghostdog74 on 2008-09-03
show your input file, and describe what you want to see as output.

---

### Post by cardboardtoast on 2008-09-03
> **ghostdog74 said:**
> show your input file, and describe what you want to see as output.

Ok, heres the input file:
> eventide-boggart_9
morningtide-goblin_5
10th-wolf_7
morningtide-murmuring bosk_1


if I say morningtide-goblin_3, it should output with the goblin's 5 getting +3:

> eventide-boggart_9
morningtide-goblin_8
10th-wolf_7
morningtide-murmuring bosk_1


and if I add a completely new one ie- new-creature_3:
It should put out:
> eventide-boggart_9
morningtide-goblin_8
10th-wolf_7
morningtide-murmuring bosk_1
new-creature_3


The brackets "[]" added by the inputfile code trips up the code somehow (entries begin dissapearing from the file)...

Thank you for taking the time to help me :)

---

### Post by ghostdog74 on 2008-09-03
the brackets "[" and "]" are for lists. To join lists to become a string, use join()
eg
```

alist=["one,"two","three"]
print ' '.join(alist)

```

---

### Post by cardboardtoast on 2008-09-04
> the brackets "[" and "]" are for lists. To join lists to become a string, use join()
eg
Code:

alist=["one,"two","three"]
print ' '.join(alist)

ah, I had the .join in the wrong place...

THanks, that got it!:popcorn:

---

