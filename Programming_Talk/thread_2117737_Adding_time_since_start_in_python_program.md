---
title: "Adding time since start in python program"
date: 2013-02-19
forum: Programming Talk
---

### Post by huggies15 on 2013-02-19
Hi All,

Probably a basic question here, but I'm confusing myself with the time() function in python.

I want to add a column to the output of the following code with the time since the program was activated before the temperature given. This is so i get an output like

Time (s)     Temp (C)
0            30
15           34
30           45 etc

which i can then send to gnuplot to graphicise for me.
I got this code from the cambridge uni website (its for a simple raspberrypi project - and not much help on their forums).

```
# Copyright (c) 2012 Matthew Kirk
# Licensed under MIT License, see 
# http://www.cl.cam.ac.uk/freshers/raspberrypi/tutorials/temperature/LICENSE

import RPi.GPIO as GPIO
import time

LED1_GPIO_PIN = 18
LED2_GPIO_PIN = 25
BUTTON_GPIO_PIN = 17
GPIO.setmode(GPIO.BCM)
GPIO.setup(BUTTON_GPIO_PIN, GPIO.IN)
GPIO.setup(LED1_GPIO_PIN, GPIO.OUT)
GPIO.setup(LED2_GPIO_PIN, GPIO.OUT)

GPIO.output(LED1_GPIO_PIN, GPIO.HIGH)

while True:
	if GPIO.input(BUTTON_GPIO_PIN):
		break

while GPIO.input(BUTTON_GPIO_PIN):
	pass

GPIO.output(LED1_GPIO_PIN, GPIO.LOW)
GPIO.output(LED2_GPIO_PIN, GPIO.HIGH)

timestamp = time.strftime("%Y-%m-%d-%H-%M-%S")
filename = "".join(["temperaturedata", timestamp, ".log"])
datafile = open(filename, "w", 1)

measurement_wait = 15
button_pressed = False
while True:
	time_1 = time.time()
	tfile = open("/sys/bus/w1/devices/10-000802824e58/w1_slave")
	text = tfile.read()
	tfile.close()
	temperature_data = text.split()[-1]
	temperature = float(temperature_data[2:])
	temperature = temperature / 1000
	datafile.write(str(temperature) + "\n")
	time_2 = time.time()
	if (time_2 - time_1) < measurement_wait:
		no_of_sleeps = int(round((measurement_wait - (time_2 - time_1)) / 0.1))
		for i in range(no_of_sleeps):
			time.sleep(0.1)
			if GPIO.input(BUTTON_GPIO_PIN):
				button_pressed = True
				break
	if button_pressed:
		break
			

datafile.close()
GPIO.output(LED2_GPIO_PIN, GPIO.LOW)
```

I'm thinking i need something like:
```
datafile.write(time.time() + str(temperature) + "\n")
```

Am I also correct in thinking that the measurement_wait value is in seconds?

Any help would be gratefully received.
Steve

---

### Post by Tony Flury on 2013-02-19
> **huggies15 said:**
> Hi All,

Probably a basic question here, but I'm confusing myself with the time() function in python.

I want to add a column to the output of the following code with the time since the program was activated before the temperature given. This is so i get an output like

Time (s)     Temp (C)
0            30
15           34
30           45 etc

I'm thinking i need something like:
```
datafile.write(time.time() + str(temperature) + "\n")
```

Am I also correct in thinking that the measurement_wait value is in seconds?

Any help would be gratefully received.
Steve

using time.time() gives the number of seconds since the start of the EPOCH i.e. since 1st Jan 1970.

What you need to do is capture that value at the start of your program : 

```

prog_start = time.time()

```

And then wite the difference between it and time.time() into your data file : 

```
datafile.write(str(time.time()-prog_start) + "\t" + str(temperature) + "\n")
```

Noticed i added a tab character between your two values - you will need a space or tab or something to separate them.

---

### Post by huggies15 on 2013-02-19
Awesome! Thanks so much! I was getting confused with the whole EPOCH thing and couldnt work out how to set a T0.
Cheers,
Steve

---

