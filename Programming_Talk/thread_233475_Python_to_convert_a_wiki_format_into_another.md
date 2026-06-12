---
title: "Python to convert a wiki format into another"
date: 2006-08-10
forum: Programming Talk
---

### Post by tseliot on 2006-08-10
Hi, I'm trying to write a script which should convert my guides from a wiki format to another.

```
#/usr/bin/env python
import fileinput, re

'''Title'''
pat = re.compile('(==)([^\=]+)(==)')
'''Subsections'''
pat1 = re.compile('(===)(.+)(===)')
'''Boxcode'''
pat2 = re.compile('({{BoxCode\|<nowiki>)(.*)(.+)(.*)(</nowiki>.*}})')


for line in fileinput.input():
    m = pat.match(line)
    n = pat1.match(line)
    o = pat2.match(line)

    if m:
        title = m.group(2)
    if n:
        title1 = n.group(2)
    if o:
        codebox = o.group(3)

lines = []
for line in fileinput.input():
    lines.append(line)

text = ''.join(lines)

print pat.sub('= ' + title + ' =', text)
print pat1.sub('== ' + title1 + ' ==', text)
print pat2.sub('{{{' + codebox + '}}}', text)
```



1) I want my script to convert (for example):
```
==HOWTO: Latest NVIDIA drivers==
```

into

```
= HOWTO: Latest NVIDIA drivers =
```

2) and to convert:

```
===Something else===
```

into

```
== Something else ==
```


3) and to convert:
```
{{BoxCode|<nowiki>sudo apt-get install linux-k7</nowiki>}}
```

into
```

{{{sudo apt-get install linux-k7}}}
```

The problem is that there are several sentences which begin and end with "==" but when I run my script every line which begins and ends with "==" looks exactly like this:
```
= HOWTO: Latest NVIDIA drivers =
```

so that I have texts like:
```
= HOWTO: Latest NVIDIA drivers =

then something else

= HOWTO: Latest NVIDIA drivers =
```


**But they should look like**:
```
= HOWTO: Latest NVIDIA drivers =

then something else

= Method1 =

```


Any ideas on how I could solve the problem?


Thanks in advance

---

