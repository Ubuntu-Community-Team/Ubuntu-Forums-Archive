---
title: "quick python script error"
date: 2013-07-14
forum: Programming Talk
---

### Post by wingnut2626 on 2013-07-14
I wrote a quick script in python to write the METAR report for my area to a file....for debug purposes I have the file executing every 5 seconds.  Here is the code:import timeimport osfileIn=open('/home/wingnut2626/weather.txt',  'a')b = '-' * 30def timeAppendWeather():    a = time.time() + 5    while time.time() != a:        continue    else:        fileIn.write(time.ctime())        fileIn.write(b)        os.popen2('metar -d KILG > /home/wingnut2626/weather.txt')        fileIn.write(b)        fileIn.write('\n')        timeAppendWeather()               if __name__ == '__main__':    timeAppendWeather()            Here is the error that is generated:p11-kit: invalid config filename, will be ignored in the future: /etc/pkcs11/modules/gnome-keyring-moduleWARNING: gnome-keyring:: couldn't connect to: /home/wingnut2626/.cache/keyring-sKSRG2/pkcs11: No such file or directoryp11-kit: failed to initialize module: gnome-keyring-module: An error occurred on the deviceAny ideas?

---

### Post by sanderj on 2013-07-14
I cannot read this. So I can't help you.

---

### Post by ofnuts on 2013-07-14
Hardly readable. 

Which instruction makes the message appear?

---

### Post by MG&amp;TL on 2013-07-14
I apparently have nothing I'd rather do on a Sunday evening.

> I wrote a quick script in python to write the METAR report for my area  to a file. For debug purposes I have the file executing every 5  seconds.  Here is the code:

```

import time
import  os

fileIn=open('/home/wingnut2626/weather.txt',  'a')
b = '-' * 30

def  timeAppendWeather():
    a = time.time() + 5
    while time.time() != a:
        continue
    else:
        fileIn.write(time.ctime())
        fileIn.write(b)
        os.popen2('metar -d KILG >  /home/wingnut2626/weather.txt')
        fileIn.write(b)
        fileIn.write('\n')
        timeAppendWeather()

if __name__  == '__main__':
    timeAppendWeather()

```

Here is the error that  is generated:

```
P11-kit:  invalid config filename, will be ignored in the future:  /etc/pkcs11/modules/gnome-keyring-module
WARNING: gnome-keyring::  couldn't connect to: /home/wingnut2626/.cache/keyring-sKSRG2/pkcs11: No  such file or directory
p11-kit: failed to initialize module:  gnome-keyring-module: An error occurred on the device

```
Any ideas?

I guessed at the python indentation, sorry. It appears to be legal python anyhow.

---

### Post by wingnut2626 on 2013-07-14
I figured it out.  I just needed to update my debian

---

