---
title: "simple Arduino IDE launcher in menu"
date: 2008-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Keen101 on 2008-10-15
I found out how to create a simple launcher in your menu to start the Arduino IDE without having to browse to the folder every time.

One way to this is to use this launcher command:

```
**bash -c "cd /home/andrew/arduino-0012/; ./arduino"**
```

and the other way was to create a script with the following code, rename it to "arduino", and copy it to /usr/local/bin

```
[B]#!/bin/sh

cd /home/andrew/arduino-0012
./arduino[/B]

```

I also found this launcher icon [http://osx.iusethis.com/icon/osx/arduino.png]("http://osx.iusethis.com/icon/osx/arduino.png")

and i copied it to /usr/share/icons and i also made a copy to /usr/local/share. Now when i go to create a launcher and type the command "arduino" it automatically finds this icon, i then just change the command to work.

---

### Post by rexmo on 2008-12-28
Hey thanks for this.  I found it very useful!

---

### Post by ArduinoFun on 2009-05-05
Thanks for posting this. Great tip! I had been trying to get the launcher to do this before. I am new to Ubuntu so I didn't have the command written in properly for the launcher, this helped a lot!

Shawn Augustson
[http://www.ArduinoFun.com]("http://www.arduinofun.com")

---

### Post by Linux_rookie on 2009-11-27
I set this up and it worked just like you said, but when I click on the icon the screen "blips" and nothing happens. Am I missing a permission thing or something?

---

### Post by flitzjoy on 2010-10-16
It just works for Arduino 0.21 and Ubuntu 10.10.

I downloaded the tar.gz from Arduino.cc and
as i already had java installed it was just necessary to install gcc-avr and avr-libc.

---

