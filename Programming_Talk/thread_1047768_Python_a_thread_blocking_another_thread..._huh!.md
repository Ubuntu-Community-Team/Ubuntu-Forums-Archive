---
title: "Python: a thread blocking another thread... huh?!"
date: 2009-01-22
forum: Programming Talk
---

### Post by NetSkay on 2009-01-22
ok... i was programming today and i wanted to add terminal input feature to a socket client...
naturally, the client has a thread that has a blocking recv socket... however, i knew if i wanted to add terminal input to the client itd have to separate both, so i figured ill start a separate thread with raw_input, the problem is that ones i start the thread with raw_input, the client can no longer receive commands, but ones i type something in the client terminal then is the command executed... wierd... any ideas?!

---

### Post by slavik on 2009-01-22
python has something called GIL Global Interpreter Lock. This stop python from executing 2 or more threads at the simultaneously. Try jython or ironpython if you need simultaneous threads in python.

---

### Post by NetSkay on 2009-01-22
well i know of the lock... but i mean, why would python (classic) have threads that can NOT run "parallel" and independent, like in my case where both threads block on diff methods...

---

### Post by slavik on 2009-01-22
because of the lock ... there is no other explanation. within the Python virtual machine, there is only 1 thread being run at a time.

---

### Post by NetSkay on 2009-01-26
i get lost in confusion...
since im using raw_input in a totally different thread, then the system should multiplex between and not cause one thread to block the other...
or is it that just python interpreter has been designed bad?

---

### Post by slavik on 2009-01-26
maybe that's how raw_input is designed, I don't know what to tell you, I didn't write the Python interpreter. I would suggest asking in a Python mail list or usenet group.

---

### Post by The Cog on 2009-01-26
Slavik is mistaken. There is a GIL but it doesn't prevent a second thread from running until the first is finished - that would be silly. It ensures that two threads can't modify the same object at the same time by only allowing one thread to be executing at any instant. But in interleaves running threads by switching between them. 

I don't know what your problem is but this code example happily accepts both keyboard and socket input.

```

import socket
import threading

def listen():
    s = socket.socket()
    s.bind(("0.0.0.0", 9999))
    s.listen(3)
    print "listening"
    while True:
        x, y = s.accept()
        print "Got connection from", y
        x.send("------Goodbye--------\n")
        x.close()


t = threading.Thread(target=listen)
t.start()
print "waiting for kbd"
while True:
    s = raw_input()
    print "Keyboard says", s



```


Aah, it occurs to me. Are you perhaps calling the thread's run() method instead of its start() method? run() doesn't start a new thread - it does its work in the context of the calling thread thus trapping it until the run() method terminates. The start() method is the right one to use. start() starts a new thread (which calls run()) and returns immediately, to allow the caller and the new thread to go their separate ways.

---

### Post by slavik on 2009-01-26
thanks for the corrections ... another thing I learn about Python without ever having written any real code in it :D

---

