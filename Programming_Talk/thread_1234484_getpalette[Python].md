---
title: "getpalette[Python]"
date: 2009-08-07
forum: Programming Talk
---

### Post by Godd on 2009-08-07
With PIL, why is it that when I change the color palette of a photo with putpalette, once it's saved(and noticeably modified) the value returned by getpalette is exactly the same as the unmodified image?

Even from the conversion from color to B&W?

I'm stumped.

---

### Post by Can+~ on 2009-08-07
How about some code? PIL is one of those things I normally go, read about, use and then forget.

---

### Post by Godd on 2009-08-07
Ha. K.

I understand. PIL seems like a library that is only easy to remember if yo do alot of image manipulation apps.

Syntax: ./pic_encoder.py <image location> <info to be encoded>

Hopefully my coding isn't too horrible.

I'm naturally good at code obfuscation. Ha.

---

### Post by Can+~ on 2009-08-08
Any particular reason to do this?
```
ent = [encoder.coder.bin.**im_func**(sys.argv[2])]
```

What's going on here?
[PHP]for x in range(len(code_act)):
    if int(code_act[x]) == 0:
        list[x] = 0[/PHP]

I could go on, but to summarize:
[LIST]
[*]I can't understand what the code does (not a single comment aside a single __doc__ string).
[*]Unhelpful variable and function/methods names (astr, bin, io, ent). You're not coding on assembly, you can use long names for this things.
[*]Said variables sometimes use builtin names (list, bin)
[/LIST]

As for your problem, it's really difficult to tell what's going on. And to save everyone's time on downloading the file:

pic_encoder.py
[PHP]#!/usr/bin/python
#for me
#Pic_Coder is an attempt at hiding small bits of information in a very
#inobvious place. That being hidden inside of a photo without adding extra 
#levels of complexity to the picture. 
#NOTE: The longer the bit of information, the more obvious the difference.

import sys
import PIL
from PIL import Image
import encoder

if len(sys.argv) != 3:
    print "Syntax Error: ./pic_coder.py <picture location> <'info to be encoded'>"
    sys.exit() 

im = Image.open(sys.argv[1]).convert("P")
im.load()
list = im.getpalette()

print list

ent = [encoder.coder.bin.im_func(sys.argv[2])]
code_act = ent[0]

for x in range(len(code_act)):
    if int(code_act[x]) == 0:
        list[x] = 0

im.putpalette(list)

im.show()

[/PHP]

encoder.py
[PHP]#!/usr/bin/python
#for me

import sys 
import bin

class coder():

    def __init__(self,astr):

        self.astr=astr

    def bin(astr):

        list=[bin.bin(ord(io)) for io in astr]
        iter = len(list) - 1

        out = ''.join(map(str,list))

        return out
[/PHP]

bin.py
[PHP]#!/usr/bin/env python

def bin(num):
    """
    __source__='http://mail.python.org/pipermail/python-list/2000-March/028379.html'
    __author__='wheineman 1wheinemanNOwhSPAM at uconect.net.invalid'
    Returns a string binary representation of a number. For example
    bin(255) returns '11111111'.
    """
    import sys
    returnValue = ''
    mask = 0
    i = 0
    while(1):
        mask = 1 << i
        if (i != 0) and (mask > num):
            break
        if (mask & num):
            returnValue = '1' + returnValue
        else:
            returnValue = '0' + returnValue
        i = i + 1
    return returnValue[/PHP]

---

### Post by Godd on 2009-08-08
> **Can+~ said:**
> Any particular reason to do this?
```
ent = [encoder.coder.bin.**im_func**(sys.argv[2])]
```

What's going on here?
[PHP]for x in range(len(code_act)):
    if int(code_act[x]) == 0:
        list[x] = 0[/PHP]

I could go on, but to summarize:
[LIST]
[*]I can't understand what the code does (not a single comment aside a single __doc__ string).
[*]Unhelpful variable and function/methods names (astr, bin, io, ent). You're not coding on assembly, you can use long names for this things.
[*]Said variables sometimes use builtin names (list, bin)
[/LIST]

