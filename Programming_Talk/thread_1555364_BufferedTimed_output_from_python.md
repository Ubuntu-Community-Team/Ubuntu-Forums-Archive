---
title: "Buffered/Timed output from python?"
date: 2010-08-17
forum: Programming Talk
---

### Post by p0nman on 2010-08-17
I'm writing a python script to take an Android event capture file as input and then replay those events into a USB/serial console port.  I have a working version of the script as I've described (attached: sender.py), but I would like to add the capability to playback the events in the same time reference as they were recorded(getevent -t).  Currently they just go in as fast as the script can execute. 

In my dev version of the script I have split() the two time components into variables int(sec) and float(microsec), but I do not know how to time output to my ttyUSB0 device.

Can someone point me in the right direction?  I'm a novice coder so go easy on me ](*,)

EDIT: the usage() is a little misleading about the optional time component, it's not in the attached version on the script

---

### Post by thaelim on 2010-08-18
Why not just use time.sleep(n) between each event?

---

### Post by p0nman on 2010-08-18
> **thaelim said:**
> Why not just use time.sleep(n) between each event?

I was thinking about this but there are a few problems that I foresee:

1) the input for time.sleep() is seconds but I want as fine a granularity as possible.  Remember I captured these events occurring down to the microsecond (1/1000000 of a second).  I know that I will not be able to replay them out with such fine granularity as THAT, but what is possible?  Accuracy down to the millisecond (1/1000) would be great.  Maybe I could just pass time.sleep(0.001) for a millisecond sleep, but that brings me to problem #2

2) in the definition (below) they explain that time.sleep() might sleep for shorter or longer than requested. This granularity might be fine if you are sleeping in seconds, but I'm not sure it will be very accurate for milliseconds.  I'll give time.sleep() a shot, but I think that there might be a "right way" to do what I am attempting to; schedule output.

a getevent script of continuous touches for only 2 or 3 seconds could be 300 lines (events)

time.sleep(secs)
    Suspend execution for the given number of seconds. The argument may be a floating point number to indicate a more precise sleep time. The actual suspension time may be less than that requested because any caught signal will terminate the sleep() following execution of that signal’s catching routine. Also, the suspension time may be longer than requested by an arbitrary amount because of the scheduling of other activity in the system.

---

### Post by p0nman on 2010-08-24
Seems that time.sleep() is as accurate as I'll get.  Seems to work pretty good actually.

---

