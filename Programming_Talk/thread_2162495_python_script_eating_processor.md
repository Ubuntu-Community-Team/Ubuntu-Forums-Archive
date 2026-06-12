---
title: "python script eating processor"
date: 2013-07-14
forum: Programming Talk
---

### Post by wingnut2626 on 2013-07-14
```
import osimport timedef getWeather(interval):	a = int(time.time()) + int(interval)	b = int(time.time())	dataFile = open('/sdcard/weather.txt','a')	while b < a:		b = int(time.time())		continue	b = '-' * 50	c = '\n'	dataFile.write(b)	os.popen2('metar -d KILG >> /sdcard/weather.txt')	dataFile.write(b)	dataFile.write(c)	a = 0def initiateSequence():	print 'Time between readings?'	elapse = raw_input('>')	while True:		getWeather(elapse)if __name__ == '__main__':	initiateSequence()
```when i run this as a program from the bash shell, my processor usage is 100% on that program. Any way to cut it down?

---

### Post by wingnut2626 on 2013-07-14
how come my code is not posting vertically?

---

### Post by trent.josephsen on 2013-07-14
It almost certainly has to do with how you're copying it. It might be your editor. Without more information that's as much as I can say. With that in mind, this is exactly what the preview button is for -- so you can see how your post will look before submitting it. Proofread, and if you're having a technical problem posting code make a new thread about that.

---

### Post by alan9800 on 2013-07-14
this should be the code```
[COLOR=#000000][FONT=Ubuntu Mono]import os
import time

def getWeather(interval):
    a = int(time.time()) + int(interval)
    b = int(time.time())
    dataFile = open('/sdcard/weather.txt','a')
    while b < a:
        b = int(time.time())
        continue
    b = '-' * 50
    c = '\n'
    dataFile.write(b)
    os.popen2('metar -d KILG >> /sdcard/weather.txt')
    dataFile.write(b)
    dataFile.write(c)
    a = 0

def initiateSequence():
    print 'Time between readings?'
    elapse = raw_input('>')
    while True:
        getWeather(elapse)

if _name__ == '__main__':
    initiateSequence()[/FONT][/COLOR]
```

---

### Post by prodigy_ on 2013-07-14
Any particular reason for using python over bash? I don't see anything here that bash couldn't accomplish.

Anyway
```
while True:
```
is what eats CPU. You need to add **time.sleep(<number>)** somewhere.

---

### Post by alan9800 on 2013-07-15
> **wingnut2626 said:**
> how come my code is not posting vertically?you might use [ideone]("http://ideone.com"), an online editor for a lot of programming languages.
It allows you to test immediately your code.
That said, why do you use os.popen instead of [subprocess]("http://docs.python.org/release/2.7.3/library/subprocess.html#module-subprocess")?

---

### Post by alan9800 on 2013-07-15
the following link shows a tip for controlling CPU and RAM usage:
[http://stackoverflow.com/questions/276052/how-to-get-current-cpu-and-ram-usage-in-python/278271#278271](http://stackoverflow.com/questions/276052/how-to-get-current-cpu-and-ram-usage-in-python/278271#278271)

---

### Post by ofnuts on 2013-07-15
What kiils your CPU is this:

```

w[COLOR=#000000][FONT=Ubuntu Mono]hile b < a:         
   b = int(time.time())         
   continue
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
In other words you run a tight loop while waiting for the end of the interval. use sleep(interval) instead as suggested above.

[/FONT][/COLOR]

---

### Post by Bodsda on 2013-07-15
I won't comment on the CPU usage as others have already covered that, but here is my list of issues in that code
[LIST]
[*]non-descriptive variable names
[*]pointless variables used once
[*]reuse of variable names
[*]why reset 'a' back to 0
[*]use subprocess instead of popen2
[*]using a while loop to wait for a time period means unnecessary calls to time.time - use time.sleep instead
[*]you have 3 calls to file.write - If you read in your metar results you could simplify it to 1 write
[/LIST]


[LIST]
[/LIST]

---

### Post by wingnut2626 on 2013-07-15
Thanks guys for the help

---