As for your problem, it's really difficult to tell what's going on. And to save everyone's time on downloading the file:

pic_encoder.py
[PHP]#!/usr/bin/python
#for me
#Pic_Coder is an attempt at hiding small bits of information in a very
#inobvious place. That being hidden inside of a photo without adding extra 
#levels of complexity to the picture. 
#NOTE: The longer the bit of information, the more obvious the difference.

import sys
import PIL
from PIL import Image
import encoder

if len(sys.argv) != 3:
    print "Syntax Error: ./pic_coder.py <picture location> <'info to be encoded'>"
    sys.exit() 

im = Image.open(sys.argv[1]).convert("P")
im.load()
list = im.getpalette()

print list

ent = [encoder.coder.bin.im_func(sys.argv[2])] # bin converts a text 
code_act = ent[0]                              # string to binary.

for x in range(len(code_act)):  # this bit modifys the color palette in
    if int(code_act[x]) == 0:   #a sequence corresponding to the binary 
        list[x] = 0             #output of bin.

im.putpalette(list)             # this applys the color palette

im.show()

[/PHP]

encoder.py
[PHP]#!/usr/bin/python
#for me

import sys 
import bin

class coder():

    def __init__(self,astr):

        self.astr=astr

    def bin(astr):

        list=[bin.bin(ord(io)) for io in astr]
        iter = len(list) - 1

        out = ''.join(map(str,list)) # this concatenates the output from
                                     # i couldn't think of a more concise
        return out                   # name than bin so i lazily used 
                                     # twice. Stupid I know.
[/PHP]                          

bin.py
[PHP]#!/usr/bin/env python

def bin(num):
    """
    __source__='http://mail.python.org/pipermail/python-list/2000-March/028379.html'
    __author__='wheineman 1wheinemanNOwhSPAM at uconect.net.invalid'
    Returns a string binary representation of a number. For example
    bin(255) returns '11111111'.
    """
    import sys
    returnValue = ''
    mask = 0
    i = 0
    while(1):
        mask = 1 << i
        if (i != 0) and (mask > num):
            break
        if (mask & num):
            returnValue = '1' + returnValue
        else:
            returnValue = '0' + returnValue
        i = i + 1
    return returnValue[/PHP]

I'll try to re-edit it using better coding habits. I just haven't gotten used to it yet, My progs are just for my own learning and I never saw the need to use doc strings for myself on such small code.

as per the im_func. I was just chunking that part out and couldn't find a better solution to the problem I was having. Figured I would fix it later.

As I said, I'm not good. I've only been coding for a very short time and a very limited amount of scripts. ha. Sorry. I'll do better.

---

### Post by Godd on 2009-08-08
Hopefully this is more readable.

```
#!/usr/bin/python
#for me
#Pic_Coder is an attempt at hiding small bits of information in a very
#inobvious place. That being hidden inside of a photo without adding extra 
#levels of complexity to the picture. 
#NOTE: The longer the bit of information, the more obvious the difference.
"""
pic_encoder is a small application for the incognito hiding of small bits of information such as passwords or names
"""

import sys
import PIL
from PIL import Image
import encoder 

if len(sys.argv) != 3:
    print "Syntax Error: ./pic_coder.py <picture location> <'info to be encoded'>"
    sys.exit() 

im = Image.open(sys.argv[1]).convert("P")
im.load()
pal = im.getpalette()

ent = [encoder.bin_str(sys.argv[2])]
code_act = ent[0]

for x in range(len(code_act)):
    if int(code_act[x]) == 0:
        pal[x] = 0 

bw = im.putpalette(pal)

im.show()
final = im.convert("RGB")
yn = raw_input("Would you like to save the encoded image? (y/n)")

if yn is "y":

    sv_yn = raw_input("What would you like to save the image as? (name.jpeg)")
    final.save(sv_yn)

```

```
#!/usr/bin/python
#for me

import sys 
from bin import bin

"""
This concatenates the output from the text to binary converter bin.
"""
def __init__(self,astr):

    self.astr=astr
  
def main():
    if __name__ == "__main__":
        bin_str = encoder()

def bin_str(astr):

    br_strs = [bin(ord(io)) for io in astr] #outputs the text from stdin to a binary string for each char.

    con_str = ''.join(map(str,br_strs))     #this concatenates the multiple binary strings.

    return con_str 

```

