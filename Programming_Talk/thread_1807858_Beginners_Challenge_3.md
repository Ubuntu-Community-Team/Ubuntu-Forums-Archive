---
title: "Beginners Challenge 3"
date: 2011-07-19
forum: Programming Talk
---

### Post by Randy Flagg on 2011-07-19
Alright I am back for more punishment.  I found this challenge really easy.  I know I could have done some easier things instead of the .re statement but if you have been following along I just learned it and wanted to try it out.  

Please let me know what you think.

Original Challenge is here:

[http://ubuntuforums.org/showthread.php?t=884394](http://ubuntuforums.org/showthread.php?t=884394)

[PHP]
#!/usr/bin/env python
# Ubuntu Forums Beginner Challenge #3
#
#Read all lines from a text file and copy language names beginning with
#S and H to a new file.  Also add a line to the original file.

import sys
import re

try:
    infile = open('bhaarat.text', 'r+')
except IOError: 
    print 'This file does not exist in the current directory'
        
        
outfile = open('out.text', "w")
linenum = 1
for line in infile:
    pattern = re.compile(r'''    
                ^        #tells us to start at the beginning of the string
                \d*        #match any number of digits
                \W        #match any non-alphanumberic character
                \s        #match whitespace
                (S+|H+)    #match either S or H one or more times
                (\w*)    #match anything that follows S or H
                ''', re.VERBOSE)
          
    try:
        (lang1, lang2) = pattern.search(line).groups()
        lang = lang1 + lang2
        outfile.write(str(linenum) + '. ' + lang + '\n')
        linenum += 1
    except AttributeError:
        pass
    
infile.write('23. English')
infile.close()
outfile.close()
        
[/PHP]

---

### Post by TwoEars on 2011-07-19
Very good :D

One little comment though - instead of

```

(lang1, lang2) = pattern.search(line).groups()
lang = lang1 + lang2
```
You could use the reduce function, for example -

```
 lang = reduce(lambda x,y:x+y,pattern.search(line).groups())
```

---

### Post by Bachstelze on 2011-07-19
Nice try with try but your exception handling is bad for two reasons:

1) If an IOError is raised by open, the error message will be printed but the program will continue running, and eventually crash:

```
firas@aoba ~ % python test.py 
This file does not exist in the current directory
Traceback (most recent call last):
  File "test.py", line 18, in <module>
    for line in infile:
NameError: name 'infile' is not defined

```

2) If the file exists but is not readable, an IOError will be raised and your program will say that the file does not exist, which is misleading.

You should be able to fix that by yourself if you read more about exception handling: [http://docs.python.org/tutorial/errors.html](http://docs.python.org/tutorial/errors.html)

*EDIT:* Also I would add a comment to explain why you ignore AttributeError exceptions in your secont try...except block, because it's not obvious.

---

### Post by schauerlich on 2011-07-19
> **TwoEars said:**
> You could use the reduce function, for example -

```
 lang = reduce(lambda x,y:x+y,pattern.search(line).groups())
```

I wouldn't say that's any clearer. No point in using reduce on a two element collection.

---

### Post by TwoEars on 2011-07-19
> **schauerlich said:**
> I wouldn't say that's any clearer. No point in using reduce on a two element collection.

True, but
1) It makes for more reusable code, which code should always be
2) It saves using tuple unpacking and IMO, that makes code a lot cleaner in code such as this. lang1 and lang2 aren't wonderful names, and any clearer names are going to be quite long.

Oh, and @OP

```
outfile.write(str(linenum) + '. ' + lang + '\n')
```
would be better achieved using string formatting.

I also recommend "with" to ensure file closing - it makes your code more readable, and when it comes to writing modular programs, it ensures you don't make a mistake and leave a file open.

---

### Post by Randy Flagg on 2011-07-20
> **TwoEars said:**
> Very good :D


```
 lang = reduce(lambda x,y:x+y,pattern.search(line).groups())
```

