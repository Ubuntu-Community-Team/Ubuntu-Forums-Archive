---
title: "Does not always log the information in the database"
date: 2016-09-22
forum: Programming Talk
---

### Post by cazz on 2016-09-22
With alot of help from here I have got my network script to work but something is wrong but I'm not sure what.

In crontab I have set so every 15 min it going to run the script and what I have see is that crontab is not the problem.

I have attache a image of how it look in the MySQL and you can see that something is wrong.
[ATTACH=CONFIG]271307[/ATTACH]

The code is very simple

```


#! /bin/bash

place="Kontoret"

iperf3 -c 192.168.0.138 >> speed.log

speed=$(grep -Po 'GBytes\s+\K\d+' speed.log)

stringarray=($speed)
clear
echo "Download:"
echo ${stringarray[0]}
echo "Upload:"
echo ${stringarray[1]}
rm speed.log

echo "$place"

upload=${stringarray[1]}
download=${stringarray[0]}

if [ -z $upload ]
 then
  $upload='000'
fi
if [ -z $download ]
 then
  $download='000'
fi

echo "insert into speed(upload, download, place) values ('$upload', '$download', '$place');" | mysql --user=X --password=X --host=X X

```

I use some echo to see how it looks if I want to run i manual.
I was thinking maybe the error is that it sometime not got some value from download and upload so I did create a if that if the value is nothing it write 000 and save it in MySQL
But as you can see in the pic that no 000 can be found so I'm not sure if my if works.

Maybe not so nice code that I have done :) but I have no idea what it does sometime save it in MySQL and sometime not.

---

### Post by spjackson on 2016-09-22
There could be many reasons why your insert might fail: maybe the host is not reachable, or maybe there's a single quote in one of your $upload, $download, $place variables. Where does the standard output and error of your cron job go? Does it get mailed to you or is it written to a file? Check that output.

You could also try examining the mysql log on the remote host and/or enable query logging if it is not already enabled.

---

### Post by cazz on 2016-09-22
hi, thanks for the replay
*Host is not reachable
I don't think that is any problem, is a local Network and it works very well but even if I have that problem, the if is going to set the variables to 000 (Or is my if something wrong?)

*Single quote
Well it works most of the time so that is strange if it does not works if I have done something wrong there.

*error in the cron job
if the crontab does not have any error log then I don't have any log at all to read.
so that is something I can do when I get back to work, add a log to the crontab like this

```
*/15 * * * * /home/pi/speed.sh > /home/pi/speed.log
```

---

### Post by spjackson on 2016-09-22
Is /home/pi/speed.log the same speed.log you are writing to near the top of the script? Also, you need to redirect the error stream too and maybe you want to append to a log file unless you can readily check it whenever a "miss" occurs.

---

### Post by cazz on 2016-09-22
sorry I have to change the error log to Another name like speederror.log

How do i redirect the error strem?

Right now I just read what I can do tomorrow when I get back to work to see what log error it show to my script.
It is so strange that sometime it works and sometime it does not work.
Sometime it can run every 15 min and sometime it take 30 or even 45 min Before it show any value in the MySQL database.

---

### Post by cazz on 2016-09-23
After have add and read the error log I have notice that value $upload/$download does not have any info sometime so it is maybe that why I have problem with add information to MySQL

is a little strange so somehow my script is not reliable as I hope
If I can't get the script to work then I can't use it because it give me wrong information.

I don't thin iperf3 is the problem (I hope not it is a very nice program and easy to use) so it have to be my script.

---

### Post by spjackson on 2016-09-23
> **cazz said:**
> sorry I have to change the error log to Another name like speederror.log

How do i redirect the error strem?


Here's how I might do it.
```

*/15 * * * * (date && /home/pi/speed.sh) >> /home/pi/speed-cron.log 2>&1

```

[LIST]
[*]'>>' rather than '>' so that the log file is appended to each time, not overwritten. 
[*]'2>&1' to send the error stream to the same place as the output stream. 
[*]'date' so that I can tell when any messages are from. 
[/LIST]

A bash or cron expert might suggest a different approach.> 
It is so strange that sometime it works and sometime it does not work.

Welcome to the world of debugging.

---

