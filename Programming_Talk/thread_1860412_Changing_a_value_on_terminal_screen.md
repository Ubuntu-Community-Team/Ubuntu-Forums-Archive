---
title: "Changing a value on terminal screen"
date: 2011-10-14
forum: Programming Talk
---

### Post by mushy365 on 2011-10-14
You know how when you create a python program, and it outputs content to terminal. Every time i use the print call it adds a new line below and clutters up the screen, is there a way of just updating one line i.e if you are downloading a file 

at the minute mine looks like this 
> 1/100 1%
> 2/100 2%
> 3/100 3%

is there any way of having it just update the first line?

---

### Post by Smart Viking on 2011-10-14
It becomes much more complex very fast when doing that, but this would do it:

```

from sys import stdout
import time

i = 1
while i < 4:
  stdout.write("\r%s/100 %s" % (i,i) + "%")
  i += 1
  stdout.flush()
  time.sleep(0.5)

print "\nhayhay"


```

First you write data, then you "flush" it, to refresh the terminal or whatever.

---

### Post by mushy365 on 2011-10-14
i sort of found out about this before seeing reply, id like to add a sleep, but im using it with a file transfer and it updates everytime  a packet is recieved. I dont want to sleep 0.5 secs between packet recieves so dont know how to do it

---

### Post by ziekfiguur on 2011-10-15
The sleep is just there to make it go slow enough for you to see the effect, you don't have to use it in your own program.
Here is some code I used a while ago to do somethign similar, it creates a progressbar on the terminal
```
import sys
import time
from fractions import Fraction as frac

class Progress:
    def __init__(self, total, width, out=sys.stdout):
        self.total = total
        self.width = width
        self.progress = 0
        self.progress2 = frac()
        self.delta = frac(self.total, self.width)
        self.out = out
        self.out.write('\033[?25l[{0:s}]\033[{1:d}D\033[34m'.format(' ' * self.width, self.width + 1))
        self.out.flush()

    def _step(self):
        self.out.write('*')
        self.out.flush()

    def _stop(self):
        self.out.write('\033[0m]\n\033[?25h')
        self.out.flush()

    def cycle(self):
        self.progress += 1
        self.progress2 += 1
        if self.progress <= self.total:
            while self.progress2 >= self.delta:
                self.progress2 -= self.delta
                self._step();
        if self.progress == self.total:
            self._stop()
            self.progress += 1
```
To use it do something similar to this:
```
cycles = 100
pr = Progress(cycles, 60)
for i in range(cycles):
    pr.cycle()
    time.sleep(0.1)

```
Just create a Progress object with the amount of steps your process is going to take (in your case i think 100) and the width of the progressbar.
Than just call cycle every once in a while, and make sure not to have any other output before it's done.

---

### Post by nvteighen on 2011-10-15
I highly discourage the use of ASCII escapes, because they can work differently in different terminals... or even worse, they may not work even in the same terminal with different settings.

I know it may be sort of killing a bird with a cannon, but try using ncurses (Python's module is called curses... it's a core module). Even though it requires you loading a somewhat big library that requires you to write some nasty boilerplate initialization code, it makes this much simpler in a way that is guarranteed to work in any ncurses compatible terminal and console (all of the ones available in a normal GNU/Linux system).

---

