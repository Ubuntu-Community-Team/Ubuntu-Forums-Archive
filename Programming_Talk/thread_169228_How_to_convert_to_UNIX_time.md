---
title: "How to convert to UNIX time?"
date: 2006-05-02
forum: Programming Talk
---

### Post by bhubanmm on 2006-05-02
I am new to Linux. I am trying to learn about timers.

Can someone guide me on how to convert a user given time like (Tue May 2, 5:02 PM 2006) to UNIX time (long, ex : 1146524531).

Please help.

---

### Post by thumper on 2006-05-02
It depends on the language...

In C look for strptime and mktime.  strptime parses a string and creates a tm struct.  mktime converts a tm struct into a time_t (which is normally a long).

---

### Post by nocturn on 2006-05-02
[QUOTE=bhubanmm]I am new to Linux. I am trying to learn about timers.

Can someone guide me on how to convert a user given time like (Tue May 2, 5:02 PM 2006) to UNIX time (long, ex : 1146524531).

Please help.[/QUOTE]

Or run a shell command:

```

date -d "datetouse" +%s

```

---

### Post by bhubanmm on 2006-05-02
Thanks for the answers. I hope I can proceed from here.

---

### Post by thumper on 2006-05-02
If you told us what language you were looking to implement your solution in we could provide more useful help.

It is done quite differentlyin C, C++, perl, or python.

---

### Post by tevildo on 2009-08-07
I've got a similar, related problem - I need to convert a human readable time into unix time (or something similar, anyway - you'll see in a bit).

The problem here is that I need this in a datalogger program, and the designers of the datalogger decided not to include a function to get the time in seconds since an epoch, nor did they provide a function to convert a time in human readable format into seconds-since-epoch. All I have is a function to get the current datetime as an array of floats for year,month etc.

This would be ok, all I need is a way to store the time of each log entry, but I need to also communicate this time to a telemetry device through a restricted version of modbus with only 36 floating point variables available for transmission, and I don't have 6 spare to send the datetime as is.

Since all I need is to compress the datetime into a single floating point number, I don't need to specifically use the Unix epoch.

The best I've managed to come up with so far is to multiply the number of years since the epoch by 31,536,000, add the appropriate multiple of 86,400 for the amount of days in each month so far, and so on down.

The problem I'm hitting is handling leap years - my best idea so far is to iterate over each year that has passed and test if it was a leap year, but I'm wondering if there's a better way to count the number of leap years between two dates? Or maybe a better way of approaching the problem overall?

---

### Post by tevildo on 2009-08-07
Well, I've had a look at the php source code (after haranguing the IT guys to let me download it :P) for their implementation of this, and they just iterate over the years and add the appropriate amount of days after testing for leap status, so I'm not going to hold my breath for a better way :(

---

### Post by smartbei on 2009-08-07
Does it need to be a real float? How about using the float's data (if it is a double - 64 bits) and encoding the date into that bitwise? Year is 12 bits, month is 4, day is 5, hour is 5, minute is 6, seconds is 6. All together - 38 bits, which can be naively packed into 64 bits.

If, on the other hand, you only have 32 bits to transfer, then how about copying the implementation of one of the time functions from some open-source project (glibc fo instance) which implements them?

---

### Post by tevildo on 2009-08-07
Oooh, I didn't think of that... Unfortunately, I'm pretty sure the telemetry doesn't support 64 bit floats, only 32 bit, so I'll have to use your second suggestion. I'll use the PHP one, as I already have the source (not quite sure _why_ I looked at PHP instead of glibc, though...). Fortunately, I have some ability to manipulate individual bits in variables, otherwise this could be awkward too :P

---

### Post by smartbei on 2009-08-07
I thought about it a bit more - and figured you don't really need to use 12 bits for the year - you would do fine with 6 bits. Then it fits with 32 bit floats.

All you would need to do is decide that you support years in the range [x, x+64), so your base year would be, for example, 2000.

Here is code that would do this:
```

typedef unsigned char uchar;

int packed_time(int year, uchar month, uchar day, uchar hours, uchar minutes, uchar seconds)
{
	year = year - 2000;
	return (year << 25) | (month << 21) | (day << 16) | (hours << 12) | (minutes << 6) | seconds;
}
// Note - I didn't test it, but this is the idea.

```
Unpacking is the same, and just as trivial. I assumed 32 bit ints. All you would need to do is cast to a float.

---

### Post by tevildo on 2009-08-07
That's really quite nice :) A lot fewer lines of code than the php implementation, meaning I can probably get away with running it every time it stores a record instead of once at the start of the program and then adding the offset - program runs scan cycles every 15 minutes, and needs to timestamp the start of the cycle. With unix time format, I was just adding 15*60 to the 'current' time every cycle. This would have caused problems if I ever changed the scan interval and forgot to change both (can't use a variable or const to set scan interval... who designs these crazy programming languages? :P).

Thank you very much for your help, I'm pretty sure we'll go with your implementation.

---

