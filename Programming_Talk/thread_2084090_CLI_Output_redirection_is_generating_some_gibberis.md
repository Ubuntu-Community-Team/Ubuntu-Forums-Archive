---
title: "CLI Output redirection is generating some gibberish"
date: 2012-11-14
forum: Programming Talk
---

### Post by yma981 on 2012-11-14
I am running:
./ibmonitor --bytes --max --avg --data MB --interval 5 > ./$(date +%Y%m%d).txt

CLI Output redirection is generating some gibberish

_**Redirected output:**_

[H[2J Interface  Received      Sent     Total
                KBps      KBps      KBps

 eth0           0.00      0.00      0.00
[31m |---- Max[0m[31m      0.00[0m[31m      0.00[0m[31m      0.00[0m
[32m |---- Avg[0m[32m      0.00[0m[32m      0.00[0m[32m      0.00[0m
[35m |- Amount[0m[35m   0.00 KB[0m[35m   0.00 KB[0m[35m   0.00 KB[0m

 lo             0.00      0.00      0.00
[31m |---- Max[0m[31m      0.00[0m[31m      0.00[0m[31m      0.00[0m
[32m |---- Avg[0m[32m      0.00[0m[32m      0.00[0m[32m      0.00[0m
[35m |- Amount[0m[35m   0.00 KB[0m[35m   0.00 KB[0m[35m   0.00 KB[0m

 wlan0          0.98      0.63      1.61
[31m |---- Max[0m[31m      0.98[0m[31m      0.63[0m[31m      1.61[0m
[32m |---- Avg[0m[32m      0.98[0m[32m      0.63[0m[32m      1.61[0m
[35m |- Amount[0m[35m   4.90 KB[0m[35m   3.15 KB[0m[35m   8.05 KB[0m

 All            0.98      0.63      1.61
[31m |---- Max[0m[31m      0.98[0m[31m      0.63[0m[31m      1.61[0m
[32m |---- Avg[0m[32m      0.98[0m[32m      0.63[0m[32m      1.61[0m
[35m |- Amount[0m[35m   4.90 KB[0m[35m   3.15 KB[0m[35m   8.05 KB[0m

 Press ctrl+c to quit...        Elapsed time: 0 hrs, 0 mins, 5 s

_**Actual output should look:**_

 Interface  Received      Sent     Total
                KBps      KBps      KBps

 eth0           0.00      0.00      0.00
 |---- Max      0.00      0.00      0.00
 |---- Avg      0.00      0.00      0.00
 |- Amount   0.00 KB   0.00 KB   0.00 KB

 lo             0.00      0.00      0.00
 |---- Max      0.00      0.00      0.00
 |---- Avg      0.00      0.00      0.00
 |- Amount   0.00 KB   0.00 KB   0.00 KB

 wlan0          0.19      0.25      0.44
 |---- Max      0.19      0.25      0.44
 |---- Avg      0.19      0.25      0.44
 |- Amount   0.95 KB   1.25 KB   2.20 KB

 All            0.19      0.25      0.44
 |---- Max      0.19      0.25      0.44
 |---- Avg      0.19      0.25      0.44
 |- Amount   0.95 KB   1.25 KB   2.20 KB

 Press ctrl+c to quit...        Elapsed time: 0 hrs, 0 mins, 5 s

Any idea why ???

10x

---

### Post by chuck_theobald on 2012-11-14
Your terminal is not interpreting the square-bracket commands, likely to be asking for color, correctly. Check the setting of the TERM environment variable:

echo ${TERM}

What do you see when you cat the file? Also, what is the result when you run the ibmonitor command without redirection?

[edit, more information]
From the ibmonitor sourceforge page:

"The ibmonitor perl script makes use of the perl modules Term::ReadKey, **Term::ANSIColor** and Time::HiRes"

and

"--nocolors  	No fancy coloring please!"

The latter would be explained in the man page.

---

### Post by yma981 on 2012-11-14
> **chuck_theobald said:**
> Your terminal is not interpreting the square-bracket commands, likely to be asking for color, correctly. Check the setting of the TERM environment variable:

echo ${TERM}

What do you see when you cat the file? Also, what is the result when you run the ibmonitor command without redirection?

[edit, more information]
From the ibmonitor sourceforge page:

"The ibmonitor perl script makes use of the perl modules Term::ReadKey, **Term::ANSIColor** and Time::HiRes"

and

"--nocolors      No fancy coloring please!"

The latter would be explained in the man page.

I appreciate your support thank you alot 

the echo ${TERM}

return xterm

I just added the --nocolors option and the output file turned out ok. 

THANK YOU chuck_theobald

---

