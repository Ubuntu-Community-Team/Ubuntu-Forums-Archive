---
title: "Problems with Python 3 global integers"
date: 2012-05-26
forum: Programming Talk
---

### Post by Superpelican12 on 2012-05-26
I'm working on a couple of little Python (3.2) scripts that help people to exercise with maths. I am mainly writing those scripts for myself to learn coding in Python. But I will open source those scripts. One of the programs, this one is called Pythagorean Python, is already open sourced. You can read more about the program at [http://superpelican-web.tk ]("http://superpelican-web.tk")
at the "Projects" page

However I am trying to implement a new function in my latest script (which will be open sourced soon ;) ) and it depends on global integers, however Python constantly gives errors about the global variable not defined. It doesn't matter what I try. It always gives an error. While I've seen a lot of different people on stackoverflow.com define the integer just like I did, it still gives errors.

It doesn't matter if I do:

```

global counter
counter = counter +1

```or
```

global counter
counter = 0
counter = counter +1

```or all sorts of other variants it keeps complaining. I've also tried it without defining the variable as a global variable.

Here' s my code:

```

#!/usr/bin/python3

import math
import random

while 1 == 1:
 usersanswer = input("Answer:")

 if usersanswer == "yes":
  def main1():
   global counter
   counter = 0
   counter = counter +1
 elif usersanswer == "no":
  def main2():
   global meter
   meter = 0
   meter = meter +1
 elif usersanswer == "how many times did I answer yes?":
  print(counter)
 elif usersanswer == "how many times did I answer no?":
  print(meter) 
 else:
  print("You didn't answer with either 'yes' or 'no' ")

```I'm desperate. 

EDIT:
It gives this error:
```

Name error: global name 'counter' is not defined

```According to the debugger/interpreter the error is in line 20

---

### Post by MadCow108 on 2012-05-26
put the counter = 0 and meter = 0 into global scope = the lowest indentation level
e.g. 

```

counter = 0 
meter = 0 
while 1 == 1:
 ....

```

in your code main1 and main2 functions are never called

---

### Post by PeterP24 on 2012-05-26
You have an if-elif-else structure which can fail at the very first pass through the loop. Since only one choice can be true at one pass, if your user choose the wrong answer your loop can execute one of the following at the first pass:

```
 elif usersanswer == "how many times did I answer yes?":
  print(counter)
 elif usersanswer == "how many times did I answer no?":
  print(meter) 
```

thus using counter and meter without them to exist. Oh, an by the way - define these (counter and meter) outside the while loop.

---

### Post by Superpelican12 on 2012-05-26
Thanks both now I understand the problem. How stupid of me. If one of the earlier statements in if-elif-else applies the variable will also never get defined.

Really thanks!

---

### Post by PeterP24 on 2012-05-26
sorry - took a look closer - you are defining main1 and main2 - but because you are not calling them in any way, there is no reason for counter and meter to spring into existence.

---

### Post by Superpelican12 on 2012-05-26
I've fixed it. Now the program at least runs. But when I ask the program how many times I answered yes it always says 0. Which obviously isn't true (in all cases).

---

### Post by PeterP24 on 2012-05-26
How about now?

```
#!/usr/bin/python3

import math
import random

counter, meter = 0, 0

while True:
 usersanswer = input("Answer:")

 if usersanswer == "yes":
   counter = counter +1
 elif usersanswer == "no":
   meter = meter +1
 elif usersanswer == "how many times did I answer yes?":
  print(counter)
 elif usersanswer == "how many times did I answer no?":
  print(meter) 
 else:
  print("You didn't answer with either 'yes' or 'no' ")
```

Importing the random module in this script doesn't serve to anything (you are not using stuff from random module).

---

### Post by Superpelican12 on 2012-05-26
Thanks, for taking the time to help me out. I'm a real newbie. :)

---

