---
title: "PySerial issues controlling a step motor, screen works tho...."
date: 2013-05-22
forum: Programming Talk
---

### Post by wannabegeek on 2013-05-22
Hi all...

I find myself coming back here b/c this is thee place to get help... :)

I am setting up a scientific application using step motors and my system runs with Ubuntu 10.04. I already control a HP Network analyzer with 
a linux based python wrapped gpib library.

Now I need to control the step motors with Python too.....the whole world appears to use Windoze for this. My project controls two MDrive 23 step motors
which come with builtin drivers that read commands from a ASCII terminal emulator, like screen.

Screen connects to the motors just fine:
```
screen /dev/ttyUSB0
``` 

and I've been able to get PySerial to connect too, using:

```

import serial

motor = serial.Serial( port ='/dev/ttyUSB0', baud=9600, timeout=0)
motor.write('MR 123456\r\n')
motor.close()

```

This code will move my motors....but when I try to set a user variable, like the Device Name (DN), I can only set it once. Any other attempts to set
a variable ( any of them ) results in the motor outputting a '?'  which indicates an error.

```

import serial

motor = serial.Serial( port ='/dev/ttyUSB0', baud=9600, timeout=0)
motor.write('DN\075"X"\r\n') # using the ascii code for "=" sign 
motor.readlines()


```
This code above works exactly once...! If i try to change the DN or Micro Step (MS) value, I get an "?" in the output stream from readlines().

When I use the screen program, I can set and change the variables any number of times..

This is a new field for me and I'm lost at this point.
There are more PySerial com options that can be set but I don't know which could be the problem. I though the writeTimeout should be changed from the default of None
to 0, but that didn't help.

I also would like to compare how screen is connecting since that works flawlessly. I haven't been able to figure out a way to examine the connection protocols that
screen is using....

TIA,
wbg

---

### Post by wannabegeek on 2013-05-24
It would appear that the series of \r and \n is hard to keep track of and for a reason I'm not sure of, 
I needed to add another \r after certain commands.

It's as if the cursor is not at the prompt and this throws things off.

I'll try to doc this here better in a few days in case some other poor person needs it someday.

wbg

---

