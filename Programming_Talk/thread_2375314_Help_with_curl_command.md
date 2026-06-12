---
title: "Help with curl command"
date: 2017-10-23
forum: Programming Talk
---

### Post by dam034 on 2017-10-23
Dear users,

I'm writing a plain-text file on ubuntu which contains some batch commands to execute.

One of these is this:
```
curl -v -u user:pass -A "my vps agent" -H "X-Why: to clean the thumbnails" http://my.website.com/clean
```

Now, I want to execute a command not only to call the webpage, but to log it in a plain-text file these informations:
[LIST]
[*]date/time in my local format of the execution
[*]the curl status (success/failed/timed out)
[*]the execution time
[*]the http code received from the server
[/LIST]

Obviously I need to specify in which file I want to log it, in append mode. And I need to set to infinite the timeout, because the call could last several minutes.

How can I do?


Please help!

---

### Post by norobro on 2017-10-23
You can get the http response code and several different times from curl using the "-w" option. [https://curl.haxx.se/docs/manpage.html#-w](https://curl.haxx.se/docs/manpage.html#-w)


Store the result in a variable, get the date and curl's return status from the shell and then output everything to your log file.


Give it a shot. If you have problems or questions post back.

---

### Post by dam034 on 2017-10-24
Yes, I can prepare a string that will be the format to save in the log file.

After, I need to output in the string the datetime.

But how can I append the format string in the log file?


Thanks

---

### Post by norobro on 2017-10-24
> **dam034 said:**
> But how can I append the format string in the log file?
use[COLOR=#000000] >>[/COLOR] 
[https://www.gnu.org/software/bash/manual/bash.html#Appending-Redirected-Output](https://www.gnu.org/software/bash/manual/bash.html#Appending-Redirected-Output)

---

### Post by dam034 on 2017-10-24
Can you give me an example?


Please!

---

### Post by norobro on 2017-10-24
```
[FONT=monospace][COLOR=#000000]$ cat curl.sh 
 [/COLOR]
#!/bin/bash

var=$(curl -o /dev/null -w 'http_response=%{http_code}  time_total=%{time_total}' -s www.google.com)
res=$?
printf "$(date +"%Y/%m/%d %H:%M:%S") $var "status_code=$res"\n" >> logfile
[/FONT]
```

```
[FONT=monospace][COLOR=#000000]$ cat logfile
[/COLOR]
2017/10/24 15:51:20 http_response=200  time_total=0.146500 status_code=0
[/FONT]
```

---

### Post by dam034 on 2017-10-24
Thanks for the help, now it works! :popcorn:

---

### Post by dam034 on 2017-11-13
Now I'm creating a new curl call, this is the code:

```
#!/bin/bash

call=$(curl -q -s \
-u myusers:mypw \
-A "My curl script" \
-H "X-From: VPS server" \
-m 900 \
-N \
--no-keepalive \
-w "HTTP: %{http_code}\tTime: %{time_total}" \
https://mywebsite.com/cron.php?what=1)
res=$?
printf "$(date +'%d-%m-%Y %H:%M:%S')\t$call\tCurl: $res\n" >> "cron-1.log"

```

But I don't want to save in the output file the http body response, but a particular response header (X-Done).

How can I do?

Thanks

---

### Post by norobro on 2017-11-13
I think that you will need to do some additional processing in your script with awk or sed. 

I'm not familiar with the header X-Done but possibly you can modify the following script to suit your needs:```
#!/bin/bash

var=$(curl -I -w 'HTTP: %{http_code}\tTime: %{time_total}' -s www.google.com)
res=$?
parsed=$(echo "$var" | awk '/HTTP:|X-Frame/ {gsub(/\r/,""); printf "%s"" ",$0}')
printf "$(date +"%Y/%m/%d %H:%M:%S")\t$parsed\tCurl: $res\n"
```Note that the gsub removes the carriage returns from the servers response.

Output:```
[FONT=monospace][SIZE=2][COLOR=#000000]2017/11/13 13:30:40     X-Frame-Options: SAMEORIGIN HTTP: 200   Time: 0.190164  Curl: 0[/COLOR][/SIZE]
[/FONT]
```

---

### Post by dam034 on 2017-11-15
With your batch command I solved the response body problem, now in the output there isn't the response body.

But I can't see my personal response header, which isn't "X-Done" as I wrote above, but "Runde".

And if you can explain or link docs about "awk".

How can I fix this issue?

Thanks

---

### Post by norobro on 2017-11-15
> **dam034 said:**
> But I can't see my personal response header, which isn't "X-Done" as I wrote above, but "Runde".
Please post the output of:```
curl -I [SIZE=2][COLOR=#000000][FONT=&amp]https://mywebsite.com/cron.php?what=1[/FONT][/COLOR][/SIZE]
```

> **dam034 said:**
> And if you can explain or link docs about "awk".The GNU docs are here: [https://www.gnu.org/software/gawk/manual/gawk.html](https://www.gnu.org/software/gawk/manual/gawk.html)

This is pretty basic awk  that is explained in the docs but here is a brief description:```
[SIZE=2][FONT=monospace][COLOR=#000000]$ curl -I -s localhost | awk '/Date:|Server:/'   [/COLOR][COLOR=#0000ff]# Regex checks each line for "Date:" or "Server: and prints the line if found[/COLOR]
Date: Wed, 15 Nov 2017 19:21:36 GMT
Server: Apache/2.4.29 (Debian)

[/FONT][FONT=monospace][COLOR=#000000]$ curl -I -s localhost | awk '/Date:|Server:/  {printf "%s"" ",$0}' [/COLOR][COLOR=#0000ff]# $0 is the whole line sans the LF so both[/COLOR][COLOR=#000000] lines 
[/COLOR][/FONT][COLOR=#000000][FONT=monospace]Server: Apache/2.4.29 (Debian) GMT                                  [/FONT][/COLOR][FONT=monospace][COLOR=#0000ff]# are output on one line with a space between[/COLOR][COLOR=#000000]
[/COLOR][/FONT][FONT=monospace][COLOR=#0000ff]                                                                    # But the server also returns a CR so the first line is overwritten.
[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]$ curl -I -s 192.168.2.3 | awk '/Date:|Server:/  {gsub(/\r/,""); print[/COLOR]f "%s"" ",$0}' [COLOR=#0000ff]# gsub(/\r/,"") replaces the CR with nothing[/COLOR]
Date: Wed, 15 Nov 2017 19:47:43 GMT Server: Apache/2.4.29 (Debian)[/FONT][/SIZE]
```

---

### Post by dam034 on 2017-11-16
> **norobro said:**
> Please post the output of:```
curl -I https://mywebsite.com/cron.php?what=1
```
This is the console:
```
root@srvesp:~# curl -I https://mywebsite.com/cron.php?what=1
HTTP /1.1 200 OK
Date: Wed, 15 Nov 2017 20:55:20 GMT
Server: Apache/2.4.2
X-Powered-By: PHP/5.4.4
Runde: nacht
Content-Type: text/html
```

Now in the output I want a row like this:
```
2017/11/15 22:00:36        Runde: nacht        HTTP: 200       Time: 0.190164        Curl: 0
```

Obviously the "Runde" is a custom response header, though it isn't out of standard. I need it to understand the result of the serverside script (cron.php) because the Runde header can return many values (nacht, p1, p2, err, comp, ecc...).

How can I do?

Thanks

---

### Post by norobro on 2017-11-16
Does changing the awk regex to "/Runde:/HTTP:/" not work?```
[SIZE=2]#!/bin/bash

var=$(curl -I -w 'HTTP: %{http_code}    Time: %{time_total}' -s https://mywebsitte.com/cron.php?what=1)
res=$?
parsed=$(echo "$var" | awk '/Runde:|HTTP:/ {gsub(/\r/,""); printf "%s   ",$0}')
printf "$(date +"%Y/%m/%d %H:%M:%S")    $parsed Curl: $res\n" >> logfile[/SIZE]
```

---

### Post by dam034 on 2017-11-16
I edited the batch command, and I added a "Z" character to see what happens:
```
parsed=$(echo "$var" | awk '/Runde:|HTTP:/ {gsub(/\r/,""); printf "%s  Z   ",$0}')
```

And the output is this:
```
2017-11-16 16:44:11	HTTP: 200	Time: 0,029  Z		Curl: 0
```

Now it looks like awk doesn't work.

How can fix?


Thanks

---

### Post by norobro on 2017-11-16
> **dam034 said:**
> Now it looks like awk doesn't work.It's working or you would not get the "HTTP:" in the output.  It's just not detecting "Runde:" for some reason.

Do you have "-I" in the curl  command in your script?

---

### Post by dam034 on 2017-11-16
No, it was gone from my head.

Now it works.

Thanks :popcorn:

---

