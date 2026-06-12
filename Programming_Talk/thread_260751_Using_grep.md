---
title: "Using grep?"
date: 2006-09-19
forum: Programming Talk
---

### Post by meniscus on 2006-09-19
This is probably v simple i realise but im a newbie to programming](*,) 

The following information is being logged periodically to the file  /var/log/syslog

I want to log only the [COLOR="Red"]M/B temp[/COLOR] information to another file as it is written to var/log/syslog


I know i start with the command  [COLOR="Blue"]tail -f /var/log/syslog   \[/COLOR]( At least i hope it is!) followed by [COLOR="Blue"]grep[/COLOR] something? 

I want the reading written to the desktop. Anyone have any clues? 


> Sep 19 14:42:25 localhost sensord: Chip: it8712-isa-0290
Sep 19 14:42:25 localhost sensord: Adapter: ISA adapter
Sep 19 14:42:25 localhost sensord: Algorithm: ISA algorithm
Sep 19 14:42:25 localhost sensord:   VCore 1: +1.30 V (min = +1.42 V, max = +1.57 V) [ALARM]
Sep 19 14:42:25 localhost sensord:   VCore 2: +1.49 V (min = +2.40 V, max = +2.61 V) [ALARM]
Sep 19 14:42:25 localhost sensord:   +3.3V: +6.46 V (min = +3.14 V, max = +3.46 V) [ALARM]
Sep 19 14:42:25 localhost sensord:   +5V: +4.92 V (min = +4.76 V, max = +5.24 V)
Sep 19 14:42:25 localhost sensord:   +12V: +12.03 V (min = +11.39 V, max = +12.61 V)
Sep 19 14:42:25 localhost sensord:   -12V: -19.87 V (min = -12.63 V, max = -11.41 V) [ALARM]
Sep 19 14:42:25 localhost sensord:   -5V: -2.56 V (min = -5.26 V, max = -4.77 V) [ALARM]
Sep 19 14:42:25 localhost sensord:   Stdby: +5.00 V (min = +4.76 V, max = +5.24 V)
Sep 19 14:42:25 localhost sensord:   fan1: 3013 RPM (min = 0 RPM, div = 16)
Sep 19 14:42:25 localhost sensord:   fan2: 0 RPM (min = 332 RPM, div = 16)
Sep 19 14:42:25 localhost sensord:   fan3: 3375 RPM (min = 664 RPM, div = 8)
Sep 19 14:42:25 localhost sensord:   [COLOR="Red"]M/B Temp: 43 C[/COLOR] (min = 15 C, max = 40 C)
Sep 19 14:42:25 localhost sensord:   CPU Temp: 49 C (min = 15 C, max = 45 C)
Sep 19 14:42:25 localhost sensord:   Temp3: 44 C (min = 15 C, max = 45 C)


Thanks in advance
meniscus

---

### Post by bswilson on 2006-09-19
This will do exactly what you've asked for, but it is neither the most efficient way, nor is it a streamlined way.  You'd have to manually run this script when you are ready to get information; it won't happen automatically...

```
#!/bin/sh$
# mbtemp.sh will send data from syslog to a file on the current user's desktop
#
/usr/bin/sudo /usr/bin/tail -f /var/log/syslog | grep "M/B temp" > ~/Desktop/motherboardtemp.log &2>1
```

---

### Post by meniscus on 2006-09-19
> [COLOR="Red"]/usr/bin/sudo /usr/bin/tail[/COLOR] -f /var/log/syslog | grep "M/B temp" > ~/Desktop/motherboardtemp.log [COLOR="Red"]&2>1[/COLOR]


What does the code ive highlighted in red do? 

This line created a file called motherboardtemp.log alright but theres nothing in it! 

Heres the output i got.....

> meniscus@menisscot:~$ tail -f /var/log/syslog | grep "M/B temp" > ~/Desktop/motherboardtemp.log &2>1 [1] 9836
meniscus@menisscot:~$
meniscus@menisscot:~$ tail -f /var/log/syslog | grep "M/B temp" > ~/Desktop/motherboardtemp.log &2>1
[2] 9843

---

### Post by meniscus on 2006-09-19
More output... 

> meniscus@menisscot:~$ tail -f /var/log/syslog | grep "M/B temp" > ~/Desktop/motherboardtemp.log &2>1 [1] 9836
meniscus@menisscot:~$
meniscus@menisscot:~$ tail -f /var/log/syslog | grep "M/B temp" > ~/Desktop/motherboardtemp.log &2>1
[2] 9843
meniscus@menisscot:~$ tail -f /var/log/syslog | grep "M/B temp" > ~/Desktop/motherboardtemp.log &2>1
[3] 9970
meniscus@menisscot:~$ tail -f /var/log/syslog | grep "M/B temp" > ~/Desktop/motherboardtemp.log &2>1
[4] 9972
meniscus@menisscot:~$ tail -f /var/log/syslog | grep "M/B temp" > ~/Desktop/motherboardtemp.log &2>1
[5] 9974
meniscus@menisscot:~$


---

### Post by cwaldbieser on 2006-09-19
> **meniscus said:**
> What does the code ive highlighted in red do? 

This line created a file called motherboardtemp.log alright but theres nothing in it! 

Heres the output i got.....

"/usr/bin/sudo" gives the command permission to read syslog.
"/usr/bin/tail" prints the last 10 lines of the log file.

---

### Post by meniscus on 2006-09-20
What about this

> &2>1  

at the end of the command?

---

### Post by po0f on 2006-09-20
That redirects stderr to stdout, so it will print any errors you get on the console, instead of (possibly) just being logged.

---