I haven't played with lambda all that much.  I know the 'lang' names were a little conrfusing but that was the best I could come up with.  Maybe I will try and work with lambda in the next challenge as a challenge to myself.

---

### Post by TwoEars on 2011-07-20
> **Randy Flagg said:**
> I haven't played with lambda all that much.  I know the 'lang' names were a little conrfusing but that was the best I could come up with.  Maybe I will try and work with lambda in the next challenge as a challenge to myself.

Well, lambda is handy when you need it - not so much when you don't. Learning to use it in the correct place is probably the most important bit of learning them ;)

Well, you could've changed your regex to return the initial letter and the rest of the word in one , for example - 
```

re.search('([SH]\w*)', text)

```
;)

---

### Post by Randy Flagg on 2011-07-20
> **Bachstelze said:**
> Nice try with try but your exception handling is bad for two reasons:

1) If an IOError is raised by open, the error message will be printed but the program will continue running, and eventually crash:


Good catch I can't believe I missed that.  Fixed with a simple filegood boolean and if condition.

> 

```
firas@aoba ~ % python test.py 
This file does not exist in the current directory
Traceback (most recent call last):
  File "test.py", line 18, in <module>
    for line in infile:
NameError: name 'infile' is not defined

```2) If the file exists but is not readable, an IOError will be raised and your program will say that the file does not exist, which is misleading.


I get it.  IOError could be a number of different things.  I changed the screen ouput to reflect that it could be a number of problems.

> 

*EDIT:* Also I would add a comment to explain why you ignore AttributeError exceptions in your secont try...except block, because it's not obvious.

Another good point,  it took me a while just to figure out why I was getting this error.  Comment added.

I will add the new code at the end of this thread.

---

### Post by Randy Flagg on 2011-07-20
> **TwoEars said:**
> 
Well, you could've changed your regex to return the initial letter and the rest of the word in one , for example - 
```

re.search('([SH]\w*)', text)

```;)

This worked great.  I was trying to do this before but couldn't figure it out.

---

### Post by Randy Flagg on 2011-07-20
> **TwoEars said:**
> 

Yeah, maybe I am doing something wrong but this:

```

outfile.write('{0}. {1}'.format(str(linenum), lang))

```

just prints out the braces with the numbers.  It doesn't seem to reference the .format at all

I also tried:

```

outfile.write('%d. %s') % (linenum, lang[0])

```

and got back File 

"UF-Challenge3-2.py", line 35, in <module>
    outfile.write('%s. %s') % (str(linenum), lang[0])            
TypeError: unsupported operand type(s) for %: 'NoneType' and 'tuple'

[QUOTE]

I also recommend "with" to ensure file closing - it makes your code more  readable, and when it comes to writing modular programs, it ensures you  don't make a mistake and leave a file open.


I am not sure how I would use 'with' here.  The only way in my code that the files don't get opened is if the input file throws and exception???

---

### Post by Randy Flagg on 2011-07-20
Latest and greatest.

[PHP]
#!/usr/bin/env python
# Ubuntu Forums Beginner Challenge #3
#
#Read all lines from a text file and copy language names beginning with
#S and H to a new file.  Also add a line to the original file.

import sys
import re

try:
    infile = open('bhaarat.text', 'r+')
    filegood = True
except IOError: 
    print 'There is a problem with the bhaarat.txt file'
    print 'It may not exist in the current directory or may be corrupted'
    print 'Please correct the problem and run the program again.'
    filegood = False
        
if filegood:        
    outfile = open('out.text', "w")
    linenum = 1
    for line in infile:
        pattern = re.compile(r'''    
                ^            #tells us to start at the beginning of the string
                \d*            #match any number of digits
                \W            #match any non-alphanumberic character
                \s            #match whitespace
                ([SH]\w*)    #match either S or H one or more times and anything
                ''', re.VERBOSE) #alphanumeric that follows S or H
        try:        
            lang = pattern.search(line).groups()
            outfile.write(str(linenum) + '. ' + lang[0] + '\n')
            linenum += 1
        except AttributeError: #If the pattern is not matched it will return
            pass               #a null.  This will cause an attribute error.
                               #if we except it, we just run a pass and the 
                               #for loop moves on to the next line

    infile.write('23. English')
    infile.close()
    outfile.close()
