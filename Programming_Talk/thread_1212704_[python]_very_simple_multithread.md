---
title: "[python] very simple multithread"
date: 2009-07-14
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-14
Hey,

Here is the basic operation that i need..

```

global variable
variable = true

def reset():
\tvariable=False

##Needs to be run on a separate thread so program can continue after this
time.sleep(10)
reset()
##Now continue on with the rest of the program

while 1:
\tprint variable
\ttime.sleep(0.2)

```

After 10 seconds it would change the variable from true, to false but it would have already started printing out False... I hope it makes sense a little bit.. i can try and explain more if you need it

Thanks
~Cody Woolaver

---

### Post by Godd on 2009-07-14
I tried a very similar thing, but when I tried to pass a global variable(set equal to sys.argv[1]) it didn't work.

[PHP]
global char_select
char_select = sys.argv[1]
global pass_length
pass_length = sys.argv[2]

class gen(threading.thread)

    def _init_(self,char_select,pass_length):

        self.char_select = char_select
        self.pass_length = pass_length

    def run(self)
        pass

generator = gen()
generator.start()[/PHP]

run(self) is something more than pass, but it wouldn't make sense without posting a majority of it and it's rather large. But it does use both of the global variables.

---

### Post by Pyro.699 on 2009-07-14
Got it :)

[php]
import time, threading

variable = True

def reset():
    global variable
    variable = False
    
class resetClass(threading.Thread):
    def run(self):
        time.sleep(2)
        reset()

t = resetClass()
t.start()

while 1:
    print variable
    time.sleep(0.2)
[/php]Thanks
~Cody Woolaver

---

