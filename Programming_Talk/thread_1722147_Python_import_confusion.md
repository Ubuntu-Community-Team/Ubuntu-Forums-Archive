---
title: "Python import confusion"
date: 2011-04-05
forum: Programming Talk
---

### Post by ahayzen on 2011-04-05
Hi newbie to python here.

I am trying to get an imported class to talk back to the original class but can't get it to work.

Here is a simple example of my problem:

main.py
```
#!/usr/bin/env python
from sub import sub

class top:
    def __init__(self):
        print "Loaded Top"
        
    def printmsg(self, msg):
        print msg

top = top()
sub.printmsg("TEST")
```

sub.py
```
#!/usr/bin/env python
class sub:
    def __init__(self):
        print "Loaded Sub"
        
    def printmsg(self, msg):
        top.printmsg(msg)

sub = sub()
```

If you are wondering why i would need this, I am writing a musicplayer application but I need the library class to talk back to the gui class.

I have used PHP a lot and am used to the include function but I can't seem to get python to work. I have tried using 'main' as a separate class and importing that in a overall file but then it still doesn't work and just loops.

The error I get is:
top.printmsg(msg)
NameError: global name 'top' is not defined

So to me it seems that the scope from the main file is not being show to the sub file.

Can someone please guide me into how to solve this problem?

Thanks in advance.

Andy

---

### Post by cgroza on 2011-04-05
Have your top and sub class in separate files.

Include top into four sub file and use it from there(make sure you create an instance of it first).
You can do the rest into your main method which is in a separate file.

---

### Post by simeon87 on 2011-04-05
It doesn't work like PHP include, that confused me at first too.

The following should work:

top.py:

```

#!/usr/bin/env python
from sub import sub

class top:
    def __init__(self):
        print "Loaded Top"
        
    def printmsg(self, msg):
        print msg

top = top()
top.printmsg("TEST")
sub = sub()
sub.printmsg(top, "TEST")

```
sub.py:
```

class sub:
    def __init__(self):
        print "Loaded Sub"
        
    def printmsg(self, top, msg):
        top.printmsg(msg)

```

---

### Post by ahayzen on 2011-04-05
Thanks for you suggestions.
[cgroza]("http://ubuntuforums.org/member.php?u=917016"): I had tried using your method before however I came upon some issues.

The main issues was that it created a look because in my classes.

GUI needed to include Musicplayer, but Musicplayer needed to include GUI so it just seemed to loop and then fail when trying to import the module for the second time.

Have you got any idea why it would do this?

[simeon87]("http://ubuntuforums.org/member.php?u=772130"): Your method works very well! However this is a little messy.

Overall I would like it if [cgroza]("http://ubuntuforums.org/member.php?u=917016")'s method could work but if I can't get it to work then I will have to settle for [simeon87]("http://ubuntuforums.org/member.php?u=772130")'s method.

Thanks for your suggestions :)

Andy

---

### Post by ahayzen on 2011-04-05
Hi 

I have created an example of [cgroza]("http://ubuntuforums.org/member.php?u=917016")'s method but with calls both from top->sub and sub->top

main.py
```
#!/usr/bin/env python
from top import top
top.printmsg("TEST")
```

top.py
```
#!/usr/bin/env python
from sub import sub
class top:
    def __init__(self):
        print "Loaded Top"
        
    def printmsg(self, msg):
        sub.setmsg(msg)
        sub.printmsg()

top = top()
```

sub.py
```
#!/usr/bin/env python
from top import top
class sub:
    def __init__(self):
        print "Loaded Sub"
    
    def setmsg(self, msg):
        self.msg = msg    
    
    def printmsg(self):
        top.printmsg(self.msg)

sub = sub()
```

This is the output:
Traceback (most recent call last):
  File "/home/andy/Code/python/moduletest/main.py", line 3, in <module>
    from top import top
  File "/home/andy/Code/python/moduletest/top.py", line 2, in <module>
    from sub import sub
  File "/home/andy/Code/python/moduletest/sub.py", line 2, in <module>
    from top import top
ImportError: cannot import name top

As I said it seems to stop on the second import of the same class. If anyone could solve this issue then my question would be resolved. Otherwise if there is no solution to this I will use [simeon87]("http://ubuntuforums.org/member.php?u=772130")'s method.

Thanks in advance.

Andy

P.S. [simeon87]("http://ubuntuforums.org/member.php?u=772130"): the reason I said it is messy is that I will have to send over the class each time I need it in a function, I wish there was just a include function like PHP :)

---