### Post by cazz on 2016-09-23
After have add and read the error log I have notice that value $upload/$download does not have any info sometime so it is maybe that why I have problem with add information to MySQL

is a little strange so somehow my script is not reliable as I hope
If I can't get the script to work then I can't use it because it give me wrong information.

I don't thin iperf3 is the problem (I hope not it is a very nice program and easy to use) so it have to be my script.



I going to change in crontab to se what more info I got

---

### Post by cazz on 2016-09-23
ok after I have look in the log Before I went home from work I found out it sometime does not give any  upload or download and that is strange because I know the network there I monitor right now is very good.

the error log
```

Download:

Upload:

Kontoret
/home/pi/speed.sh: line 24: =000: command not found
/home/pi/speed.sh: line 28: =000: command not found
mysql: [Warning] Using a password on the command line interface can be insecure.
ERROR 1366 (HY000) at line 1: Incorrect integer value: '' for column 'upload' at row 1
fre 23 sep 2016 12:15:01 CEST
TERM environment variable not set.
Download:

Upload:

Kontoret
/home/pi/speed.sh: line 24: =000: command not found
/home/pi/speed.sh: line 28: =000: command not found
mysql: [Warning] Using a password on the command line interface can be insecure.
ERROR 1366 (HY000) at line 1: Incorrect integer value: '' for column 'upload' at row 1
fre 23 sep 2016 12:30:01 CEST
TERM environment variable not set.

```

the "TERM environment variable not set." is something about MySQL but why does it not always give the value of download and upload.

---

### Post by spjackson on 2016-09-24
> **cazz said:**
> 
```

/home/pi/speed.sh: line 24: =000: command not found
/home/pi/speed.sh: line 28: =000: command not found

```

That's because you should be doing:
```

if [ -z $upload ]
 then
  upload='000'
fi

```
N.B. no $ in the assignment statement, similarly for download.

It seems to me that the underlying problem is that the ouput from iperf3 isn't always in the form such that
```

(grep -Po 'GBytes\s+\K\d+' speed.log)
```gives you the results you want. I think you need to look closely at the raw output from iperf3 in the failing cases.

---

### Post by cazz on 2016-09-24
ahh thanks

Hmm ok I have to save then info of speed.log so I can see what is the problem.
Thanks, going to do that on monday

---

### Post by cazz on 2016-09-27
Hello again.
Now I have some info that I think why I have problem with my script.

When it is ok the log show

```

[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.02 GBytes   878 Mbits/sec   64             sender
[  4]   0.00-10.00  sec  1.02 GBytes   876 Mbits/sec                  receiver

```

and when I have error it is this on the log

```

[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1012 MBytes   849 Mbits/sec   61             sender
[  4]   0.00-10.00  sec  1010 MBytes   847 Mbits/sec                  receiver

```

As you can see when the log have GBytes then it works but when it show MBytes then regex going crazy and I can understand that

iperf3 does not let med format the Transfers only Bandwith.

So I guess that I need to use some kind of if case that if it does not work with GBytes then run MBytes

Going to try this now

```

speed=$(grep -Po 'GBytes\s+\K\d+' speed.log)

if [ -z $speed ]
 then
  speed=$(grep -Po 'MBytes\s+\K\d+' speed.log)
fi

```

---

### Post by cazz on 2016-09-28
It is almost done.
It did look greate but now I have a problem that I have no idea how to fix that

I have done if it show in GBytes then it going to do one regex and if it show in MBytes then it run another regex

But I have not think about what if it run like this

```
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.00 GBytes   861 Mbits/sec   89             sender
[  4]   0.00-10.00  sec  1024 MBytes   859 Mbits/sec                  receiver

```

one of each??

It can be GBytes and MBytes or MBytes and GBytes


I guess that I can use a IF that too if upload or download if null run the other but I have no idea how to make it work as good as possible.

---

### Post by cazz on 2016-09-29
A little update here
I think I have got it to work but I going to let it work a little to see everything works like I want it too.

---

### Post by cazz on 2016-10-05
ok after have run it a little now it looks like it works greate

That I did do was I use AWK to go to line 16 and 17 extract that line to a variable and then run regex for GBytes and if the variable have some information than it is fine.
If not it run another regex MBytes and save that in a variable.

Did do that one for upload and one for download.

A little more code but it works :D

---

