---
title: "Python2.6 pyserial Not working (import issue??)"
date: 2011-03-23
forum: Programming Talk
---

### Post by tippyTdizzle on 2011-03-23
I hope this is the right spot for this post! Please forgive if it is not, and advise otherwise. Need some help with what I think is a python import error. I have python-2.6 with the python-serial 2.3.1 module installed (default for ubuntu/debian).

The main problem is that I am trying to run the following code to read serial data from USB (using a FTDI chip, ft232rl, in an embedded app) so that I can read-in the data and dynamically plot it (from what I gather, python is the best approach for this, rather than a custom C program and shell script integration GNUplot, and I would do it in Octave, except that there currently is no serial port support there. If anyone has a different opinion on this, I would love to hear suggestions). Here is my code:

```

#!/usr/bin/python2.6

import serial

# grab serial port data from FTDI chip
ser = serial.Serial(port='/dev/ttyUSB0', baudrate=250000, rtscts=True)
ser = ser.open()
c = ser.read(1)
print c

ser.close()        # close port

```

The error I receive from running this is (paraphrased) the "ATTRIBUTE-ERROR: NoneType has no Attribute .read()" ... Now, from what I can gather, this could be due to an import error (i.e. the command "import serial" not functioning properly). Because if I add the line

```

ser = ser.isOpen()

```

on the line after ser=ser.open(), then the same error occurs, this time citing "...Attribute .isOpen()", which is what leads me to believe this is something like an import/module issue (i.e. the correct class functions cannot be found). 

However, being new to python, maybe it is something else. The code I have included (above) is taken mostly from examples around the web, and most of them straightforward (so, in other words, I think the core issue is possibly beyond just the code).

...

Thanks in advance!

Other Info:
Release: Ubuntu 10.04 LTS
uname -r: 2.6.32-29-generic-pae

---

### Post by robots.jpg on 2011-03-23
I'm not familiar with the serial module, but I would look at the line ser=ser.open().  You're overwriting the object you created in the previous line with the result of the open function, which apparently returns no value.

What happens if you change it to just "ser.open()"?

---

### Post by tippyTdizzle on 2011-03-23
Thanks robots.jpg! You helped me get the details shaken out :-)

Here's the code that worked:

```


#!/usr/bin/python2.6

import serial

# grab serial port data from FTDI chip
ser = serial.Serial(port='/dev/ttyUSB0', baudrate=250000, rtscts=True)
ser.open()
c=ser.read(5)
print c

ser.close()        # close port


```

And it prints to the terminal :D Very cool

Now to work with some 'print' parameters and hopefully move on to some graphing!

---