[/PHP]

---

### Post by TwoEars on 2011-07-20
> **Randy Flagg said:**
> Yeah, maybe I am doing something wrong but this:

```

outfile.write('{0}. {1}'.format(str(linenum), lang))

```

As far as I can see, this should work.

> 
I also tried:

```

outfile.write('%d. %s') % (linenum, lang[0])

```

and got back File 

"UF-Challenge3-2.py", line 35, in <module>
    outfile.write('%s. %s') % (str(linenum), lang[0])            
TypeError: unsupported operand type(s) for %: 'NoneType' and 'tuple'

Here, the formatting is in the wrong place -

Try this instead -
```

outfile.write('%d. %s' % (linenum, lang[0]))

```

> 
I am not sure how I would use 'with' here.  The only way in my code that the files don't get opened is if the input file throws and exception???

Have a read of this - [http://www.python.org/dev/peps/pep-0343/](http://www.python.org/dev/peps/pep-0343/)
It basically says why you should always use with for file handling.

```

except IOError: 
    print 'There is a problem with the bhaarat.txt file'
    print 'It may not exist in the current directory or may be corrupted'
    print 'Please correct the problem and run the program again.'
    filegood = False
```

Instead of doing this, I suggest you exit the program using sys.exit(1).

```
except AttributeError: #If the pattern is not matched it will return
            pass               #a null.  This will cause an attribute error.
                               #if we except it, we just run a pass and the 
                               #for loop moves on to the next line

```
I can't say I like this format of commenting - comments shouldn't really be on the same line as code.

---

### Post by Bachstelze on 2011-07-20
> **Randy Flagg said:**
> Good catch I can't believe I missed that.  Fixed with a simple filegood boolean and if condition.

You could also have put a sys.exit at the end of your except clause.



> I get it.  IOError could be a number of different things.  I changed the screen ouput to reflect that it could be a number of problems.

For bonus points, try to tell the user exactly what's going on. :) The link I gave you has all the info about doing that.



> Another good point,  it took me a while just to figure out why I was getting this error.  Comment added.

I will add the new code at the end of this thread.

```
        try:        
            lang = pattern.search(line).groups()
            outfile.write(str(linenum) + '. ' + lang[0] + '\n')
            linenum += 1
        except AttributeError: #If the pattern is not matched it will return
            pass               #a null.  This will cause an attribute error.
                               #if we except it, we just run a pass and the 
                               #for loop moves on to the next line
```

I would have done it like this:

```
lang = pattern.search(line).groups()
if lang is not Null: # Null => no match
    ...
```

---

### Post by Randy Flagg on 2011-07-20
> **Bachstelze said:**
> You could also have put a sys.exit at the end of your except clause.





For bonus points, try to tell the user exactly what's going on. :) The link I gave you has all the info about doing that.



Yes sysexit works better.  That is some heavy reading on the try exception deal.  I may try that at a later date.

> **Bachstelze said:**
> 

I would have done it like this:

```
lang = pattern.search(line).groups()
if lang is not Null: # Null => no match
    ...
```

Yes, I wanted to do that but wasn't sure how to implement it.  Works good.

> **TwoEars said:**
> 
Here, the formatting is in the wrong place -

Try this instead -
```

outfile.write('%d. %s' % (linenum, lang[0]))

```

I corrected this and it works fine.

> **TwoEars said:**
> 
Have a read of this - [http://www.python.org/dev/peps/pep-0343/](http://www.python.org/dev/peps/pep-0343/)
It basically says why you should always use with for file handling.


I read this an understand it but I have two problems.

First, it would be a lot nicer if 'with' came with an except.  If I use it out of the box and it throws an error I have no way of handling it.

Second, I tried using the opened_w_error function included in the PEP but it throws an Attribute Error __exit__ every time.

> **TwoEars said:**
> 
```
except AttributeError: #If the pattern is not matched it will return
            pass               #a null.  This will cause an attribute error.
                               #if we except it, we just run a pass and the 
                               #for loop moves on to the next line

```I can't say I like this format of commenting - comments shouldn't really be on the same line as code.

How do I put that much commenting on one line?

---

### Post by TwoEars on 2011-07-20
> **Randy Flagg said:**
> 
I read this an understand it but I have two problems.

First, it would be a lot nicer if 'with' came with an except.  If I use it out of the box and it throws an error I have no way of handling it.

Second, I tried using the opened_w_error function included in the PEP but it throws an Attribute Error __exit__ every time.
 

With isn't really there for that sort of error catching (with file opening, though it is possible). Instead, with is there to ensure your file is closed no matter what happens inside the with structure. Basically, with should be used to handle things which _need_ exiting (or closing, in a file's case). It doesn't catch errors in the inital statement unless using certain methods (which are fairly complex if you're a beginner). 

