---
title: "Stupid Python Question"
date: 2009-04-21
forum: Programming Talk
---

### Post by Sarai the Geek on 2009-04-21
Okay, as I said in the title, it is so insanely basic I'm embarrassed that I can't figure it out. I've run umpteenth google searches and have found nothing.

I can't get python to divide. At all. I'm doing some number crunching for a research paper and I need to run the same basic equation over and over again with a single variable, soI figured that writing a quick program could speed things up, but so far I've just ended up pulling a lot of my hair out.

Here's my code:
```
import math

indiv = raw_input("# of Individuals: ")
dens = indiv/3
print dens
```

But every time I try to run it it lets me define indiv then spits this out:
```
 File "popecodens.py", line 4, in <module>
    dens = spec/3.0
TypeError: unsupported operand type(s) for /: 'str' and 'float'

```

Gah! What am I missing?

---

### Post by dandaman0061 on 2009-04-21
You need to convert the input into a float or int.

```

indiv = raw_input("# of Individuals: ")
indiv = int(indiv)   # <--- convert the input
dens = indiv/3
print dens

```

oh and you also don't need to 'import math'... at least for what you've posted here.

---

### Post by Occasionally Correct on 2009-04-21
raw_input() returns a string. You could try

[php]indiv = int(raw_input("..."))[/php]although you may want to ensure that the input is correct. Hope that helps. :)

**edit:** seconds late! Oh well. ;)

---

### Post by Can+~ on 2009-04-22
Since you're using this for yourself, there's no problem on using "[FONT="Courier New"]input[/FONT]" instead of "[FONT="Courier New"]raw_input[/FONT]"

(Also, in python3, input() is the new raw_input())

---

### Post by Sarai the Geek on 2009-04-22
Sweet, it works now! Thank you so much, guys, also thanks for not making me feel like a total idiot. :)

---

### Post by Sarai the Geek on 2009-04-22
Oh, one more question. Is there a way to set it to repeat indefinitely, so for example my terminal would like like myeh:
```
sarai@Sarai-Laptop:~/Desktop$ python popecoreldens.py
Species density: .66
0.0232047112596
Species density: 193
6.78562011075

```

and on and on until I close the terminal?

---

### Post by sekinto on 2009-04-22
A while loop.

```
from time import sleep
while True:
    CODE
    sleep(SECONDS)
```

Replace CODE with the code you want to run. Replace SECONDS with the number of seconds you want to pause between each execution.

---

### Post by Sarai the Geek on 2009-04-22
> **sekinto said:**
> A while loop.

```
from time import sleep
while True:
    CODE
    sleep(SECONDS)
```Replace CODE with the code you want to run. Replace SECONDS with the number of seconds you want to pause between each execution.

Perfection.
Thanks again!

---

