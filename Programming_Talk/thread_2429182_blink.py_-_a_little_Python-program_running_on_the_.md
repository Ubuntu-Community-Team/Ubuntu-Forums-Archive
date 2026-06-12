---
title: "blink.py - a little Python-program running on the ESP8266"
date: 2019-10-14
forum: Programming Talk
---

### Post by dilbert_one on 2019-10-14
hi there  good evening, 

the topic today: blink.py - a little Python-program running on the ESP8266


i am running this code on a ESP 8266 

```



import RPi.GPIO as GPIO
import time
GPIO.setmode(GPIO.BCM)
GPIO.setup(18, GPIO.OUT)
while True:
	GPIO.output(18, GPIO.HIGH)
	time.sleep(1)
	GPIO.output(18, GPIO.LOW)
	time.sleep(1)



```





with the following 


```



>>> import sys
>>> print ('Hello World')
Hello World
>>> os.stat('./boot.py')
(32768, 0, 0, 0, 0, 0, 230, 2, 2, 2)
>>> print ('Hello World')
Hello World
>>> print ('Hello World')
Hello World
>>> print ('Hello World')
Hello World
>>> 
>>> 




```

which outputs this 




```



>>> 


Ready to download this file,please wait!
..
download ok
exec(open('blink.py').read(),globals())
program is running,do anything with stop it!1
program is running,do anything with stop it!1
program is running,do anything with stop it!1
program is running,do anything with stop it!1
program is running,do anything with stop it!1
program is running,do anything with stop it!1
program is running,do anything with stop it!1



```



[/CODE]

---

