---
title: "Python program execution time"
date: 2009-08-23
forum: Programming Talk
---

### Post by nipunreddevil on 2009-08-23
I need to output time taken by various functions in a python program.Have not been able to find an easy enough example on using profilers.Can we use some other way without using profilers,something like clock() in Turbo C.Please give an example regarding both approches as it will be extremely helpful and will solve lots of problems for me

---

### Post by CptPicard on 2009-08-23
Well, look at the "time" module... time.time() at least gives a nice float-point number for you to use. You can write a simple higher-order function that times the given function's execution with the given arguments... this is a simple exercise.

---

### Post by nipunreddevil on 2009-08-23
Thanks for telling about it,but time function gives different results almost everytime.
```

import time
a=time.clock()

for i in range(1,100):
	for j in range(1,100):
		print i*j
b=time.clock()
print b
print a

```
Now for this i get different values of b with the same program and same dataset.Is this a foolproof method of analyzing algos

---

### Post by nipunreddevil on 2009-08-23
Even using time.time() gives inconsistent results.```

import time
a=time.time()

for i in range(1,100):
	for j in range(1,100):
		print i*j
b=time.time()
print b
print a

```
Now logically b-a should always be same for same data set,but thats not the case.
And moreover the multiplication seems to take less time as compared to addition.Thats quite strange.

---

### Post by wmcbrine on 2009-08-23
First of all, what you're primarily timing with that code is the print statement, which is far slower than the multiplication. Second, if you want to get a meaningful time for multiplication, you need much higher loop values.

---

### Post by spupy on 2009-08-23
Just for exercise I wrote a function decorator that clocks the execution time of the function it decorated.
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
import time

class TimerDecorator():
    timer_func = time.time

    def __init__(self, f):
        self.func = f

    def __call__(self):
        """
            Runs the decorated function. The two return values are the return value of the function and its execution time.
        """
        start_time = self.timer_func()
        return_value = self.func()
        finish_time = self.timer_func()
        exec_time = finish_time - start_time
        return return_value, exec_time
```
It may not be state-of-the-art, I just hacked it together in 5 minutes. You use it like this:
```
@TimerDecorator
def my_func(...):
    ...

return_value, exec_time = my_func()
```
I'm not sure if it works with functions that return multiple values. Later I will test this as well.

---

