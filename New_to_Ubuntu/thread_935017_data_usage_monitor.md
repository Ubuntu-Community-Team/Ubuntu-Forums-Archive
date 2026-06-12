---
title: "data usage monitor"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by hellomoto on 2008-10-01
Ok I am looking for a simple program, ideally console based that will allow me to monitor my total internet usage untill I reset it. 

Basically I have a mobile broadband connection and I would like to monitor my total usage over the month. I am allowed 1gb of data usage, hence why I want to monitor as its not a vast amount and I don't want to get charged.

Does anyone know of such a program?

Thank you in advance!

---

### Post by renzokuken on 2008-10-01
i don't know if **ntop** provides that functionality. a quick google search found **Blinky** too, but again not sure if it does exactly what you need

---

### Post by m_duck on 2008-10-01
I think vnstat is a good program. It must be run as root the first time to create the database for it but can be run as a user after that.

Install:```
sudo apt-get install vnstat
```

Create DB:```
sudo vnstat -u -i <interface>
```
(ie sudo vnstat -u -i eth0)

Then have a look at vnstats man page for displaying what you require. IE to display the traffic in the past month on interface eth0, you would type:
```
vnstat -m
```

---

### Post by hellomoto on 2008-10-01
vnstat seams to be working great. I have a q though. How long does it define a month? 30 or 31 days?

---

### Post by hellomoto on 2008-10-01
I seam to be having trouble to get it to monitor my ppp0 connection:

```


mark@ubuntu:~$ sudo vnstat -u -i ppp0
[sudo] password for mark: 
mark@ubuntu:~$ vnstat -l
Monitoring eth0...    (press CTRL-C to stop)

   getting traffic...Error:
Unable to get interface statistics.


```

---

### Post by aeiah on 2008-10-01
> **hellomoto said:**
> vnstat seams to be working great. I have a q though. How long does it define a month? 30 or 31 days?

it does calendar months
```

$ vnstat -m

        eth1

           month        rx      |       tx      |    total
        ------------------------+---------------+---------------
          Mar '08     60290 MB  |     38595 MB  |     98886 MB
          Apr '08    229145 MB  |    165124 MB  |    394269 MB
          May '08    111282 MB  |    105101 MB  |    216383 MB
          Jun '08    129706 MB  |    106022 MB  |    235729 MB
          Jul '08     97841 MB  |    127276 MB  |    225118 MB
          Aug '08    121011 MB  |    131409 MB  |    252420 MB
          Sep '08    139039 MB  |    149724 MB  |    288763 MB
          Oct '08      8636 MB  |      7236 MB  |     15872 MB
        ------------------------+---------------+---------------
        estimated    494244 MB  |    414121 MB  |    908365 MB

```

and for weeks, it does this calendar week, last calendar week, and last 7 days

---

### Post by m_duck on 2008-10-01
Does it run if you type:```
vnstat -l -i eth0
```I would have thought that if you modem is plugged into your ethernet port, you can just monitor that rather than setting up the pp0 thing. I may be wrong as I've not used that myself.

---

### Post by aflatun on 2008-12-15
I am having issues monitoring my wirless network using vnStat. I type in:

name@name-laptop:~$ sudo vnstat -u -i networkname
Error:
Unable to read database "/var/lib/vnstat/networkname".
Error:
Unable to get interface statistics.
 
Any help would be appreciated.

---

### Post by shof2k on 2009-03-04
> **hellomoto said:**
> I seam to be having trouble to get it to monitor my ppp0 connection:

```


mark@ubuntu:~$ sudo vnstat -u -i ppp0
[sudo] password for mark: 
mark@ubuntu:~$ vnstat -l
Monitoring eth0...    (press CTRL-C to stop)

   getting traffic...Error:
Unable to get interface statistics.


```

You need to set up the initial database. To do this, type the following into a terminal

```

sudo chmod o+x /usr/bin/vnstat && sudo chmod o+wx /var/lib/vnstat/

```

Peace

---

