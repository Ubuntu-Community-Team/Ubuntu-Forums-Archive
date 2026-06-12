---
title: "Problem with Crontab and a speedtest script"
date: 2014-04-29
forum: Programming Talk
---

### Post by marco39 on 2014-04-29
Hi everybody, i've a problem with the periodic execution of a speedtest script through crontab.
I've wrote the following script invoking the speedtest-cli script, the script is the following:
**speed_script.sh**
```
#!/bin/shdate >> /home/user/speedtest.log
speedtest-cli --simple >> /home/user/speedtest.log
echo "" >> /home/user/speedtest.log
```
Then i've edited the crontab configuration file (**crontab -e**) with the following line, in order to test and write down the network speed every half an hour:
```
0,30 * * * * /home/user/speed_script.sh
```
So, the resulting file speedtest.log only contains the date of the tests, without the internet speed results.
:confused:
If I run the script manually from terminal, the script runs correctly and the speedtest.log contains the date anche the speedtest output.
Where's the mistake?
Thanks everybody...

This is the output file with crontab:
```
Tue Apr 29 11:00:53 CEST 2014
Download: 4.84 Mbits/s
Upload: 0.47 Mbits/s

Tue Apr 29 11:30:45 CEST 2014
Download: 3.89 Mbits/s
Upload: 0.38 Mbits/s
```
And this with the manual execution:
```
Tue Apr 29 11:47:11 CEST 2014

Tue Apr 29 11:51:32 CEST 2014

Tue Apr 29 11:55:08 CEST 2014

```

P.S. Sorry for my english, but it's not my native language...

---

### Post by ofnuts on 2014-04-29
Where is the "speedtest-cli" executable and is that in the execution path of whatever runs the cron jobs? Ddi you try to give a full path to it in the script?

---

### Post by marco39 on 2014-04-29
First thing: I began to study and use crontab only yesterday, so I know very little :(. 
I installed speedtest via [FONT=courier new]pip[/FONT] using the command pip install speedtest-cli so i don't know where the executable is. I tried to look it up in [FONT=courier new]/usr/bin[/FONT] but unsuccessfully.
Then i use l[FONT=courier new]ocate speedtest-cli[/FONT] and the result is [FONT=courier new]/usr/local/bin/speedtest-cli[/FONT].So i modified the script including the full path of speedtest-cli... and now seems to work!
Now i do some tests...
For now thank you so much!

---

### Post by marco39 on 2014-04-30
Alla seems working.. Thank you!

---