Perhaps this site has better examples - [http://effbot.org/zone/python-with-statement.htm](http://effbot.org/zone/python-with-statement.htm)

**Edit**: I can't seem to find any good tutorials to link for you, so perhaps you should skip this. It's a shame, it's quite  handy when it comes to large projects where you're likely to leave out that vital f.close(), or you're in a bad state of mind and don't work through your conditionals properly.
> 
How do I put that much commenting on one line?

Simple answer - you don't.

Instead, this is where triple quoting comments comes in - 

```

except AttributeError:
    """If the pattern is not matched it will return
    null.  This will cause an attribute error.
    if we except it, we just pass and the 
    for loop moves on to the next line"""
    
    pass  
```

If you kept it as it is now, you'd have to mess around with relining every time you make a change to the code - not fun! This way, you just say what's going to happen, then do it. Document the process, then do the process.

---

### Post by Bachstelze on 2011-07-21
> **Randy Flagg said:**
> Yes sysexit works better.  That is some heavy reading on the try exception deal.  I may try that at a later date.


More specifically this part:

> The except clause may specify a variable after the exception name (or tuple). The variable is bound to an exception instance with the arguments stored in instance.args. For convenience, the exception instance defines __str__() so the arguments can be printed directly without having to reference .args.

One may also instantiate an exception first before raising it and add any attributes to it as desired.

```
>>> try:
...    raise Exception('spam', 'eggs')
... except Exception as inst:
...    print type(inst)     # the exception instance
...    print inst.args      # arguments stored in .args
...    print inst           # __str__ allows args to printed directly
...    x, y = inst          # __getitem__ allows args to be unpacked directly
...    print 'x =', x
...    print 'y =', y
...
<type 'exceptions.Exception'>
('spam', 'eggs')
('spam', 'eggs')
x = spam
y = eggs
```


Basically, an exception is an object (almost everything in Python is an object), and it has attributes, so you can bind it to a variable and manipulate it and its attributes. In the case at hand:

```
firas@aoba ~ % ls -l bhaarat.text 
--w------- 1 firas staff 8 Jul 19 23:02 bhaarat.text
firas@aoba ~ % python
Python 2.6.1 (r261:67515, Jun 24 2010, 21:47:49) 
[GCC 4.2.1 (Apple Inc. build 5646)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> try:
...     f = open('bhaarat.text', 'r')
... except IOError as ioerror:
...     print ioerror.args
... 
(13, 'Permission denied')

```

So you can do something like:

```
except IOError as ioerror:
    print "Could not read input file: Error %s (%s)" % ioerror.args
```

If you're wondering what 13 means, it's the errno number for "Permission denied":

```
firas@aoba ~ % grep 13 /usr/include/sys/errno.h 
#define	EACCES		13		/* Permission denied */

```

---

