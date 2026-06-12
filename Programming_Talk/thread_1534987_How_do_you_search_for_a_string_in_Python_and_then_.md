---
title: "How do you search for a string in Python and then return True or False?"
date: 2010-07-20
forum: Programming Talk
---

### Post by Christian Christiansen on 2010-07-20
Hi, this should be a fairly straightforward problem but I'm still getting to grips with programming.

What I wish to do is to search for a string in an xml file using python and then for it to say True or False, depending on whether the string appears within the file or not.

At the moment I've got this:

>>> datafile = file('data.xml')
>>> for line in datafile:
...     if '168439992' in line:
...             print 'True'
...     else:
...             print 'False'
...
False
False
True
False

So at the moment it goes through each line in the xml file and says whether the string appears or not, whereas I would like it only to say True or False just once.

Thanks in advance

---

### Post by simeon87 on 2010-07-20
You shouldn't print at each line but only at the end, when you have analyzed the whole file or as far as needed:

```

found = False
for line in datafile:
    if '168439992' in line:
        found = True
        break
print found

```

---

### Post by Christian Christiansen on 2010-07-20
Thank you for the quick reply, but at the moment it shows up False although 168439992 does appear in the file. Is this because I'm in interactive mode? And could you please clarify what break means? Does that mean not checking the next line?

---

### Post by javierrivera on 2010-07-20
What about:

```
datafile = file('data.xml')
'168439992' in datafile
```

Way more pythonic IMHO.

---

### Post by simeon87 on 2010-07-20
Interactive mode shouldn't matter, it's the same file and Python works the same. Could you post what you did in interactive mode? Have you correctly indented the for-loop so that it really loops over all the lines of the file?

break means the for-loop is exited and it therefore no longer does all the remaining lines. That makes sense because when you've found the string in the line, you no longer need to search the remaining lines.. you already have all the information you need to give the right answer.

---

### Post by simeon87 on 2010-07-20
I just checked: you have to reload the file in interactive mode each time you want to test it out. So do the datafile = file('..') line again and then the for-loop code. Or better yet, make it a function, if you're up to that:

```

def check():
    datafile = file('data.xml')
    found = False
    for line in datafile:
        if '168439992' in line:
            found = True
            break
    print found

```

And then run ```
check()
``` to test.

> **javierrivera said:**
> What about:

```
datafile = file('data.xml')
'168439992' in datafile
```

Way more pythonic IMHO.


That does not appear to work.

---

### Post by Christian Christiansen on 2010-07-20
> **javierrivera said:**
> What about:

```
datafile = file('data.xml')
'168439992' in datafile
```

Way more pythonic IMHO.

I know, but somehow it doesn't work, I don't know why.

I just tried your code (simeon87) without the found='False' to begin with and then it works. I think that once it exits the for loop, the found variable changes back to False for some reason, but thank you for the help, I will just leave out the found='False' to begin with and just check whether the variable is empty or 'True'. It's not perfect but definitely good enough for what I'm trying to do.

Thanks again for your help

---

### Post by Christian Christiansen on 2010-07-20
> **simeon87 said:**
> I just checked: you have to reload the file in interactive mode each time you want to test it out. So do the datafile = file('..') line again and then the for-loop code. Or better yet, make it a function, if you're up to that:

```

def check():
    datafile = file('data.xml')
    found = False
    for line in datafile:
        if '168439992' in line:
            found = True
            break
    print found

```

And then run ```
check()
``` to test.




That does not appear to work.

Thank you, that's perfect :D

---

### Post by simeon87 on 2010-07-20
> **Christian Christiansen said:**
> I just tried your code (simeon87) without the found='False' to begin with and then it works. I think that once it exits the for loop, the found variable changes back to False for some reason, but thank you for the help, I will just leave out the found='False' to begin with and just check whether the variable is empty or 'True'. It's not perfect but definitely good enough for what I'm trying to do.

I'm not sure what you're doing differently that makes it do that. The idea of setting it to False initially is that the variable always has a value so there's no empty variable case. The found variable is False, you walk over all the lines of the file and only when the string is found, it is set to True. Afterwards, this guarantees that the variable found has either the value False or True but not empty, which is what you want.

---

### Post by Christian Christiansen on 2010-07-20
> **simeon87 said:**
> I'm not sure what you're doing differently that makes it do that. The idea of setting it to False initially is that the variable always has a value so there's no empty variable case. The found variable is False, you walk over all the lines of the file and only when the string is found, it is set to True. Afterwards, this guarantees that the variable found has either the value False or True but not empty, which is what you want.

I wrote that before I had seen your new post, your new post has cleared the problem. Basically what I had done was give found a string instead of a value, so found = 'True' instead of found = True. That was what I meant.

Anyways, I'm going to try and see whether this works within my program but I hope I'll be able to solve everything from now on.

Thank you once again

---

### Post by javierrivera on 2010-07-20
> I know, but somehow it doesn't work, I don't know why.

Try this:

> '168439992' in file('data.xml').read()

Works for me searching for a string in a 707 Kb text file.

---

### Post by StephenF on 2010-07-20
> **simeon87 said:**
> 
```

def check():
    datafile = file('data.xml')
    found = False
    for line in datafile:
        if '168439992' in line:
            found = True
            break
    print found

```

The found variable is unnecessary.
```

def check()
    for line in open('data.xml'):
        if '168439992' in line:
            print True
            break
    else:
        print False

```

---

### Post by nvteighen on 2010-07-21
The print-at-end vs. print-as-soonest is just a revamped version of the return-at-end vs. return-as-soonest debate... As usual, it depends on the code and in this kind of snippets neither of both alternatives seems to add nothing at all.

But, what I'd suggest is that if you're going to use that code in some program, please replace those print statements into return statements, so that the function doesn't print True/False, but actually returns it. That way you'll be able for example, to do:

```

if check():
    ...

```

Something that seems quite obvious to do when you have a checking procedure (in Lisp-lingo: a predicate).

---

