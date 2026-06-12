---
title: "Python/PyGTK gobject.timeout_add"
date: 2008-04-15
forum: Programming Talk
---

### Post by Nunslaughter on 2008-04-15
Here a bit of my code (very stripped):

```
self.maintimer = gobject.timeout_add(1000, self.checktemp)

def checktemp(self):
    if temp < 40 :
        print "lower then 40"
        # do a command 1
    else:
        print "higher then 40"
        # do command 2
    return True
```

OK, nothing wrong with this, it works just fine. It prints out every second if the temp is higher or lower then 40. The problem is the commands. If I enter a command, it will also do that command every second, but it only needs to be done once.

I mean: if the temp is below 40, do command 1 (only once!). Then if the temp rises to above 40, it should do command 2 (but again only once!). When the temp drops again to below 40, it should do command 1 again (and again only once!).

How can this be done?

---

### Post by loell on 2008-04-15
probably

```
return False
``` 

 according to gtk doc

> The function is called repeatedly until it returns FALSE, at which point the timeout is automatically destroyed and the function will not be called again.

---

### Post by Nunslaughter on 2008-04-15
Then the whole loop will stop. It should keep checking for the temp, but the commands should only be executed once if the temp is above or below 40.

---

### Post by EXCiD3 on 2008-04-15
What if you use another variable to keep track of the previous temp recorded. If this value does not match (temp < 40) then it will know to display it. Do the same thing for the other one also and then you should only get the temp change displayed once :)

---

### Post by loell on 2008-04-15
yeah, just use a global or a static variable ,  for tracking :)

---

### Post by Siph0n on 2008-04-15
Just made this really quick, without testing... but get the idea?

```
first = True
over = True
def checktemp(self):
    if temp < 40 :
        if over == True:
           first = True
           over = False
        print "lower then 40"
        if first: 
            do command 1
            first = False
    else:
        if over == False:
           first = True
           over = True
        print "higher then 40"
        if first:
            do command 2
            first = False
    return True
```

---

### Post by Nunslaughter on 2008-04-15
Nope, he keeps doing the commands every second.

---

### Post by WW on 2008-04-15
Perhaps something like this...
[php]

prev_command = 0


def checktemp(self):
    if temp < 40 and prev_command != 1:
        print "lower than 40"
        # do a command 1
        prev_command = 1
    elif temp > 40 and prev_command != 2:
        print "higher than 40"
        # do command 2
        prev_command = 2
    return True
[/php]
(I also corrected the spelling. :) )

---

### Post by EXCiD3 on 2008-04-15
> **WW said:**
> Perhaps something like this...
[php]

prev_command = 0


def checktemp(self):
    if temp < 40 and prev_command != 1:
        print "lower than 40"
        # do a command 1
        prev_command = 1
    elif temp > 40 and prev_command != 2:
        print "higher than 40"
        # do command 2
        prev_command = 2
    return True
[/php](I also corrected the spelling. :) )

Yep thats what i was trying to recommend pretty much, only problem was i dont know any python so its hard to give an example :lolflag:

---

### Post by Nunslaughter on 2008-04-15
I have no idea why, but it doesn't work either. I still get the output of print and the command every second.


Then, than, all the same ;)

---

### Post by WW on 2008-04-15
It could be a scoping problem.  My code snippet was not necessarily working code.  prev_command must persist between calls.  Perhaps change it to self.prev_command.

---

### Post by EXCiD3 on 2008-04-15
nvm...lol

---

### Post by Nunslaughter on 2008-04-15
Damn, I already tried that, but made a typo. Tried again, and it seems that it works. I'll have a further look at it, but thanks already!

---

### Post by WW on 2008-04-15
> **Nunslaughter said:**
> 
Then, than, all the same ;)
Than I guess this sentence will bother you less then it bothers me. :-D

---

