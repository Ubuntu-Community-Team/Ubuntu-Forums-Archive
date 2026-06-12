---
title: "regular expression question"
date: 2011-09-04
forum: Programming Talk
---

### Post by raac on 2011-09-04
hello guys, I´ve been working on a regular expression for a while...
 
from a set {0,1,2}, I need to create a regular expression that takes string that do not contain 010.
 
This is what I´ve done so far
 
^([^0]|00*[^1]|00*1[^0]|^[0-2]$)*$
 
 
however it does not take all instances
for instance it does not take
0000110
 
and it suppose to.
 
I´m not sure why is not taking that number
 
Thanks in advance

---

### Post by papibe on 2011-09-04
Is it for sed, bash, something else?
Regards.

---

### Post by raac on 2011-09-04
It has to be generic
 
I have to use the normal operations {*,^(negation),+,(x|x),[a-z].....etc}

---

### Post by raac on 2011-09-04
Could there be an easier way to accomplish this?
It sounded simple when I thought about it, but when I sat down and started doing the regular expression I realized I was wrong

---

### Post by Smart Viking on 2011-09-04
Make some lines, and say if they should match or not.
It's hard to understand what you mean.

---

### Post by raac on 2011-09-04
0000000[COLOR=red]010 [/COLOR]   should NOT match because it contains 010
1111111001    should match because it does not contain 010
(empty string) should match because it does not contain 010
[COLOR=red]010[/COLOR]               should NOT match because it contains 010
111111111[COLOR=red]010[/COLOR]11111    should NOT match because it contains 010
00022000000000[COLOR=red]010[/COLOR]00000  should NOT match because it contains 010
00000000000 should match because it does not contain 010

---

### Post by Smart Viking on 2011-09-04
There are more intelligent ways to do that:


Example with grep:
```
echo "11111111101011111" | grep -v 010
```
Example in python:
```
strings = ["0000000010","1111111001","","11111111101011111","0002200000000001000000","00000000000"]

for i in strings:
  if not "010" in i:
    print i
```

---

### Post by Vaphell on 2011-09-04
[http://stackoverflow.com/questions/406230/regular-expression-to-match-string-not-containing-a-word](http://stackoverflow.com/questions/406230/regular-expression-to-match-string-not-containing-a-word)

---

### Post by NovaAesa on 2011-09-04
This looks a heck of a lot like homework to me. I would suggest building a finite state automata, then convert it into a regular expression from there if you are having trouble.

---

