---
title: "[SOLVED] [Regular Expression] Matching the same character in different spots?"
date: 2008-04-19
forum: Programming Talk
---

### Post by xelapond on 2008-04-19
I am just learning regular expressions and was wondering if there was a way to match the same character in different spots.  take for example, the following example:

```
aaathdfjehsdyaaa
```Would match three of the same character at the beginning, and random sequence of character in the middle, and then three more of the same(That is the same as the one matched in the beginning) character at the end.  

Also, this may have to match when that is inside a string:
```
ajkl;dilgjvaf**aaahhgydhaaa**iorehdfk
```Thanks, 

Alex

---

### Post by aks44 on 2008-04-19
The concept you're looking for is: *_back-references_* (which go  together with captures).

---

### Post by ghostdog74 on 2008-04-19
what happens when you have this

ajkl;dilgjvafaaahhgydhaaaiorehdfkdfjfdnid[COLOR="Red"]aaa[/COLOR]fdfdsf[COLOR="Red"]aaa[/COLOR]

what would your result look like?

---

### Post by xelapond on 2008-04-19
>  		what happens when you have this

ajkl;dilgjvafaaahhgydhaaaiorehdfkdfjfdnid[COLOR=Red]aaa[/COLOR]fdfdsf[COLOR=Red]aaa[/COLOR]

what would your result look like?

I would expect it to return aaafdfdsfaaa.

---

### Post by ghostdog74 on 2008-04-19
so you only want the very last set of patterns to be displayed. Say you have a file like this
```

aaa12345aaaxxxxxxaaawerttyewweerwerwerwerwersfdsfsdfsaaadfdfsdfdsfsdf

```
the part you want to get is "aaawerttyewweerwerwerwerwersfdsfsdfsaaa"
. you can wait for someone to give you regexp solution, in the meantime, here's a non regexp solution, using splits on pattern.
```

#!/bin/bash
awk 'BEGIN{OFS=FS="aaa"}{ print OFS $(NF-1) OFS}' file

```'
output:
```

# ./test.sh
aaawerttyewweerwerwerwerwersfdsfsdfsaaa

```

you can use the split on pattern method with other languages as well.

---

### Post by xelapond on 2008-04-19
Oh, sorry, I did not realize there were two sets in there.  It would be nice if it could return both.

Here is what I came up with, but it doesn't work:
```
r'(.{3}).+/1'
```If gives the following output:
```
>>> string = 'jksdfajsdhfjtrklsdfjaaajjdhjaaa'
>>> s = re.search(r'(.{3}).+/1', string)
>>> s.group()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'NoneType' object has no attribute 'group'

```I am using Python for the programming language.

---

### Post by aks44 on 2008-04-19
> **xelapond said:**
> ```
r'(.{3}).+/1'
```

The forward slash ( [COLOR="DarkRed"]/1[/COLOR] ) should be a backslash ( [COLOR="DarkRed"]\1[/COLOR] ).


EDIT: FWIW that "[COLOR="DarkRed"]AttributeError: 'NoneType' object has no attribute 'group'[/COLOR]" error means that the regex didn't match at all. You have to ensure the object resulting from the search() call is not null (or whatever that concept is called in Python) before actually using it.

EDIT2:
```
string = 'jksdfajsdhfjtrklsdfjaaajjdhjaaa'
s = re.search(r'(.{3}).+\1', string)
if s != None :
    s.group()
else:
    'Error'
```

---

### Post by xelapond on 2008-04-19
Thanks a ton, 

Now I have this:
```
>>> string = 'jksdfajsdhfjtrklsdfjaaajjdhjaaa'
>>> s = re.search(r'(.{3}).+\1', string)
>>> s.group()
'sdfajsdhfjtrklsdf'

```It appears to be only taking the first on in the sequence.  How do I make it return all of them?  Do I have to remove that from the string and run it again?

Thanks, 

Alex

---

### Post by aks44 on 2008-04-19
> **xelapond said:**
> How do I make it return all of them?

Read the manual or search the web? FWIW here's what I found after about 20 seconds : [http://www.amk.ca/python/howto/regex/regex.html#SECTION000430000000000000000](http://www.amk.ca/python/howto/regex/regex.html#SECTION000430000000000000000)

And no, I don't know anything about Python...

---

### Post by ghostdog74 on 2008-04-19
you want to return them all? that means from this :

aaa12345aaaxxxxxxaaawerttyewweerwerwerwerwersfdsfsdfsaaadfdfsdfdsfsdf

you want to return

1) aaa12345aaa
2) aaaxxxxxxaaa
3) aaawerttyewweerwerwerwerwersfdsfsdfsaaa 
right?

you can use split method like i suggested
```

for lines in open("file"):
    lines = lines.replace("aaa","|").split("|")
    print lines

```
output:
```

# ./test1.py
['', '12345', 'xxxxxx', 'werttyewweerwerwerwerwersfdsfs dfs', 'dfdfsdfdsfsdf']

```
i leave it to you to join each element back with "aaa". You are using Python, so there's really no need to waste your time setting up regexp. If you are still bent on it, 
```

import re
pat = re.compile("(?=aaa(.*?)aaa)")
data = open("file").read()
print pat.findall(data)

```
output:
```

 # ./test1.py
['12345', 'xxxxxx', 'werttyewweerwerwerwerwersfdsfs dfs']


```

---

### Post by ghostdog74 on 2008-04-20
make adjustments to the brackets to include the "aaa"s. i leave it to you.

---

### Post by xelapond on 2008-04-21
Thanks everyone, I got it working.

---

