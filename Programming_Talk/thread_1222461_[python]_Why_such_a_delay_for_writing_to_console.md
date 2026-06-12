---
title: "[python] Why such a delay for writing to console?"
date: 2009-07-24
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-24
Hey,

I noticed a few days ago that when i ran a program which did calculations and had no printing done, it went much... and by much (and by much, i mean by several magnitudes) faster. So here's what i did.

[php]
import time, threading, sys

skip = False

def reset():
    global skip
    skip = True
    
class resetClass(threading.Thread):
    def run(self):
        time.sleep(2)
        reset()

a = resetClass()
a.start()
x = 0
while (not skip):
    x += 1

b = resetClass()
b.start()
skip = False
y = 0
while (not skip):
    y += 1
    print y

c = resetClass()
c.start()
skip = False
z = 0
while (not skip):
    z += 1
    sys.stdout.write(str(z))

print
print
print
print "The results were:\n X: %i\n Y: %i\n Z: %i" % (x,y,z)
[/php]

You should be able to see what i did.
**X** will be calculations with no output
**Y** will be calculations using **print**
**Z** will be calculations using **sys.stdout.write**

My results were:
**X:** 14851378
**Y**: 10073
**Z**: 21988

With no print it was almost 1500 time as fast. And using sys.stdout.write was twice as fast as using print.

Why? It seems like it wouldn't be much of a process to print single characters to a console or terminal? I'm obviously quite wrong, but i was more curious as to why and whats going on behind the scenes that takes up so much time.

Thanks for your input
~Cody Woolaver

---

### Post by Can+~ on 2009-07-24
(Disclaimer: I'm not 100% sure about this, don't take my word, I tried googling but no interesting results)

I think the problem lies that I/O operations are slow (in the eyes of the processor). Doing an I/O must raise an interruption signal to send or retrieve data from/to a device. This is something that has to do with hardware, and even with assembly you must do it.

[PHP]
move        $a0, $s0    # Value to print        (move = Move registry)
li          $v0, 1      # Print instruction (1) (li = Load immediate)
syscall                 # System Call[/PHP]
(MIPS assembly)

The fact that sys.stdout.write works faster might be that python automatically buffers certain file operations, therefore, having a buffer and having less interruptions improves the performance.

The easiest solution is the one you already figured, crunch all the numbers and finally print the result.

---

### Post by lswb on 2009-07-24
I might be wrong here but it seems to me that the raster nature of the screen means that adding new visible characters can occur only during screen refresh which happens in the neighborhood of 60 to 80 times per second. I am over simplifying by ignoring buffering, but whenever the program writes to the screen, it pauses til that write is complete.

---

### Post by CptPicard on 2009-07-24
No, it doesn't... even if we were still working on that level, the screen character buffer in video memory is separate from the screen refresh rate. That is, you do not wait for a sync from screen to get to write to video memory (I do remember actually doing this for graphics back in the day when I was writing some stuff on top of DOS...)

But, these days it's much more complex and more layered. As a matter of fact, some X terminal emulator programs are awfully slow to render large amounts of text in their own right -- just try the difference between plain xterm and something like konsole.

---

### Post by lswb on 2009-07-25
> **CptPicard said:**
> No, it doesn't... even if we were still working on that level, the screen character buffer in video memory is separate from the screen refresh rate. That is, you do not wait for a sync from screen to get to write to video memory (I do remember actually doing this for graphics back in the day when I was writing some stuff on top of DOS...)

But, these days it's much more complex and more layered. As a matter of fact, some X terminal emulator programs are awfully slow to render large amounts of text in their own right -- just try the difference between plain xterm and something like konsole.

OK, but writing to standard output is not the same as writing to screen memory. What happens when the standard output from a program is coming fast enough to completely fill the screen buffer and any intermediate buffers? If it just starts overwriting the buffer, wouldn't some of the output be lost, and not viewable by scrolling back the terminal?

---

### Post by Pyro.699 on 2009-07-25
That is very interesting (all of your comments)...

Its somewhat interesting how we can add 1+1 in a matter of nano seconds, but it takes microseconds to display that. I just find it all quite interesting ^^;

---

### Post by slavik on 2009-07-25
So, you want to print to the terminal. The vm now has to convert the number type to a string. Then it has to move this new string to some other place in memory. Finally, call some underlying function to read it and display it through the terminal driver.

This is without doing something like C's printf's read the format to decide how to print/convert things. (which might be done by the python vm, but we don't know that ... who has the code?).

try doing print and redirecting to a file ;)

---

