---
title: "remove multiple CR (0xOA) from large textstring with Python"
date: 2009-06-06
forum: Programming Talk
---

### Post by Krijk on 2009-06-06
I have a large textstring with multiple CR's (OA) in it. I would like to remove these with a single newline. I've tried:

```
def removeUnwantedCR(text):
    text = text.replace('\r\r\r\r', '\n')
    return text

```
but this isn't working. How do I do this in Python?

---

### Post by ghostdog74 on 2009-06-06
it should be '\r\n'. however, you can just use strip()

---

### Post by wmcbrine on 2009-06-06
Just to point out... 0x0A is in fact '\n' aka NL aka new line. CR aka carriage return aka '\r' is 0x0D.

---

### Post by smartbei on 2009-06-06
@ghostdog - strip will only work if the whitespace is at the end of the string. I think waht you want to do (remove all the carraige returns (\r) from a string) is:
```

def remove_all_crs(stirng):
    return string.replace("\r", "")

```
Ususally, you will have new lines (from windows) as "\r\n", and you will need to remove the \r so that it will look normal in linux.
If this is not the case, what exactly is the problem? The code snipper you posted looks fine, except that it searches for and replaces all sequences of 4 carriage returns with a single newline. Is this what you meant?

---

### Post by Krijk on 2009-06-06
> **smartbei said:**
> 
If this is not the case, what exactly is the problem? The code snipper you posted looks fine, except that it searches for and replaces all sequences of 4 carriage returns with a single newline. Is this what you meant?

I have text strings that have large whitespaces in between that I want to remove. I don't want to remove all the newlines ( @wmcbrine :oops: you're absolutely right. ), but keep the last one.

I rstrip() the end, but I also want to remove the whitespace in between.  When I run the text = text.replace('\n\n\n\n', '\n') it just doesn't work. When I remove singular \n with "" it works fine.

---

### Post by ghostdog74 on 2009-06-06
@OP then how does your data file look like? post a sample here, or attach a sample.

@smartbei
> 
strip will only work if the whitespace is at the end of the string

wrong, strip works on both leading whitespaces and trailing spaces. anyway, i had thought OP wants to remove at the end of the line, not in between.

---

### Post by Krijk on 2009-06-06
> **ghostdog74 said:**
> @OP then how does your data file look like? post a sample here, or attach a sample.


The original looks like this

```
just some text with whitespace behind.



text continues here.
```

It has to become:

```
just some text with whitespace behind.
text continues here.
```

---

### Post by unutbu on 2009-06-06
[PHP]#!/usr/bin/env python
input_fh=open('a','r')
output_fh=open('b','w')
for line in input_fh:
    if line.strip():        
        output_fh.write(line.rstrip()+'\n')[/PHP]

The script reads a file called 'a' and writes to a file called 'b'.

---

### Post by Krijk on 2009-06-06
> **unutbu said:**
> [PHP]#!/usr/bin/env python
input_fh=open('a','r')
output_fh=open('b','w')
for line in input_fh:
    if line.strip():        
        output_fh.write(line.rstrip()+'\n')[/PHP]

The script reads a file called 'a' and writes to a file called 'b'.

Thought about something like that, but I'm not reading the string from a file.

---

### Post by unutbu on 2009-06-06
How's this then:
[PHP]#!/usr/bin/env python
astr='''
just some text with whitespace behind.



text continues here.
'''

for line in astr.split('\n'):
    if line.strip():        
        print line[/PHP]

---

### Post by Krijk on 2009-06-06
> **unutbu said:**
> How's this then:
[PHP]#!/usr/bin/env python
astr='''
just some text with whitespace behind.



text continues here.
'''

for line in astr.split('\n'):
    if line.strip():        
        print line[/PHP]

No, this isn't working either. If I reconstruct the complete string I lose the \n I want to keep:

```
#!/usr/bin/env python
astr='''
just some text with whitespace behind.



text continues here.
'''
newstring=''
for line in astr.split('\n'):
    if line.strip():
          newstring += line  
print newstring
```

This results in:
just some text with whitespace behind.text continues here.

---

### Post by Can+~ on 2009-06-06
> **Krijk said:**
> No, this isn't working either. If I reconstruct the complete string I lose the \n I want to keep:

Of course you lose them, you have to reimplement them.

[PHP]#!/usr/bin/env python
astr='''
just some text with whitespace behind.



text continues here.
'''
newstring=''
for line in astr.splitlines():
    if line.strip():
          newstring += line+'\n'  

print newstring[/PHP]

(I also changed .split('\n') with .splitlines(), not a big deal)

---

### Post by ghostdog74 on 2009-06-06
```

print ''.join([i for i in open("file").readlines() if i.strip()!=""])

```

---

### Post by Krijk on 2009-06-07
Thanks everyone, I'll go for Can+~ solution.

---

### Post by ghostdog74 on 2009-06-07
> **Krijk said:**
> Thanks everyone, I'll go for Can+~ solution.

if that's the case, you do not need to create an entire new string. 
```

astr='''
just some text with whitespace behind.



text continues here.
'''
print '\n'.join([ i for i in astr.splitlines() if i.strip()!=""])

```

---

### Post by Krijk on 2009-06-07
> **ghostdog74 said:**
> if that's the case, you do not need to create an entire new string. 
```

print '\n'.join([ i for i in astr.splitlines() if i.strip()!=""])

```

You're right ghostdog. That's even better. I'll use it.

I'm pretty fresh with Python (and programming), but it certainly has a lot to offer.

---

### Post by soltanis on 2009-06-07
Hello regular expressions

```

import re

#...

string = "\r\r\r\r\n"
result = ""

while not string.equals(result):
    result = string.sub(r'\r+\n', "\n")
string = result


```

---

### Post by ghostdog74 on 2009-06-07
> **soltanis said:**
> Hello regular expressions

i wouldn't bother with re in this case.

---

