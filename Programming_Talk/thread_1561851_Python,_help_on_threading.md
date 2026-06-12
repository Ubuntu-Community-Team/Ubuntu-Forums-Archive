---
title: "Python, help on threading"
date: 2010-08-26
forum: Programming Talk
---

### Post by fokuslee on 2010-08-26
Hi im learning python out of hobby, so more explaination the better.  I need help understanding this threading example. 

```
#!/usr/bin/python

import threading
import time

exitFlag = 0

class myThread (threading.Thread):
    def __init__(self, threadID, name, counter):
        self.threadID = threadID
        self.name = name
        self.counter = counter
        threading.Thread.__init__(self)
    def run(self):
        print "Starting " + self.name
        print_time(self.name, self.counter, 5)
        print "Exiting " + self.name

def print_time(threadName, delay, counter):
    while counter:
        if exitFlag:
            thread.exit()
        time.sleep(delay)
        print "%s: %s" % (threadName, time.ctime(time.time()))
        counter -= 1

# Create new threads
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)

# Start new Threads
thread1.start()
thread2.run()

while thread2.isAlive():
    if not thread1.isAlive():
        exitFlag = 1
    pass
print "Exiting Main Thread"

```

Q1: why thread1.start()and thread2.run(), does that mean thread1 becomese the main thread? 

Q2: in the print_time fn, inside while loop 
there is the if statement, if exitflag: thread.exit() wouldn't that terminate thread 2 before the counter goes down to zero?

Any help is appreciated. Im stuck :popcorn:

---

### Post by StephenF on 2010-08-26
thread2 is never started since all you did was directly call the run method you provided.

I don't understand this thread.exit() a simple break or return statement would break the loop allowing the thread to finish. An exception could be used in more complex code to the same effect.

---

### Post by smartbei on 2010-08-27
If you want to start a thread as a thread (and not have run it as a function in the main thread), you need to call it's start method.

Try this - stick a long loop in a thread, and see how it works then. For example:
```

class MyThread(threading.Thread):
    def run(self):
        for a in xrange(30000000):
            pass

t = MyThread()
print "Should print immediately..."
t.start() # does not block
print "Yep!"

print "Should take a while..."
t2 = MyThread()
t2.run() # blocks
print "Yep!"

```

As for thread.exit - In the print_time function, thread is undefined, so I am not sure what is intended by thread.exit(). See above post for simpler  options for exiting the thread.

---

### Post by fokuslee on 2010-08-27
thanks for the explaination on run vs start, that was great

---

