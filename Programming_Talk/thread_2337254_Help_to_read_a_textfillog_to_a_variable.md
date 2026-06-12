---
title: "Help to read a textfil/log to a variable"
date: 2016-09-16
forum: Programming Talk
---

### Post by cazz on 2016-09-16
Hi
After looking around a little I did find it very cool tool for network name iperf3
It is that I was looking for and easy to use.


So when I run the command **iperf3 -c <ipnr> > send.log**
then I have info in my log but I just want to have  000 Mbits/sec (sender)

```
Connecting to host x.x.x.x, port 5201
[  4] local x.x.x.x port 55950 connected to x.x.x.x port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   106 MBytes   893 Mbits/sec    0    523 KBytes
[  4]   1.00-2.00   sec   107 MBytes   897 Mbits/sec    0    604 KBytes
[  4]   2.00-3.00   sec   109 MBytes   911 Mbits/sec    0    604 KBytes
[  4]   3.00-4.00   sec   106 MBytes   891 Mbits/sec    0    604 KBytes
[  4]   4.00-5.00   sec   107 MBytes   900 Mbits/sec    0    604 KBytes
[  4]   5.00-6.00   sec   107 MBytes   901 Mbits/sec    0    604 KBytes
[  4]   6.00-7.00   sec   107 MBytes   901 Mbits/sec    0    645 KBytes
[  4]   7.00-8.00   sec   108 MBytes   902 Mbits/sec    0    645 KBytes
[  4]   8.00-9.00   sec   108 MBytes   902 Mbits/sec    0    645 KBytes
[  4]   9.00-10.00  sec   106 MBytes   891 Mbits/sec    0    645 KBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.05 GBytes   899 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  1.04 GBytes   897 Mbits/sec                  receiver



```

I'm not so good in regex because I guess it that I need to have to get my info to a varable
So can someone help me?



/Update
After have done some try an error I have got this far

speed=$(grep '\<GBytes.*0\>' send.log)

So inside the varable speed I got now
```
[  4]   0.00-10.00  sec  1.05 GBytes   899 Mbits/sec    0             sender
```

Still to much but more less then before :)

---

### Post by steeldriver on 2016-09-16
From `man grep`

```

       -o, --only-matching
              Print  only  the  matched  (non-empty) parts of a matching line,
              with each such part on a separate output line.


```

---

### Post by cazz on 2016-09-16
wow thank, it was simple :)
Now I get
```
GBytes   899 Mbits/sec    0
```
and that is better then before
But now I trying to get the 899 that I going to put in a database

I did try with 
```
speed=$(grep -o 'GBytes   (.*)\ Mbits' send.log)
```

but then it show blank

---

### Post by steeldriver on 2016-09-16
To get only the digits after the GBytes match, it's easier to take a different approach - using grep's PCRE mode

```

grep -Po 'GBytes\s+\K\d+'

```

---

### Post by The Cog on 2016-09-16
Maybe cut out fixed position characters:
```
echo '[  4]   1.00-2.00   sec   107 MBytes   897 Mbits/sec    0    604 KBytes' | cut -c 38-52
```
Or grep for the number and size:
```
echo '[  4]   1.00-2.00   sec   107 MBytes   897 Mbits/sec    0    604 KBytes' | grep -Po '\d+\s+.bits/sec'
```

---

### Post by cazz on 2016-09-16
wow nice, have no idea what \s+\K\d+ mean but I know I have to read about it to understand what you have done :)

when it read the log it read the speed of download and upload and show it like this

```
899
897
```

Does it read as a string with n\ so I need to put it a array to divide the info I got from regex?

/Update

Have not got it to work

```
stringarray=($speed)

echo "Download:"
echo ${stringarray[0]}
echo "Upload:"
echo ${stringarray[1]}
```

---

