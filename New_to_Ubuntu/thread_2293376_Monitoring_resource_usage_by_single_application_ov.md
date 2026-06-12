---
title: "Monitoring resource usage by single application over period of time"
date: 2015-09-04
forum: New to Ubuntu
---

### Post by suryaveer2 on 2015-09-04
[COLOR=#111111][FONT=Ubuntu]I am looking for an utility which can monitor the resource usage (CPU & RAM) by an application.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have an third party application which runs as service, once started, it will receive requests periodically. Here, I want to monitor the resource usage under varying loads.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I searched and found few tools like nmon, collectd, collectl, atop,monitorix and more but I am not sure how to use them for my purpose. I have installed and they show some statics but I don't know if I have to write some script or plugin to fetch what I want.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It's just two months since I started working on Linux so its look bit intimidating to me.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I don't just want to see the current usage. I need to check the historical data and have a report, graphs.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks[/FONT][/COLOR]

---

### Post by cariboo on 2015-09-04
Top or htop doesn't work for you? Top is installed by default, and htop is in the repositories.

---

### Post by Habitual on 2015-09-04
So, you only want to monitor this "third party application"?

---

### Post by suryaveer2 on 2015-09-04
Yes. I want to have performance metrics for comparison with few others. I tried TOP, but I guess it just gives current status while I want to have a history for the period I am running the application. Then I need to plot it on graph.

---

### Post by mc4man on 2015-09-04
Maybe pidstat would serve you.
```
 sudo apt-get install sysstat
```
```
man pidstat
```
Look at the options & the examples of usage. Can be set to run at x interval for x amount of time & output to a log file
(the terminal must be left open but can be minimized

Note that the pid of your app will be different each time started so you'd need to start app, get it's pid & use that pid in pidstat
(- pa ax or ps aux or ps -A will show pids
(- to output to a log file just add after a space this to end of pidstat command
>> whatever.log

The sysstat package has other useful binaries, worth checking out.

---

### Post by suryaveer2 on 2015-09-04
Thanks. I have installed this and will try.
Is there a possibility to provide the service name because the application when started several child. Or does the parent PID resource usage covers the childs also. 
Sorry, I am not aware of internals.

---

### Post by mc4man on 2015-09-05
> **suryaveer2 said:**
> Thanks. I have installed this and will try.
Is there a possibility to provide the service name because the application when started several child. Or does the parent PID resource usage covers the childs also. 
Sorry, I am not aware of internals.
see here regarding childs, 1/2 way down  - [http://www.cyberciti.biz/open-source/command-line-hacks/linux-monitor-process-using-pidstat/](http://www.cyberciti.biz/open-source/command-line-hacks/linux-monitor-process-using-pidstat/)

---

### Post by suryaveer2 on 2015-09-05
> **mc4man said:**
> see here regarding childs, 1/2 way down  - [http://www.cyberciti.biz/open-source/command-line-hacks/linux-monitor-process-using-pidstat/](http://www.cyberciti.biz/open-source/command-line-hacks/linux-monitor-process-using-pidstat/)

Thanks. This is useful. I'll go through it and get back. :)

---

