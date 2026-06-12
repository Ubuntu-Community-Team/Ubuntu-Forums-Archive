---
title: "Python - fastest way to remove ASCII &gt; 128 from string?"
date: 2010-05-01
forum: Programming Talk
---

### Post by s1ightcrazed on 2010-05-01
OK, 

I've got a database conversion app that I've been working on, and part of what it needs to do is to remove ASCII characters that are above ord(128), or equal to ord(26). I do this through a scrub routine, and I've found through profiling that, as expected, this routine is very expensive. 

I've tried 2 different methods: 

through a join with a constructor (reasonably fast):

```
for line in table:
        scrubbed_line=scrubbed_line.join([x for x in line if ord(x) < 128 and ord(x) != 26]) 
```

and through an iterator (kinda not so fast):

```
for line in table:
	scrubbed_line=""
	for i in range(len(line)):
		if ord(line[i]) < 128 and ord(line[i]) != 26:
			scrubbed_line+=line[i] 
```

I'm wondering if there is another (faster) method that I've missed. These two are the only ones that I could come up with. 

Any ideas?

---

### Post by azagaros on 2010-05-01
from what you state an optimizer isn't in python's interpreter. 

In the second version move the two function calls in the for statement out to variables before the for statement.  That should speed it up.  The speed issue is it calls the two functions every time the loop runs and they are fixed numbers for each loop.

The method of doing what you are doing is what we have done for years in many programming languages.  The second form is more like we do it in other programming languages.

---

### Post by StephenF on 2010-05-01
Maybe the regular expressions module, re, can help?

Also,
> ```
for line in table:
        scrubbed_line=scrubbed_line.join([x for x in line if ord(x) < 128 and ord(x) != 26])
```

This could probably read:
```

for line in table:
        scrubbed_line = "".join(x for x in line if ord(x) < 128 and ord(x) != 26)

```

By placing square brackets you are creating and copying to a list which must then be iterated over again by join. Much better to just pass the generator because it's a lot faster.

---

### Post by s1ightcrazed on 2010-05-01
I looked into re, but I couldn't find a way to have it search within a string for an ASCII value. 

azagaros: You are right, moving the ord() calls to a function did speed it up, but only by about 10%. 

I found a third way, using the array module:

```
for line in table:
	fixed_array=array.array('B', '')
	orig_array=array.array('B', line)
	fixed_array.extend([x for x in orig_array if x < 128 or x != 26 ])
	newline=fixed_array.tostring()
```

This is similar to my first attempt, and uses the same constructor, but is nearly 40% faster. 

I might be getting closer to what I would consider usable, if not perfect. When iterating over a database that has 10.2 million rows, every millisecond counts. 

My next move might be to break this out into pure C....but I hate C. ;)

---

### Post by ratcheer on 2010-05-01
I am not a Python programmer, but if Python can call Linux commands, it would be a very simple matter to call ***tr*** (for translate) and remove 128 characters with excellent performance.

Tim

---

### Post by s1ightcrazed on 2010-05-01
StephenF - I hadn't even noticed the brackets. That generator was cut and pasted from another project of mine, and I guess I should pay better attention. Removing the extraneous 'listing' inside the generator knocked off another 15 - 20 %. 

So, with the latest changes...:

randall@randall-laptop:~/Documents/projects/code$ ./speed_test.py
testing bad chr stripping - join method
Converted 8064 lines in: 0.680312871933. 11853.3697254 per second.
testing bad chr stripping - iterate method
Converted 8064 lines in: 1.57627010345. 5115.87448263 per second.
testing bad chr stripping - array method
Converted 8064 lines in: 0.579920053482. 13905.364975 per second.

So, I'm pretty happy with almost 14,000 rows per second. The database can't even insert 14,000 rows a second, so this removes the scrub from being a bottleneck in the conversion. 

Many thanks.

---

### Post by StephenF on 2010-05-02
> **s1ightcrazed said:**
> 
```
fixed_array.extend([x for x in orig_array if x < 128 **or** x != 26 ])
```
or -> and

---

### Post by s1ightcrazed on 2010-05-02
Good catch. ;)

---

### Post by trent.josephsen on 2010-05-02
> **s1ightcrazed said:**
> I looked into re, but I couldn't find a way to have it search within a string for an ASCII value.
```
>>> import re
>>> p = re.compile(r'[^\x00-\x19\x1B-\x80]*')
>>> def scrub(string):
...     return p.sub('', string)
... 
>>> scrub('\x04\x99\x14hello, world\x00\x90\x81\x11\x1A')
'\x04\x14hello, world\x00\x11'

```

---

### Post by StephenF on 2010-05-02
> **trent.josephsen said:**
> ```
>>> import re
>>> p = re.compile(r'[^\x00-\x19\x1B-\x80]*')
>>> def scrub(string):
...     return p.sub('', string)
... 
>>> scrub('\x04\x99\x14hello, world\x00\x90\x81\x11\x1A')
'\x04\x14hello, world\x00\x11'

```
Nice. This is easily the fastest of the methods I have tried so far. I noticed this does not strip character 128 which seems to be the requirement despite the thread title. In my test it takes 25% less time than array.array which is not too surprising since the stripping operation takes place entirely in C land.
```

import re

def resub_factory(name, pattern):
    p = re.compile(pattern)
    def sub(string):
        return p.sub('', string)
    sub.__name__ = name
    return sub

db_cleaner = resub_factory('db_cleaner', r'[^\x00-\x19\x1B-\x7F]*')

```
```

for line in table:
    new_line = db_cleaner(line)

```

---

### Post by ShadowRanger on 2011-04-29
For anyone who reads this, please ignore the ridiculous solutions above. Python has always had an efficient way of doing this that apparently no one here noticed.

In Python 2:
```

import string
# Create a string with all single byte characters (only done once)
nochangetable = string.maketrans('', '')
# Create a string with the characters you want removed (only done once)
deletethese = nochangetable[26] + nochangetable[128:]
for line in whatever:
    # Strip all the bad characters from line blazingly fast
    line = line.translate(nochangetable, deletethese)
    # do stuff with the newly stripped line

```str.translate (which is the main worker function here) is doing the same thing as the UNIX tr utility, it's just integrated into Python and coded directly in C. It runs *much* faster than any solution involving hand-coded Python loops, because it processes the whole string at once with no interpreter overhead. In brief tests with timeit, I got a speedup of ~25x versus any of the solutions here. No need for regular expressions, no complicated code. It's been a str builtin forever. In Python 3, the only change is that you'll want to work with bytes, not strs, and the maketrans method is defined directly on the bytes and str classes, not in the string module.

---

