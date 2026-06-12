---
title: "Unresponsive server"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by Sapph1r3 on 2014-02-24
Hi there,
I previously posted for help doing an upgrade and got wonderful help, thanks again to those that took the time to help.
I'm hoping I can get a similar response as I am definitely a beginner with this.
We have a web server running Ubuntu 12.04 LTS, previously 11.10.
Before and after the upgrade it becomes unresponsive.
I am able to ping it but unable to get to it via webmin.
It is a remote server and this has been the only way I could access it without going down to it physically.
What I am hoping to get out of this is to be pointed in a direction as where to look.
I have been able to find some things in logs, but with this problem I have no idea what I would be looking for or which log to refer to.
The server is completely unresponsive physically as well.
I went out once when it entered this state, screen won't come on and no response from keyboard or mouse.
If anyone can guide me in any way, it would be greatly appreciated.

edit: I managed to get the machine rebooted, below output from top command:

```
top - 11:41:49 up 26 min,  1 user,  load average: 1.07, 1.34, 1.74Mem:   2056336k total,  1531596k used,   524740k free,   296120k buffers
Swap:  3080188k total,        0k used,  3080188k free,   620024k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1107 root      20   0  164m  25m  14m S  0.0  1.3   0:12.78 Xorg
 2191 www-data  20   0  313m  53m 5876 S  0.0  2.7   0:05.35 apache2
 1064 mysql     20   0  858m  64m 7968 S  0.0  3.2   0:04.28 mysqld
 2591 www-data  20   0  304m  46m 3588 S  0.0  2.3   0:03.24 apache2
 2190 www-data  20   0  304m  46m 3540 S  0.0  2.3   0:02.93 apache2
 1230 kdm       20   0  447m  44m  23m S  0.3  2.2   0:02.84 kdm_greet
 2696 www-data  20   0  310m  52m 4092 S  0.0  2.6   0:02.02 apache2
 2697 www-data  20   0  303m  43m 5504 S  0.0  2.1   0:01.93 apache2
 1403 clamav    20   0 49820 1996 1108 S  0.0  0.1   0:01.89 freshclam
 2515 user      20   0 17340 1348 1012 R  0.0  0.1   0:01.85 top
 2756 www-data  20   0  314m  52m 5676 S  0.0  2.6   0:01.25 apache2
 2536 root      30  10  4388  904  612 D  0.0  0.0   0:00.99 updatedb.mlocat
    1 root      20   0 24472 2408 1292 S  0.0  0.1   0:00.87 init
 2698 www-data  20   0  296m  35m 4688 S  0.0  1.8   0:00.63 apache2
 2753 www-data  20   0  289m  30m 3316 S  0.0  1.5   0:00.53 apache2
 2754 root      20   0     0    0    0 R  0.3  0.0   0:00.41 kworker/0:0
 1202 bind      20   0  157m  20m 3080 S  0.0  1.0   0:00.34 named
  435 root      20   0 17236  640  444 S  0.0  0.0   0:00.18 upstart-udev-br
```



potentially solved by kernel upgrade - monitoring

---

### Post by knpoe on 2014-02-24
do you have the upgraded webmin? have you updated its dependencies? 

assuming you're able to ssh to the host as this is how you're checking the logs?

perhaps this will help a bit? [http://www.rackspace.com/knowledge_center/article/ubuntu-1204-lts-webmin-1630](http://www.rackspace.com/knowledge_center/article/ubuntu-1204-lts-webmin-1630) *(i like rackspace- they have awesome support and docs)

 i would recommend trying to back up the configs you have for webmin and going through the steps to install it again-- this may not be necessary - but im having trouble from your post identifying exactly what the problem could be...

---

### Post by Sapph1r3 on 2014-02-25
Apologies if there is a lack of information (feeling under the weather)
I don't think the problem is webmin, the version is the most updated one.
The first things I check when I can't reach the server using webmin is if I can get to the Samba shared folder and if the websites hosted on it are accessible.
We do a hard reboot and then are able to access the server once more.
When it gets into this state, it does not respond to mouse or keyboard and nothing can be seen on the screen (when viewing locally - I have to work remotely as the server is not at the same location)

---

### Post by Sapph1r3 on 2014-03-17
Bump

---

### Post by Sapph1r3 on 2014-06-30
This problem is still ongoing and has now seemed to have advanced in that this has happened 3 days in a row.
I did updates on Friday and rebooted the box, got in this morning and cannot ssh or webmin into the box, but am still able to ping it without issues.
We did identify that it appears to be under DOS attacks (this was picked up on our firewall logs)...could this be a factor.
It isn't the only one under attack but may be the worst affected?
ClamAV is running on the server, but there is an error updating it, I cannot get the error right now as it is still in unresponsive state.
I am going to try to get to the box physically tomorrow morning, so any advice with this before then would be greatly appreciated.
Thanks in advance

---

