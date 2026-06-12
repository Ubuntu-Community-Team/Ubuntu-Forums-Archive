---
title: "Reading temperature to a php page"
date: 2009-01-01
forum: Programming Talk
---

### Post by Bootes87 on 2009-01-01
I have a temperature sensor connected to the serial port of my server. I use a command line program (digitemp_DS9097) to query the sensor and get the current temperature and it works great. Now I would like to post the temperature to a web page hosted on the server. Each time the page is loaded my a php script calls digitemp_DS9097 and print the results to the web page. At least that's how I would like it to happen.

**index.php**
[PHP]<?
$temp = `digitemp_DS9097 -a -o %F`;
print($temp);
?>[/PHP]

**running digitemp_DS9097 in console:**
```

jeffrey@Tabitha:/var/www$ digitemp_DS9097 -a -o %F
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
68.000000
jeffrey@Tabitha:/var/www$

```

**The web page displays:**
```
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane GNU Public License v2.0 - http://www.digitemp.com
```

**the web page (view source):**
```
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com

```

You can see that it excludes the last and IMPORTANT part of the output ... the temperature!

**digitemp has a -v parameter that displays alot more information about the sensor:**
```

jeffrey@Tabitha:/var/www$ digitemp_DS9097 -a -v -o %F
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
67.887500
  Temperature   : 0x28
  Sign          : 0x00
  TH            : 0x4B
  TL            : 0x46
  Remain        : 0x0D
  Count Per C   : 0x10
  CRC           : 0x57
scratchpad[0] = 0xBE
scratchpad[1] = 0x28
scratchpad[2] = 0x00
scratchpad[3] = 0x4B
scratchpad[4] = 0x46
scratchpad[5] = 0xFF
scratchpad[6] = 0xFF
scratchpad[7] = 0x0D
scratchpad[8] = 0x10
scratchpad[9] = 0x57
jeffrey@Tabitha:/var/www$

```

however the resulting web page and source does not change. It gets cut off after "Public License v2.0 - http://www.digitemp.com"

One thing I've noticed is that when running digitemp from the console it immediately prints 

```
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com

```

then there is a 750ms -1000ms delay before the temperature is printed. This is due to the time it takes to query the sensor. Is it possible that php is not patient enough to wait for the rest of the string and just carries on with out it? If so is there a way to put the breaks on and make it wait for the rest of the output?

I also wonder if after printing "Public License v2.0 - http://www.digitemp.com" there is some kind of character (like a carriage return) that is falsely telling php, it has reached the end?

Please let me know what you think about this!
Thank You,
Bootes

---

### Post by kidders on 2009-01-02
Hi there,

It's possible that your sensor utility needs something the www-data user doesn't have access to. Assuming "-a" means "all", it seems reasonable to report no sensor data, if no accessible sensors are found. Try running your utility as www-data ... that should give you a more realistic reproduction of what happens when PHP tries to do it in a web page.

---

### Post by Bootes87 on 2009-01-02
Kidders, your my hero!

I did not realize the web server acted as a "user". Running my utility as:```
sudo su www-data digitemp_DS9097 -a
``` reveled that www-data did not have +rw permission to asses ttyS0 (the serial port the sensor is connected to). So I ran: ```
sudo chmod 777 /dev/ttyS0
```...and everything works PERFECTLY!

THANK YOU!

---

### Post by kidders on 2009-01-02
Hey again,

Glad I could help. All web servers work that way ... mostly so that stuff like PHP scripts can't be manipulated into doing anything that might damage your system. The user they run as tends to be too unprivileged to do much of consequence.

Incidentally, running "chmod 777" on things is bad practice, and in any case, the change to /dev/ttyS0 will probably be lost the next time your reboot. For a more permanent solution, I suggest either adding www-data to a group that would allow it access to the serial port, or altering your udev rules to change the group that owns /dev/ttyS0 ... whichever seems more secure. That way, your PHP script will still work after a reboot.

---

### Post by Bootes87 on 2009-01-02
That is something I will have to look into. I'm aware that 'chmod 777' is not a good idea, I was just looking for a "quick fix" after I found out it was a permission issue, and I thought sense  it was only the serial port, it couldn't hurt much. I've been pulling my hair out for days trying to understand how I could be getting the output form the utility *except* the part I was looking for.

For now I'm just playing around with this stuff to see what I can do. The server is an old PC and its not even live to the internet. 

Should I go any further with this, and make it live, I'm sure there will be a number of security issues I will need to address. I was just excited to finally see it work! 

Thank you again, you've been a HUGE help!

---

### Post by kidders on 2009-01-02
No problem :-)

---

