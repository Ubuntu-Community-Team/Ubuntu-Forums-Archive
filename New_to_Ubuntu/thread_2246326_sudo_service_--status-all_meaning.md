---
title: "sudo service --status-all meaning"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by Michael_Knapp on 2014-09-29
When I do sudo service --status-all, it displays a '+', '-' or '?' next to each service, but when I do status on those services individually it does not match the output of --status-all:

```
mike@ubuntu:~$ sudo service --status-all
...
 [ - ]  mongodb
...
 [ - ]  tomcat7
...
mike@ubuntu:~$ sudo service tomcat7 status
 * Tomcat servlet engine is not running.
mike@ubuntu:~$ sudo service mongodb status
mongodb start/running, process 1064

```

so in this case --status-all had a '-' for both services, but when I checked, it said mongodb was actually running.  I tried 'man service' and it says this:

"service  --status-all  runs  all init scripts, in alphabetical order, with the status command. 
This option only calls status for sysvinit jobs, upstart jobs can be queried in a similar manner with initctl list'."

That did not explain to me what the '-', '+', and '?' mean to me, and it's apparently not what I expected.  So I think I am confused about how to interpret the output of --status-all, would somebody please explain it to me?

---

### Post by tgalati4 on 2014-09-30
Yes, the documentation is lacking.  Looking at the status of individual jobs it seems the status marker is as follows:

[?] Unknown job status--could be running or could be stopped, probably not an Upstart job or the response to "status" is unknown or unrecognized or nothing returned.
[-]  Not running, but installed and recognized as an Upstart job.  Could be started with the *service* command.
[+]  Running, and installed as an Upstart job.  Could be stopped with the *service* command.

> tgalati4@Mint14-Extensa ~ $ sudo service rwhod status
 * rwhod is running
tgalati4@Mint14-Extensa ~ $ sudo service urandom status
tgalati4@Mint14-Extensa ~ $ sudo service hddtemp status
 * hddtemp is not running


---

### Post by steeldriver on 2014-09-30
I think the confusion arises because some upstart scripts are just wrappers for SYSV style init scripts. Try running 'initctl list' as well and compare the results.

---

