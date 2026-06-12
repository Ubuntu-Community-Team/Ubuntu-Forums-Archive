---
title: "Play audio file after receiving a signal from serial port?"
date: 2011-09-09
forum: Programming Talk
---

### Post by bmdsherman on 2011-09-09
I have very little programing experience with ubuntu but I am looking for a way to have an arduino ([www.arduino.cc](www.arduino.cc)) tell my Ubuntu laptop to play an audio file via the usb port.

How would I go about writing a program to play an audio file when a certain message is received from the serial port?

Thanks in advanced!

---

### Post by Senesence on 2011-09-09
I don't really have any experience with arduino, but I think it should show up as a device under /dev, which is essentially a file that you can read like any other.

So, a small program to actually do something based on data received from arduino could look like:

```

== PSEUDO CODE ==
file = open('/dev/devname')
data = file.readline()
if data:
 playAudio()

```

I'm not really sure though - you can do some testing on your own.

---