```
#!/usr/bin/env python

def bin(num):
    """
    __source__='http://mail.python.org/pipermail/python-list/2000-March/028379.html'
    __author__='wheineman 1wheinemanNOwhSPAM at uconect.net.invalid'
    Returns a string binary representation of a number. For example
    bin(255) returns '11111111'.
    """
    import sys
    returnValue = ''
    mask = 0
    i = 0
    while(1):
        mask = 1 << i
        if (i != 0) and (mask > num):
            break
        if (mask & num):
            returnValue = '1' + returnValue
        else:
            returnValue = '0' + returnValue
        i = i + 1

    return returnValue

```

---

### Post by Sebaztian Ortiz on 2009-08-08
> **Godd said:**
> Hopefully this is more readable.

```
#!/usr/bin/python
#for me
#Pic_Coder is an attempt at hiding small bits of information in a very
#inobvious place. That being hidden inside of a photo without adding extra 
#levels of complexity to the picture. 
#NOTE: The longer the bit of information, the more obvious the difference.
"""
pic_encoder is a small application for the incognito hiding of small bits of information such as passwords or names
"""

import sys
import PIL
from PIL import Image
import encoder 

if len(sys.argv) != 3:
    print "Syntax Error: ./pic_coder.py <picture location> <'info to be encoded'>"
    sys.exit() 

im = Image.open(sys.argv[1]).convert("P")
im.load()
pal = im.getpalette()

ent = [encoder.bin_str(sys.argv[2])]
code_act = ent[0]

for x in range(len(code_act)):
    if int(code_act[x]) == 0:
        pal[x] = 0 

bw = im.putpalette(pal)

im.show()
final = im.convert("RGB")
yn = raw_input("Would you like to save the encoded image? (y/n)")

if yn is "y":

    sv_yn = raw_input("What would you like to save the image as? (name.jpeg)")
    final.save(sv_yn)

``````
#!/usr/bin/python
#for me

import sys 
from bin import bin

"""
This concatenates the output from the text to binary converter bin.
"""
def __init__(self,astr):

    self.astr=astr
  
def main():
    if __name__ == "__main__":
        bin_str = encoder()

def bin_str(astr):

    br_strs = [bin(ord(io)) for io in astr] #outputs the text from stdin to a binary string for each char.

    con_str = ''.join(map(str,br_strs))     #this concatenates the multiple binary strings.

    return con_str 

``````
#!/usr/bin/env python

def bin(num):
    """
    __source__='http://mail.python.org/pipermail/python-list/2000-March/028379.html'
    __author__='wheineman 1wheinemanNOwhSPAM at uconect.net.invalid'
    Returns a string binary representation of a number. For example
    bin(255) returns '11111111'.
    """
    import sys
    returnValue = ''
    mask = 0
    i = 0
    while(1):
        mask = 1 << i
        if (i != 0) and (mask > num):
            break
        if (mask & num):
            returnValue = '1' + returnValue
        else:
            returnValue = '0' + returnValue
        i = i + 1

    return returnValue

```

Do it really works on avatars?

---

### Post by Godd on 2009-08-08
Yes. It works on any file savable as a .jpeg. The issue is that without being able to recover the palette the text string is non-recoverable.

---

### Post by bobince on 2009-08-10
> **Godd said:**
> With PIL, why is it that when I change the color palette of a photo with putpalette, once it's saved(and noticeably modified) the value returned by getpalette is exactly the same as the unmodified image?

I'm pretty sure it's a bug in getpalette. The same thing happens to me when I use im.convert() to change a full-colour image to a paletted one (using ADAPTIVE palette). The correct palette is there somewhere, but the public API won't let you see it.

The rather pathetic workaround I use at the moment is to save the newly-paletted file and load it back in again, at which point the API-visible palette is reloaded and catches up. One of these years I'll have a look through PIL and see if I can't find out what's going on and fix it properly...

---

