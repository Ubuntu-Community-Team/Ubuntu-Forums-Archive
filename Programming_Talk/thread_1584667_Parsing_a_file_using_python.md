---
title: "Parsing a file using python"
date: 2010-09-29
forum: Programming Talk
---

### Post by KIAaze on 2010-09-29
Hi,

I want to parse a file of the following form:
```
**comment

foo **comment
{
value1 **comment
value2 **comment
value3 value4 **comment
}

bar **comment
{
value1 **comment
value2 **comment
value3 value4 value5 **comment
value6
}

bar **comment
{
value1 **comment
value2 **comment
value3 value4 **comment
value5
}

end

```
What's the best way to do this?

The values can be strings or numbers, but once I have them as strings, converting them shouldn't be a problem.
Objects are of the form "type { values }" and values are separated by newline characters or spaces.
Comments begin with "**" and end with a newline character.

The idea is to create a structure storing the information as a list of objects (list of "foo" objects, list of "bar" objects) with each object containing a list of values.

Here's my current parsing function:
```
def read_input_file(filename):
    print 'Processing ', filename;
    
    # open file
    input = open(filename);
    # read the whole file as one string
    fulltext = input.read();

    print fulltext;

    # remove comments
    pattern_stripcomments = re.compile("\*\*.*\n")
    cleantext = pattern_stripcomments.sub("\n", fulltext);

    print cleantext;
    
    # extract blocks
    pattern_blocks = re.compile("^(?<type>\w+).*?\{(?<data>[^\{\}]*?)\}");
    # from MATLAB, need python equivalent
    # [tokens_blocks match_blocks names_blocks] =  regexp(cleantext, pattern_blocks, 'tokens', 'match', 'names', 'lineanchors', 'warnings');

    # close file
    input.close();

```

---

### Post by KIAaze on 2010-10-21
Just to add the final solution solution to my problem here:

parser.py:
```

#!/usr/bin/env python
# -*- coding: utf-8 -*-

import math
import os
import sys
import re

# class to store objects
class Entry:
    def __init__(self):
        self.type = ''
        self.data = []
    def __str__(self):
        ret = 'type = ' + self.type + '\n' +\
        'data = ' + str(self.data)
        return ret
    
# parsing function
def read_input_file(filename):
    
    print 'Processing ', filename
    
    # open file
    input = open(filename)
    # read the whole file as one string
    fulltext = input.read()
    # close file
    input.close()

    # remove comments
    pattern_stripcomments = re.compile("\*\*.*\n")
    cleantext = pattern_stripcomments.sub("\n", fulltext)

    # Regular expression for matching the blocks:
    # (?P<type>\w+) -> match any word and store it in a group called "type"
    # \s* -> any number of "whitespace characters" (spaces, tabs, newlines, etc)
    # { -> opening bracket
    # (?P<data>[^{}]*) -> match anything except "{" or "}" store it in a group called "data"
    # } -> closing bracket
    # re.DOTALL -> consider everything as "any character", including newline characters
    pattern_objects = re.compile("(?P<type>\w+)\s*{(?P<data>[^{}]*)}",re.DOTALL)
    
    # get list of objects using pattern
    objects = [m.groupdict() for m in pattern_objects.finditer(cleantext)]

    entries = []
    # process objects
    for i in range(len(objects)):
        type = objects[i]['type']
        data = objects[i]['data']
        
        # convert type to upper case and strip it
        type = type.upper().strip()
        # split data by spaces and new lines
        data = re.split('\s+',data)
        # remove empty lines from data
        data = filter(None, data)
        
        entry = Entry()
        entry.type = type
        entry.data = data
        entries.append(entry)
    
    return entries

# code to test parser
entries = read_input_file('input.txt')
for e in entries:
    print e

##########################
# Some simple functions which some might find interesting. Not necessary for parser.
# convert string array to float array
def float_array(A):
    for i in range(len(A)):
        A[i]=float(A[i])
    return(A)
  
# convert string array to int array
def int_array(A):
    for i in range(len(A)):
        A[i]=int(float(A[i]))
    return(A)

# returns true if s can be converted to a float, otherwise false
def is_number(s):
    try:
        float(s)
        return True
    except ValueError:
        return False
    
# returns extension of filename
def getExtension(filename):
    return filename.split(".")[-1]
##########################

```

input.txt:
```
**comment

foo **comment
{
value1 **comment
value2 **comment
value3 value4 **comment
}

bar **comment
{
value1 **comment
value2 **comment
value3 value4 value5 **comment
value6
}

bar **comment
{
value1 **comment
value2 **comment
value3 value4 **comment
value5
}

ubu **comment
{
0 **comment
6 **comment
12 18 **comment
'_great_'
}

end

```

Resulting output:
```
Processing  input.txt
type = FOO
data = ['value1', 'value2', 'value3', 'value4']
type = BAR
data = ['value1', 'value2', 'value3', 'value4', 'value5', 'value6']
type = BAR
data = ['value1', 'value2', 'value3', 'value4', 'value5']
type = UBU
data = ['0', '6', '12', '18', "'_great_'"]

```
I left in a few more simple functions I created in case someone finds it useful. :)
My full code also includes additional postprocessing on the entries depending on their type, but that's not really a big problem.

I found the awesome groupdict/finditer trick in it here:
[http://stackoverflow.com/questions/255332/python-re-findall-with-groupdicts](http://stackoverflow.com/questions/255332/python-re-findall-with-groupdicts)

---

### Post by Vox754 on 2010-10-21
> **KIAaze said:**
> Just to add the final solution solution to my problem here:

Lol, semi-colons in Python!

> 
```
#!/usr/bin/env python
   
def read_input_file(filename):
    
    print 'Processing ', filename;
    
    # open file
    input = open(filename);
    # read the whole file as one string
    fulltext = input.read();
    # close file
    input.close();

...

    entries = [];
    # process objects
    for i in range(len(objects)):
        type = objects[i]['type'];
        data = objects[i]['data'];
        
        # convert type to upper case and strip it
        type = type.upper().strip();
        # split data by spaces and new lines
        data = re.split('\s+',data);
        # remove empty lines from data
        data = filter(None, data);

```


Avoid commenting each line. Better to comment blocks of code:
```

def read_input_file(filename):
    ''' Read the whole file '''
    print 'Processing ', filename
    
    input = open(filename)
    fulltext = input.read()
    input.close()

...
    # Process objects
    #
    # convert type to upper case and strip whitespace
    # split data by spaces and new lines
    # remove empty lines
    entries = [];
    
    for i in range(len(objects)):
        type = objects[i]['type'];
        data = objects[i]['data'];

        type = type.upper().strip();
        data = re.split('\s+',data);
        data = filter(None, data);

```

---

### Post by KIAaze on 2010-10-21
Yes, I know... Bad C,C++ habits. ^^

Commenting each line (well some of them) for a piece of reference code is not necessarily a bad idea in my opinion. Makes it easier for someone unfamiliar with python. Depends of the cases of course. I don't think it makes a big difference here. It's not like I commented every single line.

I didn't even comment the regular expression, which is probably the most cryptic part. So:
```
(?P<type>\w+) -> match any word and store it in a group called "type"
\s* -> any number of "whitespace characters" (spaces, tabs, newlines, etc)
{ -> opening bracket
(?P<data>[^{}]*) -> match anything except "{" or "}" store it in a group called "data"
} -> closing bracket
re.DOTALL -> consider everything as "any character", including newline characters
```

edit: semicolons removed :P

---

