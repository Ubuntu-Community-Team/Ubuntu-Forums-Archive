---
title: "Python: invoking next line in short hand loops"
date: 2010-05-12
forum: Programming Talk
---

### Post by anlag on 2010-05-12
Hope that title isn't completely insane...

If I'm looping through, say, lines in a files or elements in an array, I can easily do it with something like

for line in file:
   pieces=line.split()
   print pieces[0]

...etc, whatever I want to do with it. My question: is there a way in this short hand syntax to perform an operation on the *next* line/element? So, to access "line+1". This for instance doesn't work:

for line in file:
   print line
   print line+1

...which is no surprise, but can it be done in a similarly convenient manner? I can of course instead determine the length of the file/array and loop over it with numerical indices, but the short hand notation is quite nice and I just thought I'd ask if there's a way to use it for this.

---

### Post by Reiger on 2010-05-12
As far as I can see: I don't think there will be because the abstraction has a massive "leak" there:

Files are presented as iterable collections of lines of text, but in actual fact streamed to the application so at any point in time you only have the most current buffer (line) to work with.

The only way to do what you want is (a) store lines in a bigger structure and do the look up after reading the data into that structure; (b) use more flow control (assuming Python sports the continue statement).

---

### Post by ssam on 2010-05-12
there are a few methods depending on what you want to do. if you want to always go forward, but sometimes grab 2 lines (or more) lines in the same loop do something like:

```

fh = open(FILENAME)

while True:
  try:
    line = fh.next()
  except StopIteration:
    break # stop at end of file

  print line
  if line.startswith('x'):
    print "next", line.next()

```
will print out the lines. if a line starts with an 'x' then print the next line too. using next will always move the position through the file, the *next line* will not be the *line* next time around the loop.

Another example when you just want the last line is to store it and overwrite it each time.

```

last_line = ""
for line in file:
  print line, last_line
  ...
  last_line = line

```

for more complex situations you may have to read everything into a list:
```

lines = file.readlines()

for x in xrange(lines):
  line = lines[x]
  nextline = lines[x+1]
  lastline = lines[x-1]

```
but beware of memory usage, and index errors.

---

### Post by trent.josephsen on 2010-05-12
Python doesn't provide a built-in way to do what you're asking, I imagine because it would make optimization of the loop much more complicated to do well (i.e., you're no longer dealing with just one item at a time, so Python will have to keep all of them accessible instead of just the one).

However, if you are iterating over an iterator, you can call the .next() method to get the next item.  However, using this method will cause the for loop to skip that item entirely.  You can use this technique to deal with things in twos.  You could also keep track of the index yourself (starting at 0 and incrementing each iteration), using it only when necessary.

Of course, you can always use continue to skip the rest of the current iteration and go to the next.  Or save the current value of the iterator at the end of the loop so it's available in the next iteration.

I guess what I'm trying to say here is that it all depends on what you're trying to do.  Code would help us recommend a solution.

---

### Post by anlag on 2010-05-12
Thanks for the replies! I opted for rewriting the loop so that it each time worked with what it read from the previous line, and then ended with saving the current line again for the next loop.

Just to illustrate I'll paste the code, though it might be a bit hard to get an overview of since it's quite out of context here. But, where it used to apply its operations to *line*, I now have it work mainly with *lastline* and only use *line* when requiring something from the line below. If that makes sense. :-)

```
for line in file:
    if 'sieged' in lastline or 'attacked' in lastline or ') pillaged' in lastline:
        lspl=lastline.split()

        name=lspl[3]
        mid=lspl[4].split('\'')[0]
        defender=name+' '+mid

	name=lspl[0]
        mid=lspl[1]
	attacker=name+' '+mid
		
	if ') pillaged' in lastline:
	  if len(line) < 5:		# break loop if line=blank (block, nothing killed)
	    lastline=line
	    continue
	  nspl=line.split()
	  if nspl[2]=='killed':		# break loop if blocked
	    lastline=line
	    continue

        cnt.setdefault(defender,[]).append(attacker)
        cnt2.setdefault(attacker,[]).append(defender)
        
    lastline=line
```

---

### Post by StephenF on 2010-05-12
The itertools module has a couple of useful items.
```

from itertools import tee, izip

f = open("testfile", "r")
i1, i2 = tee(f) # Two iterators on the file.
i2.next() # This puts one iterator out of step.
for current, following in izip(i1, i2):
    # Indicate which iterator is sourcing the data.
    # The newline character is not printed.
    print "C ", current[:-1]
    print "F ", following[:-1]

f.close()
```
testfile:
```

First
Second
Third
Fourth
Fifth
Sixth
Seventh
Eighth
Ninth
Tenth
```
Output:
```

C  First
F  Second
C  Second
F  Third
C  Third
F  Fourth
C  Fourth
F  Fifth
C  Fifth
F  Sixth
C  Sixth
F  Seventh
C  Seventh
F  Eighth
C  Eighth
F  Ninth
C  Ninth
F  Tenth
C  Tenth
F
```

---

