---
title: "Python Looping question"
date: 2011-07-22
forum: Programming Talk
---

### Post by mikedemon on 2011-07-22
Hi

Is there way to copy the first word of each line using phyton with looping . Txt file will have many lines , Sample is shown below


Sample lines

infamous_kb: Do’s And Don’ts Of Facebook 

techbiz911: Do’s And Don’ts Of Facebook 

sowebinc: Do’s And Don’ts Of #Facebook 

kontestapp: Do’s And Don’ts Of Facebook Commenting


Want to want to select and write the lines below back to diffrent txt file. Result should be 

infamous_kb
techbiz911
sowebinc
kontestapp


Can you please give me a sample code

---

### Post by Bachstelze on 2011-07-22
Do you really need Python? Just a simple command will do:

```
cut -d ':' -f 1 input.txt > output.txt
```

---

### Post by LemursDontExist on 2011-07-22
I'm with Bachstelze on this one!  But if you need the output in python for some reason:

```

with open(filename) as f:
    output = '\n'.join(line.split(':')[0] for line in f.readlines())
    with open(other_filename, 'w') as g:
        g.write(output)

```

should work.

There are a million ways to do this - I've spent too much time programming in Haskell, and so I like list comprehensions.

---

### Post by ve4cib on 2011-07-22
Another alternative, slightly more lengthy, but does the same thing in the end:

```

fid = open(filename,'r')     # open the file in read-mode
lines = fid.readlines()      # read all the lines of the file into an array
fid.close()                  # close the file since we're done with it

firstWords = []              # create an empty array to store the first words in
for l in lines:
    tokens = l.split(':')

    # insert the first token (whatever comes before the ':')
    # into the end of the firstWords list
    firstWords.insert(len(firstWords),tokens[0])

# firstWords now contains the first word of every line
print(firstWords)
```

Obviously there may be issues if there's a blank line, but I'll leave that as an exercise for the reader

---

### Post by kaibob on 2011-07-22
I'm just learning Python and thought I would suggest an approach that is only slightly different from that suggested by LemursDontExist. I have omitted the blank line in the output as that is what the OP requested, although this is easily changed. 

```

#!/usr/bin/env python

with open('new.txt', 'w') as inFile:
  with open('file.txt') as outFile:
    for line in outFile:
      word = line.partition(':')
      inFile.write(word[0])

```

REFERENCE
[http://www.python-forum.org/pythonforum/viewtopic.php?f=3&t=27685&sid=940b1ab407fefa0c4da1a197d965d7fc](http://www.python-forum.org/pythonforum/viewtopic.php?f=3&t=27685&sid=940b1ab407fefa0c4da1a197d965d7fc)

---

### Post by TwoEars on 2011-07-22
> **ve4cib said:**
> Another alternative, slightly more lengthy, but does the same thing in the end:

```

fid = open(filename,'r')     # open the file in read-mode
lines = fid.readlines()      # read all the lines of the file into an array
fid.close()                  # close the file since we're done with it

firstWords = []              # create an empty array to store the first words in
for l in lines:
    tokens = l.split(':')

    # insert the first token (whatever comes before the ':')
    # into the end of the firstWords list
    firstWords.insert(len(firstWords),tokens[0])

# firstWords now contains the first word of every line
print(firstWords)
```

Obviously there may be issues if there's a blank line, but I'll leave that as an exercise for the reader

```

# insert the first token (whatever comes before the ':')
    # into the end of the firstWords list
    firstWords.insert(len(firstWords),tokens[0])
```
What's all this about? What do you think .append does?

---

### Post by ve4cib on 2011-07-22
> **TwoEars said:**
> ```

# insert the first token (whatever comes before the ':')
    # into the end of the firstWords list
    firstWords.insert(len(firstWords),tokens[0])
```
What's all this about? What do you think .append does?

Derp.  That's the result of too much time spent staring at C++ today and not thinking clearly.

However, this does further illustrate the point that was made earlier in the thread: there are a million ways of doing this.

---

