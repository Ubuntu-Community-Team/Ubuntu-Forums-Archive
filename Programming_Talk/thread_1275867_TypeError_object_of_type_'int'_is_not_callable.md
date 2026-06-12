---
title: "TypeError: object of type 'int' is not callable"
date: 2009-09-26
forum: Programming Talk
---

### Post by tom66 on 2009-09-26
The following python program is my attempt to teach me how to use multiprocessing in python. Note at the moment, I'm using an older version of the multiprocessing library and it's called processing. 

```

#!/usr/bin/python
import processing as _pthread
import psyco, math, time
psyco.full()

class PrimeThread(_pthread.Process):
    def __init__(self, start, step, thread_num):
        self.thread_num = thread_num
        self.max = 5000000
        self.start = start
        self.step = step
        self.primes = [0 for i in range(self.max)]
        _pthread.Process.__init__(self)
    
    def test_prime(self, num):
        prime = True
        for i in xrange(2, math.sqrt(num) + 1):
            # print "does %d divide into %d?" % (i, num)
            if num % i == 0:
                prime = False
                break
        return prime
    
    def run(self):
        n = 0
        for i in xrange(self.start, self.max, self.step):
            if self.test_prime(i) == True:
                self.primes[n] = i
                n += 1
        print "Thread %d finished; found %d primes." % (self.thread_num, n)

def main():
    # 2 is not shown by any of the outputs, so show it here.
    # print "2",
    
    # Create many threads.
    thread_count = 2
    for i in range(thread_count):
        PrimeThread(3 + (2 * i), (2 * thread_count), i).start()

if __name__ == '__main__':
    main()

```

I get an error:

```

Traceback (most recent call last):
  File "test.py", line 42, in <module>
    main()
  File "test.py", line 39, in main
    PrimeThread(3 + (2 * i), (2 * thread_count), i).start()
TypeError: object of type 'int' is not callable

```

Much appreciated if anyone could tell me what's happening.. I can't figure it out. Oddly, using .run() instead of .start() works but then I don't get my multiprocessing. :(

I'm using a dual core machine, if this works, both cores should shoot up to 100%.

---

### Post by nvteighen on 2009-09-26
It's obvious... the PrimeThread object's **start** attribute is not a function... Follow how you're calling the constructor and you'll spot the error.

---

### Post by tom66 on 2009-09-26
Thanks ... spotted my silly error. :) I'm overriding the processing.Process.start() definition with an int, causing the error. Much appreciated.

---

