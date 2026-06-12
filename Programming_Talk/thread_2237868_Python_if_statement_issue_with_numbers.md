---
title: "Python if statement issue with numbers"
date: 2014-08-04
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2014-08-04
so i have a loop i can counting when it reaches 5 or 10 i want it to do something different
my issue is with the line "[FONT=courier new]if cnt == 0 or cnt == 5 or cnt == 10:[/FONT]"
it only return true on when cnt is 0 i have tried 5 and 5.0 nigher returned true when the count reached 5/5.0
```
#!/usr/bin/python
import RPi.GPIO as GPIO
import time

pin = 19
pin2 = 21
GPIO.setmode(GPIO.BOARD)
GPIO.setup(pin, GPIO.IN, pull_up_down=GPIO.PUD_DOWN)
GPIO.setup(pin2, GPIO.OUT)
delay = 0.1

try:
        while True:
                cnt = 0
                while GPIO.input(pin) == 1:
                        if cnt == 0 or cnt == 5 or cnt == 10:
                                print cnt
                                GPIO.output(pin2, 1)
                                time.sleep(delay)
                                GPIO.output(pin2, 0)
                                cnt=cnt+delay
                                time.sleep(cnt)
                        else:
                                cnt=cnt+delay
                                time.sleep(delay)
                if cnt > 5 and cnt < 10:
                        # 5 to 10 seconds
                        print "5"
                elif cnt > 9:
                        # 10 seconds or more
                        print "10"
                elif cnt > 0:
                        # Less than 5 seconds
                        print "0"
                time.sleep(delay)
except KeyboardInterrupt:
        GPIO.cleanup()
```
I have also tried this, still only works on 0
[FONT=courier new]if cnt in [0, 5, "5.0", 5.0,  10, "10.0", 10.0]:[/FONT]

---

### Post by ofnuts on 2014-08-04
Your problem is comparing a plain int (0, 5, 10) with a float which is the result of computations and may not be exactly equal to 5.00000000000000000 or 10.0000000000000000. Try this:

```

cnt=0
delay=.1
for i in range(50):
  x=x+delay
  print '%3.20f' % x

```

---

### Post by kostkon on 2014-08-04
Did you put cnt = 0 in the while loop just for testing?
```
        while True:
                cnt = 0
```

---

### Post by pqwoerituytrueiwoq on 2014-08-04
> **kostkon said:**
> Did you put cnt = 0 in the while loop just for testing?
```
        while True:
                cnt = 0
```

to reset the cnt varable before testing it again

---

### Post by pqwoerituytrueiwoq on 2014-08-04
> **ofnuts said:**
> Your problem is comparing a plain int (0, 5, 10) with a float which is the result of computations and may not be exactly equal to 5.00000000000000000 or 10.0000000000000000. Try this:

```

cnt=0
delay=.1
for i in range(50):
  x=x+delay
  print '%3.20f' % x

```
still nothing :(
```
#!/usr/bin/python
import RPi.GPIO as GPIO
import time

pin = 19
pin2 = 21
GPIO.setmode(GPIO.BOARD)
GPIO.setup(pin, GPIO.IN, pull_up_down=GPIO.PUD_DOWN)
GPIO.setup(pin2, GPIO.OUT)
delay = 0.1
five='%3.20f' % 5
ten='%3.20f' % 10
try:
        while True:
                cnt = 0
                while GPIO.input(pin) == 1:
                        if cnt in [0, five, 5, 5.0, "5.0", ten, 10, 10.0, "10.0"]:
                                print "Hello"
                                GPIO.output(pin2, 1)
                                time.sleep(delay)
                                GPIO.output(pin2, 0)
                                cnt=cnt+delay
                        else:
                                cnt=cnt+delay
                                time.sleep(delay)
                if cnt > 5 and cnt < 10:
                        # 5 to 10 seconds
                        print "5 - done"
                elif cnt > 9:
                        # 10 seconds or more
                        print "10 - done"
                elif cnt > 0:
                        # Less than 5 seconds
                        print "0 - done"
                time.sleep(delay)
except KeyboardInterrupt:
        GPIO.cleanup()
        print "\n"
```

---

### Post by pqwoerituytrueiwoq on 2014-08-04
found a solution :)
[http://stackoverflow.com/questions/6209008/checking-if-float-is-equivalent-to-an-integer-value-in-python](http://stackoverflow.com/questions/6209008/checking-if-float-is-equivalent-to-an-integer-value-in-python)
```
#!/usr/bin/python
import RPi.GPIO as GPIO
import time

def equal_float(a, b):
        return abs(a - b) <= 0.00000000001

pin = 19
pin2 = 21
GPIO.setmode(GPIO.BOARD)
GPIO.setup(pin, GPIO.IN, pull_up_down=GPIO.PUD_DOWN)
GPIO.setup(pin2, GPIO.OUT)
delay = 0.1

try:
        while True:
                cnt = 0
                while GPIO.input(pin) == 1:
                        if cnt == 0 or equal_float(cnt, 5) or equal_float(cnt, 10):
                                GPIO.output(pin2, 1)
                                time.sleep(delay)
                                GPIO.output(pin2, 0)
                                cnt=cnt+delay
                        else:
                                cnt=cnt+delay
                                time.sleep(delay)
                if cnt > 5 and cnt < 10:
                        # 5 to 10 seconds
                        print "5 - done"
                elif cnt > 9:
                        # 10 seconds or more
                        print "10 - done"
                elif cnt > 0:
                        # Less than 5 seconds
                        print "0 - done"
                time.sleep(delay)
except KeyboardInterrupt:
        GPIO.cleanup()
        print "\n"
```

---

### Post by ofnuts on 2014-08-04
> **pqwoerituytrueiwoq said:**
> found a solution :)
[http://stackoverflow.com/questions/6209008/checking-if-float-is-equivalent-to-an-integer-value-in-python](http://stackoverflow.com/questions/6209008/checking-if-float-is-equivalent-to-an-integer-value-in-python)


Yes, this is the very same explanation I was mentioning... but in your case this isn't a very good solution. You should change your logic to count the number of times you use the delay, so you would compare integers to integers.

---

