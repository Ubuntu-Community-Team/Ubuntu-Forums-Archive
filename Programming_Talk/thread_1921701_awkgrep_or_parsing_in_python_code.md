---
title: "awk/grep or parsing in python code"
date: 2012-02-07
forum: Programming Talk
---

### Post by .vogue on 2012-02-07
Hello,
I am writing a python code. The output of the python code needs a little  bit of parsing. From the output of python code, which has a lot of  redundant data, I need to cut only those words or numbers which end with  &. for example: if the output is--

"This is an example of tgbn123& what i need to get"

I need to write tgbn123 in a text file. Is is possible using grep or awk in python? If so, how?

---

### Post by coffeecat on 2012-02-07
*Thread moved to **Programming Talk**.*

---

### Post by Tony Flury on 2012-02-07
Look at regular expressions - rather than looking to call awk or grep.

I am sure a regular expression expert will be along soon to help.

---

### Post by Khayyam on 2012-02-07
.vogue ...

this should select only those words that end with '&' ..

```
cat input.txt | awk '{for(i=1;i<=NF;i++){if($i~/\&$/){print $i}}}' >> output.txt
```tested with the following input ..

```
% cat input.txt
This is an example of tgbn123& what i need to get
This is another line pqrs66412& similar
This is one we don't hve&h54 want
% cat input.txt | awk '{for(i=1;i<=NF;i++){if($i~/\&$/){print $i}}}'
tgbn123&
pqrs66412&
```HTH ...

edit: fixed to make sure "hve&h54" and the like don't match.

---

### Post by Tony Flury on 2012-02-08
Using cat and awk in a python script is not a great idea - especially not when python has the re module.

see the following :

[http://docs.python.org/library/re.html#module-re](http://docs.python.org/library/re.html#module-re)

I think the regular expression you need is 

\w+&\W (i.e. match one or more alpha numeric characters, followed by an "&", followed by a non alphanumeric character).

I have only used the re module once (and the code is at home on my laptop, so I can't advise exactly how to use the above regex in the module), but this might work as a fragment.

```

import re

regex = "\w+&\W"
example = "This is an example of tgbn123& what i need to get"
mo = re.match( regex, example)
print mo.group(1)

```
if your string could include multiple examples, then you might need to use search rather than match, as the match example will only give you the last matching sub-string

---

### Post by Tony Flury on 2012-02-08
@.vogue

Revised code fragment (using match is wrong, as it tests from the start of the string, rather than finding a substring)
```

import re

regex = "\w+&\W"
example = "This is an example& of tgbn123& what i need to get"
for i in re.finditer(regex, example)
    print i.group(0).strip()

```

The strip method call is neccessary as the regexp "consumes" the space after the "&" character.

I have tested this with the example string above - no with all combinations.

---

### Post by Khayyam on 2012-02-08
> **Tony Flury said:**
> Using cat and awk in a python script is not a great idea - especially not when python has the re module.

Tony ..

Your quite right, generally its best to use native methods for the task. However awk can do alot of things that regex can't (or does less optimally), so there is a place for os.system(awk).

Also, the 'cat' in the above example isn't necessary, its just there to illustrate I/O .. "awk input.txt" does the same.

best ...

---

### Post by .vogue on 2012-02-08
Well, thank you Khayyam and Tony Flury. I am new to python and bash. I really appreciate your help!

---

### Post by Tony Flury on 2012-02-09
All 
Here is another version - which should avoid the need for a strip function call, by using a regexp group.

```

import re

regex = "(\w+&)\W"
example = "This is an example& of tgbn123& what i need to get"
for i in re.finditer(regex, example):
    print i.group(1)

```
That should work :
group(0) is the entire matched string, group(1) is the match within the first parentheses. This version might actually be a bit quicker as it avoids the need for another function call (i.e. strip), and I would guess that regex grouping is all done in C.

---

