---
title: "Python regular expressions questions"
date: 2011-04-06
forum: Programming Talk
---

### Post by DBQ on 2011-04-06
Hi!

I have a simple question. I have wrote the following code to extract the two parenthesized elements separated by a comma:

```

import re

splitter = re.compile('Greeting\(([a-zA-Z0-9]*),([a-zA-Z0-9]*)\)')

list1 = splitter.split("Greeting(Hello,World)")

print list1


```

When I run the code I get output

```

['', 'Hello', 'World', '']

```

Why are there two '' in the beginning and the end and how do I modify the regex to remove it?

---

### Post by Vaphell on 2011-04-06
that's how re.split() works when there are capturing groups in the pattern
[http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)
> If there are capturing groups in the separator and it matches at the start of the string, the result will start with an empty string. The same holds for the end of the string. That way, separator components are always found at the same relative indices within the result list (e.g., if there&#8217;s one capturing group in the separator, the 0th, the 2nd and so forth).

drop empty elements from list or use different re function
```
import re

teststr = 'Greeting(Hello,World)'
pattern = r'Greeting\(([a-zA-Z0-9]+),([a-zA-Z0-9]+)\)'
print [ x for x in re.split( pattern, teststr ) if x != '' ]
print re.search( pattern, teststr ).groups()


['Hello', 'World']
('Hello', 'World')

```

---

### Post by LemursDontExist on 2011-04-06
You'll save yourself a lot of hassle, and have faster, cleaner, more maintainable code if you avoid using regexes for simple problems.  

```
s="Greeting(Hello,World)"
l = s[9:-1].split(',')
print l
```

Or, if the string could be part of some longer string:

```
start = s.find("Greeting(") + 9
end = s[start:].index(')') + start
l = s[start:end].split(',')
print l
```

Both examples are shorter than the RE version, and should run faster.  If you need to worry about nested parentheses, and similar issues, something more serious is called for, but then, your original RE wouldn't work for that either.

Python's built in string manipulation tools which are there for a reason, so use them!

---

### Post by DBQ on 2011-04-06
Thank you guys, both answers are quite helpful.

---

