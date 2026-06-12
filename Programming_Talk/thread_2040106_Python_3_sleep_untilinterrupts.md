---
title: "Python 3 sleep until/interrupts"
date: 2012-08-10
forum: Programming Talk
---

### Post by Superpelican12 on 2012-08-10
Is there a way to let Python (3) sleep (or do something else) until something happens and than call a function. I've read on wikipedia what interrupts are but can't seem to find how to implement them in Python(3). Isn't there something like this in Python:
```

until <mystatement>:
 <mycode>
<the code that executes after something happens> 

```
for example:
```

until a == 10:
 sleep()

print("An event occured!")

```
or something like this:

```

sleep(until <a_signal>)
on <a_signal> do:
 <mycode>

```
Using a loop and if statements (or only a while loop) causes a very high CPU usage, which of course is completely unnecessary because the program doesn't have to do anything.

---

### Post by Bachstelze on 2012-08-10
sleep() calls the sleep system call via the sleep() C function. It can be interrupted only by sending a signal to the Python process. For example:

```
firas@itsuki ~ % cat test.py 
from time import sleep
try:
        sleep(100)
except KeyboardInterrupt:
        pass
print("Waking up.")
firas@itsuki ~ % python3 test.py 
Waking up.
firas@itsuki ~ % 
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
firas@itsuki ~ % ps aux | grep python
firas     7456  2.0  0.2  12460  5688 pts/9    S+   14:25   0:00 python3 test.py
firas     7466  0.0  0.0   4372   772 pts/10   S+   14:25   0:00 grep --color=auto python
firas@itsuki ~ % kill -2 7456
firas@itsuki ~ % 

```

(kill -2 sends SIGINT, which is also the signal sent by a press on Ctrl+C, hence why I catch KeyboardInterrupt.)

A more Pythonic approach would be to use the facilities provided by the Threading module. Basically, create a thread that goes to sleep and have the main thread wake it up. See [http://docs.python.org/py3k/library/threading.html#event-objects](http://docs.python.org/py3k/library/threading.html#event-objects)

---

