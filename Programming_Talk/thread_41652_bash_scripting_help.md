---
title: "bash scripting help"
date: 2005-06-14
forum: Programming Talk
---

### Post by Gandalf on 2005-06-14
Hello guys,
i have a problem with my server i won't tell all the story here, anyway i'm trying to get a quick fix, as a format didn't solve it, till i know where the problem is coming from, the problem is that apache hang up, he consume 100% CPU and server load just keep going up ( the max i saw the load was 69.7 ), no way to bring it down without restarting apache,
so i've done a little script that runs via crontab each 10 minutes to verify the load, if the load is above 10, then restart apache, but unfortunately i can't get it working, here's what i wrote

```

#!/bin/bash
date
echo ""
cat /proc/loadavg
load=$?;

if [ "${load}" -gt "10" ]; then
        echo ""
        echo "restarting apache..."
        invoke-rc.d apache2 restart
fi

``` but $load is always equal 0, so i tried to put $load=`cat /proc/loadavg` but i don't know how to get the first characters of it :(

if anyone knows how to do with shell scripting or even perl scripting, please help me it's so small and so usefull for me

any help is really appreciated

---

### Post by Gandalf on 2005-06-14
as i am a PHP programmer i did it with PHP, here's what i've done if someone is interrested too
```


#!/usr/bin/php
<?

//this script will check server load and compare it to the below defined constant, if the load is above it, apache will be restarted
//if not it will not be restarted..
define ("MAX_LOAD", 6);

//getting the date
$date = date("D M j G:i:s T Y");

echo $date . "\n";

$cm = exec("cat /proc/loadavg");
if(!$cm)
        die("execution of the command \"cat /proc/loadavg\" has failed");

//getting the current load....
$load = explode(" ", $cm);


if ( $load[0] > MAX_LOAD ) /* if the load is above the MAX_LOAD average, then we must restart apache, otherwize we don't restart it */
{
        echo "apache need to be restarted, load is \"" . $load[0] . "\"\n";
        $res=exec("invoke-rc.d apache2 restart");
        if(!$res)
                die("could not restart apache");
}
else
{
        echo "the server load is \"" . $load[0] . "\" so apache will not be restarted\n";
}


//finishing the script
echo "-----------------------------------------------------------------------------------------------\n";

?>

```

maybe this code is a bit slower than shell scripting, so if someone knows how to fix the shell please tell me

---

### Post by LordHunter317 on 2005-06-14
A better solution would be to figure out what the hell you're doing to make Apache's load run away like that.

That's a very bad, bad thing, and restarting Apache isn't the correct solution.  Ever.  Period.

So much in fact, I'm not going to tell you how to fix it until you provide more details about the Apache problem.  That's how fundamentally wrong what you're doing is.

---

### Post by Gandalf on 2005-06-14
[QUOTE=LordHunter317]A better solution would be to figure out what the hell you're doing to make Apache's load run away like that.

That's a very bad, bad thing, and restarting Apache isn't the correct solution.  Ever.  Period.

So much in fact, I'm not going to tell you how to fix it until you provide more details about the Apache problem.  That's how fundamentally wrong what you're doing is.[/QUOTE]
 if i know what happens i would have fixed it, i was on debian sarge, i switched to ubuntu hoary and then back to debian sarge, see 2 times i formatted and the same issue is here,
i noticed a lot of similar cases happens with people using mambo i use mambo for my site

---

### Post by LordHunter317 on 2005-06-14
Well, if you don't know what's causing it, you could at least say, this is what I changed last before it broke.  

Check for hung processes, log messages reporting errors.  What's likely happening is some piece of PHP code is running off into space, eating up resources.

BTW, reformatting wont' ever fix issues like this, so I'm not sure why you've bothered.

---

### Post by Gandalf on 2005-06-14
[QUOTE=LordHunter317]Well, if you don't know what's causing it, you could at least say, this is what I changed last before it broke.  

Check for hung processes, log messages reporting errors.  What's likely happening is some piece of PHP code is running off into space, eating up resources.

BTW, reformatting wont' ever fix issues like this, so I'm not sure why you've bothered.[/QUOTE]
 that's what actually annoying me, no error in logs, nothing weird with server/php becuase sometimes at night where not even one visitor on site it hangs, i searched all logs i can't figure out the reason

---

### Post by LordHunter317 on 2005-06-14
Did you check all your logs (including system ones)?

That sounds like mambo is running some sort of scheduled task somehow that's eating the server alive.

You obviously haven't found the pattern yet, but one must exist.

---

### Post by Gandalf on 2005-06-14
[QUOTE=LordHunter317]Did you check all your logs (including system ones)?

That sounds like mambo is running some sort of scheduled task somehow that's eating the server alive.

You obviously haven't found the pattern yet, but one must exist.[/QUOTE]
 well i checked the whole /var/log/apache2 dir also dmesg anything else to see?

anyway the problem too is he hanging is so random really random it happens once a week, a month or every 10 mns :(

---

### Post by Gandalf on 2005-06-14
it just happened it's the second time that happens and my script didn't work i goe in the log (coz i'm logging script activity that the script died on the command die if apache failed to be restarted
here's the top when the server was crashing
```

top - 22:21:13 up 5 days,  7:40,  2 users,  load average: 30.95, 34.18, 33.25
Tasks: 110 total,   2 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.2% us,  1.6% sy,  0.0% ni,  0.0% id, 95.2% wa,  0.0% hi,  0.0% si
Mem:    516612k total,   513556k used,     3056k free,     1140k buffers
Swap:  1967952k total,  1434060k used,   533892k free,    41152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7521 root      15   0  2064  936 1852 R  1.3  0.2   0:20.94 top
12650 www-data  15   0 48728 7724  13m D  1.3  1.5   0:03.01 apache2
    1 root      16   0  1504  184 1352 S  0.0  0.0   0:01.37 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0
    3 root       5 -10     0    0    0 S  0.0  0.0   0:03.84 events/0
    4 root       5 -10     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      14 -10     0    0    0 S  0.0  0.0   0:00.00 kacpid
   43 root       5 -10     0    0    0 S  0.0  0.0   0:41.45 kblockd/0
   56 root       5 -10     0    0    0 S  0.0  0.0   0:00.00 aio/0
   55 root      15   0     0    0    0 S  0.0  0.0   2:48.42 kswapd0
  198 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
  302 root      15   0     0    0    0 D  0.0  0.0   0:26.40 kjournald
  789 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 1242 root      15   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 1696 root      19   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1709 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 2675 root      15   0  2260  312 2092 D  0.0  0.1   0:05.01 syslogd
 2678 root      16   0  2448  172 1344 S  0.0  0.0   0:00.11 klogd
 2686 bind      18   0 31556 2296 4248 S  0.0  0.4   0:00.00 named
 2712 root      15   0 50120 1912 3672 S  0.0  0.4   0:00.66 freepopsd
 2717 root      18   0  1672  128 1360 S  0.0  0.0   0:00.00 courierlogger
 2718 root      16   0  1808  172 1468 S  0.0  0.0   0:00.02 authdaemond.pla
 2719 root      16   0  2616  632 1468 S  0.0  0.1   0:02.00 authdaemond.pla
 2720 root      16   0  2220  232 1468 S  0.0  0.0   0:02.58 authdaemond.pla
 2721 root      15   0  2220  376 1468 D  0.0  0.1   0:02.27 authdaemond.pla
 2722 root      16   0  2616  232 1468 S  0.0  0.0   0:02.12 authdaemond.pla
 2723 root      16   0  1808  552 1468 S  0.0  0.1   0:02.29 authdaemond.pla
 2729 root      16   0  2476  120 2164 S  0.0  0.0   0:00.00 couriertcpd
 2732 root      17   0  1672  132 1360 S  0.0  0.0   0:00.00 courierlogger
 2737 root      16   0  2476  192 2164 S  0.0  0.0   0:00.98 couriertcpd
 2740 root      16   0  1672  256 1360 S  0.0  0.0   0:01.82 courierlogger
 2746 root      21   0  1496  116 1344 S  0.0  0.0   0:00.00 inetd
 2762 root      23   0  2504  124 2380 S  0.0  0.0   0:00.02 mysqld_safe
 2798 root      23   0  2504  124 2380 S  0.0  0.0   0:00.00 mysqld_safe

```

i runned the script manually apache restarted
```

server:~# nice -20 /usr/bin/resapache
Tue Jun 14 22:22:51 CEST 2005
apache need to be restarted, load is "27.85"
-----------------------------------------------------------------------------------------------

```

but the cron run the same command "nice -20 /usr/bin/resapache >> /var/log/apache2/cronres" in the log:

```

Tue Jun 14 21:25:37 CEST 2005
apache need to be restarted, load is "10.30"
could not restart apache
Tue Jun 14 21:31:22 CEST 2005
apache need to be restarted, load is "27.98"
could not restart apache
Tue Jun 14 21:35:29 CEST 2005
apache need to be restarted, load is "20.74"
could not restart apache
Tue Jun 14 21:40:56 CEST 2005
apache need to be restarted, load is "25.31"
could not restart apache
Tue Jun 14 21:48:45 CEST 2005
apache need to be restarted, load is "32.24"
could not restart apache
Tue Jun 14 21:50:19 CEST 2005
apache need to be restarted, load is "33.38"
could not restart apache
Tue Jun 14 21:57:41 CEST 2005
apache need to be restarted, load is "31.66"
could not restart apache
Tue Jun 14 22:01:51 CEST 2005
apache need to be restarted, load is "49.13"
could not restart apache
Tue Jun 14 22:05:40 CEST 2005
apache need to be restarted, load is "35.56"
could not restart apache
Tue Jun 14 22:10:26 CEST 2005
apache need to be restarted, load is "33.27"
could not restart apache
Tue Jun 14 22:15:30 CEST 2005
apache need to be restarted, load is "32.62"
could not restart apache
Tue Jun 14 22:21:30 CEST 2005
apache need to be restarted, load is "29.11"
could not restart apache
Tue Jun 14 22:25:01 CEST 2005
the server load is "3.35" so apache will not be restarted
-----------------------------------------------------------------------------------------------

```

WTH :o :o :o

---

### Post by LordHunter317 on 2005-06-14
Apache can't be restarted because it's in state 'D', meaning it's uninterruptable.  No signals can be delievered to it, including SIGKILL.  This is normally due to a process doing a lot of I/O.

And yes, you should be looking at other logs. When I say system logs, I mean  /var/log/daemon, /var/log/messages, /var/log/syslog, and so on.  The end output of dmesg might be helpful to see if this is hardware related (specifically, dying disks causing I/O errors causing hung processes).

lsof on the apache process in question might be interesting to see, it may be possible to identify what file it's writing to that way.

---

### Post by Gandalf on 2005-06-14
look can i pack the whole /var/log and PM you with a dowload address, please it makes me crazy i've been like this since 2 months, on MIRC neither here nor on LQ.org they could help me

---

### Post by LordHunter317 on 2005-06-14
That's not likely to help.  Going over logs post-mortem may very well be useless without a complete system image.  

You could still post the two things I asked for ('dmesg | tail' and the output from lsof for that process).

---

### Post by Gandalf on 2005-06-14
dmesg doesn't contain something new it contains what happened 3 days ago when i stopped NFS and portmap server
```

server:~# dmesg | tail
TCP: Treason uncloaked! Peer 213.180.234.246:61001/80 shrinks window 4277421846:4277427686. Repaired.
nfsd: last server has exited
nfsd: unexporting all filesystems
rpciod: active tasks at shutdown?!
RPC: failed to contact portmap (errno -5).
atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
TCP: Treason uncloaked! Peer 202.174.154.50:2433/2000 shrinks window 1678659057:1678660493. Repaired.

```

can u please explain what u actually want from lsof? because it's a bit HUGE

---

### Post by LordHunter317 on 2005-06-14
I want the output of lsof for the process that's in state 'D'.  You'll have to look up it's PID and pass it to lsof; I think it's the '-p' option, but I don't remember.  You'll have to read the manual page.

Which is exactly what I said eariler, albiet with more explict directions.

---

### Post by z0mbix on 2005-06-17
> **Gandalf]Hello guys,
i have a problem with my server i won't tell all the story here, anyway i'm trying to get a quick fix, as a format didn't solve it, till i know where the problem is coming from, the problem is that apache hang up, he consume 100% CPU and server load just keep going up ( the max i saw the load was 69.7 ), no way to bring it down without restarting apache,
so i've done a little script that runs via crontab each 10 minutes to verify the load, if the load is above 10, then restart apache, but unfortunately i can't get it working, here's what i wrote

```

#!/bin/bash
date
echo ""
cat /proc/loadavg
load=$? said:**
> ; then
        echo ""
        echo "restarting apache..."
        invoke-rc.d apache2 restart
fi

``` but $load is always equal 0, so i tried to put $load=`cat /proc/loadavg` but i don't know how to get the first characters of it :(

if anyone knows how to do with shell scripting or even perl scripting, please help me it's so small and so usefull for me

any help is really appreciated


As stated previously, this isn't atall the right solution but you can use cut to get the first characters like so:

```

#!/bin/bash
date
echo
load=$(cut -f1 -d. /proc/loadavg)

if [ $load -gt "10" ]; then
        echo ""
        echo "restarting apache..."
        invoke-rc.d apache2 restart
fi

``` 

man cut for more info.

---

### Post by Gandalf on 2005-06-17
Thx for your answer i think i solved the issue, i'm still testing it, now it's up since 19 hours without even one crash or system above load 1 (where normally in 19 hrs uptime it crash more than 3 times). 
the issue was one of the following that i changed:
1- i disabled the uneded module (mod_rewrite)
2- i increased maxclients values as i had in the error log (same time as the crash) error maxclients reached think to increase the maxclients

---

### Post by LordHunter317 on 2005-06-17
Sounds like you hit a bug where the server failed to properly lock itself out, or a mod_rewrite pattern that was running forever.  Either of which is very bad.

---

### Post by Gandalf on 2005-06-19
ok i just found the following when i was monitoring the time of crashes (it is the first crash since 3 days, 2 hours and 8 minutes, and it is the maximum time i had betwen crashes),
so in /var/log/apache2/error.log i can see this

Warnings (it's a huge list so i take the first 9 lines)
```
[Mon Jun 20 05:02:19 2005] [warn] child process 3698 still did not exit, sending a SIGTERM
[Mon Jun 20 05:02:19 2005] [warn] child process 2834 still did not exit, sending a SIGTERM
[Mon Jun 20 05:02:19 2005] [warn] child process 4460 still did not exit, sending a SIGTERM
[Mon Jun 20 05:02:19 2005] [warn] child process 32258 still did not exit, sending a SIGTERM
[Mon Jun 20 05:02:19 2005] [warn] child process 1227 still did not exit, sending a SIGTERM
[Mon Jun 20 05:02:19 2005] [warn] child process 1080 still did not exit, sending a SIGTERM
[Mon Jun 20 05:02:19 2005] [warn] child process 2607 still did not exit, sending a SIGTERM
[Mon Jun 20 05:02:19 2005] [warn] child process 4252 still did not exit, sending a SIGTERM
[Mon Jun 20 05:02:19 2005] [warn] child process 3773 still did not exit, sending a SIGTERM

```

and after the list of warning, i have the errors (same thing, long list so i took the first 9 lines)
```
[Mon Jun 20 05:02:25 2005] [error] child process 3698 still did not exit, sending a SIGKILL
[Mon Jun 20 05:02:25 2005] [error] child process 2834 still did not exit, sending a SIGKILL
[Mon Jun 20 05:02:25 2005] [error] child process 4460 still did not exit, sending a SIGKILL
[Mon Jun 20 05:02:25 2005] [error] child process 32258 still did not exit, sending a SIGKILL
[Mon Jun 20 05:02:25 2005] [error] child process 1227 still did not exit, sending a SIGKILL
[Mon Jun 20 05:02:25 2005] [error] child process 1080 still did not exit, sending a SIGKILL
[Mon Jun 20 05:02:25 2005] [error] child process 2607 still did not exit, sending a SIGKILL
[Mon Jun 20 05:02:25 2005] [error] child process 4252 still did not exit, sending a SIGKILL
[Mon Jun 20 05:02:25 2005] [error] child process 3773 still did not exit, sending a SIGKILL
```

and at the same time when i run invoke-rc.d apache2 restart i have this
> [Mon Jun 20 05:02:26 2005] [notice] caught SIGTERM, shutting down
[Mon Jun 20 05:02:36 2005] [notice] Apache/2.0.54 (Debian GNU/Linux) PHP/4.3.10-15 configured -- resuming normal operations
[Mon Jun 20 05:05:13 2005] [notice] caught SIGTERM, shutting down
[Mon Jun 20 05:05:13 2005] [notice] Apache/2.0.54 (Debian GNU/Linux) PHP/4.3.10-15 configured -- resuming normal operations



i increased again the max client, i donno if it's safe to have them like this
```
<IfModule prefork.c>
StartServers         10
MinSpareServers      5
MaxSpareServers     10
MaxClients          100
MaxRequestsPerChild  0
</IfModule>


<IfModule worker.c>
StartServers         4
MaxClients         200
MinSpareThreads     25
MaxSpareThreads     75
ThreadsPerChild     25
MaxRequestsPerChild  0
</IfModule>

```

---

### Post by Gandalf on 2005-06-22
Ok till now i didn't have the problem yet, so i re-activated the mod_rewrite as i prefer using SEF urls,

will inform if anything new happens

thx

---

### Post by LordHunter317 on 2005-06-22
Your processes aren't dying for some reason, which is bad.  That's what's causing the apache parent to hang.

Set MaxRequestsPerChild to some low value, like 1000, to make sure the processes aren't leaking memory/resources and don't live forever.  This may help the problem.

---

### Post by Gandalf on 2005-06-22
[QUOTE=LordHunter317]Your processes aren't dying for some reason, which is bad.  That's what's causing the apache parent to hang.

Set MaxRequestsPerChild to some low value, like 1000, to make sure the processes aren't leaking memory/resources and don't live forever.  This may help the problem.[/QUOTE]
 ok now it is like this

```

<IfModule prefork.c>
StartServers         10
MinSpareServers      5
MaxSpareServers     10
MaxClients          100
MaxRequestsPerChild  1000
</IfModule>


<IfModule worker.c>
StartServers         4
MaxClients         200
MinSpareThreads     25
MaxSpareThreads     75
ThreadsPerChild     25
MaxRequestsPerChild  1000
</IfModule>

```

let's see if that change something

---

### Post by LordHunter317 on 2005-06-22
You can ignore the worker.c section, as you're not using it.  It's not safe to use with mod_php4.

---

### Post by Gandalf on 2005-06-22
[QUOTE=LordHunter317]You can ignore the worker.c section, as you're not using it.  It's not safe to use with mod_php4.[/QUOTE]
 i don't know if it is in use or not, it is not in the mods-[enabled/available] folder, here's what i have enabled mods
```

server:/etc/apache2/mods-enabled# ls
cgi.load  php4.conf  php4.load  rewrite.load  userdir.conf  userdir.load

```

---

### Post by LordHunter317 on 2005-06-22
It's an MPM, not a module.  An MPM is responsible for process control under Apache2.  You can only have one enabled at any one time (which is why those directives are in <IFModule> sections).

And I know you're not using it, because libapache2-mod-php4 explictly depends on apache2-mpm-prefork, as that's the only MPM safe for use with mod_php4 under Apache2 (on Linux anyway).

---

### Post by Gandalf on 2005-06-22
ok man, thanks for the hint, i'll keep you in touch of what happens by increasing that value from 0 to 1000 till now the server is quite cool...

---

### Post by Gandalf on 2005-06-22
hmmmm... i think that wasn't stable at all, server did not crash but server load was between 9 and 15, he don't get down nor go up then 15, so i didn't restart it, i stop it, restored the value to 0, left the server to cool down and start apache again, now it's under 1, let's see if it go up again i'll try what u suggest later because i wanna test if the rewrite module has any effect (enable it today, turned mambo into SEF site)

---

### Post by Gandalf on 2005-06-22
Ok it is indeed the mod_rewrite who makes it like this, i was away not watching the top and i just saw the HDD LED always on, i opened the terminal where i have the top already running and i find load 110.56 which is enorm, then the monitor light up showing mysql out of memory process killed etc... so i closed port 80 from the router and waiting till the server treats the invoke-rc.d apache2 stop command, coz the last time i reboot -f the server i had problems in some mysql tables :(, gonna be a long wait now.... :(

Ok after about a half an hour waiting to apache stop and server load go back to normal, i archived the whole /var/log directory and copied it to my laptop and i'll begin to see them all and quote what is weird

/var/log/apache2/errors.log
like the other day i have huge numbers of warn/errors here's an example
```

[Wed Jun 22 23:55:27 2005] [warn] child process 32514 still did not exit, sending a SIGTERM
[Wed Jun 22 23:55:29 2005] [error] child process 32302 still did not exit, sending a SIGKILL

```

/var/log/messages
i have something i have never saw yet, that's what bring the monitor on, i had it on screen
```

Jun 23 01:55:17 server kernel: <B low:40kB high:60kB active:5524kB inactive:5596kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1368kB min:700kB low:1400kB high:2100kB active:181344kB inactive:274844kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 0*4kB 11*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1400kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 17*8kB 1*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1368kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156502, delete 4156354, find 2754362/2977694, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2768kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:54874 inactive:61985 dirty:0 writeback:0 unstable:0 free:692 slab:3398 mapped:121535 pagetables:1754
Jun 23 01:55:17 server kernel: DMA free:1400kB min:20kB low:40kB high:60kB active:5756kB inactive:5620kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1368kB min:700kB low:1400kB high:2100kB active:213740kB inactive:242320kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 0*4kB 11*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1400kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 17*8kB 1*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1368kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156502, delete 4156354, find 2754362/2977694, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2768kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:80805 inactive:36134 dirty:0 writeback:0 unstable:0 free:692 slab:3398 mapped:121535 pagetables:1754
Jun 23 01:55:17 server kernel: DMA free:1400kB min:20kB low:40kB high:60kB active:5756kB inactive:5748kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1368kB min:700kB low:1400kB high:2100kB active:317464kB inactive:138788kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 0*4kB 11*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1400kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 17*8kB 1*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1368kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156502, delete 4156354, find 2754362/2977694, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2768kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:49245 inactive:67646 dirty:0 writeback:0 unstable:0 free:692 slab:3398 mapped:121535 pagetables:1754
Jun 23 01:55:17 server kernel: DMA free:1400kB min:20kB low:40kB high:60kB active:5756kB inactive:5748kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1368kB min:700kB low:1400kB high:2100kB active:191224kB inactive:264836kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 0*4kB 11*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1400kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 17*8kB 1*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1368kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156502, delete 4156354, find 2754362/2977694, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2768kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:86869 inactive:30086 dirty:0 writeback:0 unstable:0 free:692 slab:3398 mapped:121535 pagetables:1754
Jun 23 01:55:17 server kernel: DMA free:1400kB min:20kB low:40kB high:60kB active:5756kB inactive:5748kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1368kB min:700kB low:1400kB high:2100kB active:341720kB inactive:114596kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 0*4kB 11*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1400kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 17*8kB 1*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1368kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156502, delete 4156354, find 2754362/2977694, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0xd2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        3100kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:115651 inactive:1462 dirty:0 writeback:0 unstable:0 free:775 slab:3333 mapped:121545 pagetables:1754
Jun 23 01:55:17 server kernel: DMA free:1428kB min:20kB low:40kB high:60kB active:5372kB inactive:5848kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1672kB min:700kB low:1400kB high:2100kB active:457232kB inactive:0kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 5*4kB 12*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1428kB
Jun 23 01:55:17 server kernel: Normal: 64*4kB 25*8kB 0*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1672kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156839, delete 4156691, find 2754362/2977699, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0xd2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2888kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:71981 inactive:45184 dirty:0 writeback:0 unstable:0 free:722 slab:3325 mapped:121587 pagetables:1754
Jun 23 01:55:17 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:7204kB inactive:4132kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1448kB min:700kB low:1400kB high:2100kB active:280720kB inactive:176604kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 6*4kB 13*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 01:55:17 server kernel: Normal: 12*4kB 23*8kB 0*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1448kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156953, delete 4156781, find 2754382/2977731, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2824kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:59854 inactive:57314 dirty:0 writeback:0 unstable:0 free:706 slab:3327 mapped:121598 pagetables:1763
Jun 23 01:55:17 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:5628kB inactive:5628kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1384kB min:700kB low:1400kB high:2100kB active:233788kB inactive:223628kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 6*4kB 13*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 21*8kB 0*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1384kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156968, delete 4156819, find 2754384/2977735, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2824kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:8559 inactive:108769 dirty:0 writeback:0 unstable:0 free:706 slab:3321 mapped:121598 pagetables:1763
Jun 23 01:55:17 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:5440kB inactive:5816kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1384kB min:700kB low:1400kB high:2100kB active:28796kB inactive:429260kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 6*4kB 13*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 21*8kB 0*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1384kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156968, delete 4156819, find 2754384/2977735, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2824kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:99294 inactive:17938 dirty:0 writeback:0 unstable:0 free:706 slab:3321 mapped:121598 pagetables:1763
Jun 23 01:55:17 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:5500kB inactive:5884kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1384kB min:700kB low:1400kB high:2100kB active:391676kB inactive:65868kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 6*4kB 13*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 21*8kB 0*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1384kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156968, delete 4156819, find 2754384/2977735, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0xd0
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2824kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:97653 inactive:19707 dirty:0 writeback:0 unstable:0 free:706 slab:3321 mapped:121598 pagetables:1763
Jun 23 01:55:17 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:5884kB inactive:5372kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1384kB min:700kB low:1400kB high:2100kB active:384728kB inactive:73456kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 6*4kB 13*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 21*8kB 0*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1384kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156968, delete 4156819, find 2754384/2977735, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2824kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:15566 inactive:101807 dirty:0 writeback:0 unstable:0 free:706 slab:3321 mapped:121598 pagetables:1763
Jun 23 01:55:17 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:5468kB inactive:5916kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1384kB min:700kB low:1400kB high:2100kB active:56796kB inactive:401312kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 6*4kB 13*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 21*8kB 0*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1384kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156968, delete 4156819, find 2754384/2977735, race 13+27
Jun 23 01:55:17 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 01:55:17 server kernel: DMA per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 01:55:17 server kernel: Normal per-cpu:
Jun 23 01:55:17 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 01:55:17 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 01:55:17 server kernel: HighMem per-cpu: empty
Jun 23 01:55:17 server kernel: 
Jun 23 01:55:17 server kernel: Free pages:        2824kB (0kB HighMem)
Jun 23 01:55:17 server kernel: Active:23555 inactive:93773 dirty:0 writeback:0 unstable:0 free:706 slab:3321 mapped:121598 pagetables:1763
Jun 23 01:55:17 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:5416kB inactive:5840kB present:16384kB
Jun 23 01:55:17 server kernel: protections[]: 10 360 360
Jun 23 01:55:17 server kernel: Normal free:1384kB min:700kB low:1400kB high:2100kB active:88804kB inactive:369252kB present:507840kB
Jun 23 01:55:17 server kernel: protections[]: 0 350 350
Jun 23 01:55:17 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 01:55:17 server kernel: protections[]: 0 0 0
Jun 23 01:55:17 server kernel: DMA: 6*4kB 13*8kB 4*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 01:55:17 server kernel: Normal: 0*4kB 21*8kB 0*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1384kB
Jun 23 01:55:17 server kernel: HighMem: empty
Jun 23 01:55:17 server kernel: Swap cache: add 4156968, delete 4156819, find 2754384/2977735, race 13+27
Jun 23 02:11:11 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 02:12:52 server kernel: DMA per-cpu:
Jun 23 02:12:52 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 02:12:52 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 02:12:52 server kernel: Normal per-cpu:
Jun 23 02:12:52 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 02:12:52 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 02:12:52 server kernel: HighMem per-cpu: empty
Jun 23 02:12:52 server kernel: 
Jun 23 02:28:49 server kernel: Free pages:        2840kB (0kB HighMem)
Jun 23 02:28:49 server kernel: Active:59674 inactive:60357 dirty:0 writeback:0 unstable:0 free:710 slab:3233 mapped:122031 pagetables:1561
Jun 23 02:28:49 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:5596kB inactive:5372kB present:16384kB
Jun 23 02:28:49 server kernel: protections[]: 10 360 360
Jun 23 02:28:49 server kernel: Normal free:1400kB min:700kB low:1400kB high:2100kB active:233100kB inactive:236056kB present:507840kB
Jun 23 02:28:49 server kernel: protections[]: 0 350 350
Jun 23 02:28:53 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 02:28:53 server kernel: protections[]: 0 0 0
Jun 23 02:28:53 server kernel: DMA: 2*4kB 5*8kB 9*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 02:28:53 server kernel: Normal: 14*4kB 2*8kB 7*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1400kB
Jun 23 02:28:53 server kernel: HighMem: empty
Jun 23 02:28:53 server kernel: Swap cache: add 4548721, delete 4548571, find 2780564/3036214, race 29+140
Jun 23 02:28:53 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 02:28:53 server kernel: DMA per-cpu:
Jun 23 02:28:53 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 02:28:53 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 02:28:53 server kernel: Normal per-cpu:
Jun 23 02:28:57 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 02:28:57 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 02:28:57 server kernel: HighMem per-cpu: empty
Jun 23 02:28:57 server kernel: 
Jun 23 02:28:57 server kernel: Free pages:        3168kB (0kB HighMem)
Jun 23 02:28:57 server kernel: Active:60058 inactive:59564 dirty:0 writeback:0 unstable:0 free:792 slab:3218 mapped:122023 pagetables:1561
Jun 23 02:28:57 server kernel: DMA free:1448kB min:20kB low:40kB high:60kB active:5500kB inactive:5468kB present:16384kB
Jun 23 02:28:57 server kernel: protections[]: 10 360 360
Jun 23 02:28:57 server kernel: Normal free:1720kB min:700kB low:1400kB high:2100kB active:234732kB inactive:232788kB present:507840kB
Jun 23 02:28:57 server kernel: protections[]: 0 350 350
Jun 23 02:28:57 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 02:28:57 server kernel: protections[]: 0 0 0
Jun 23 02:28:57 server kernel: DMA: 4*4kB 5*8kB 9*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1448kB
Jun 23 02:28:57 server kernel: Normal: 94*4kB 2*8kB 7*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1720kB
Jun 23 02:28:57 server kernel: HighMem: empty
Jun 23 02:28:57 server kernel: Swap cache: add 4548753, delete 4548603, find 2780564/3036218, race 29+140
Jun 23 02:28:57 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 02:28:57 server kernel: DMA per-cpu:
Jun 23 02:28:57 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 02:28:57 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 02:28:57 server kernel: Normal per-cpu:
Jun 23 02:28:57 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 02:28:57 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 02:28:57 server kernel: HighMem per-cpu: empty
Jun 23 02:28:57 server kernel: 
Jun 23 02:28:57 server kernel: Free pages:        2840kB (0kB HighMem)
Jun 23 02:28:57 server kernel: Active:30825 inactive:88627 dirty:0 writeback:0 unstable:0 free:710 slab:3204 mapped:122033 pagetables:1561
Jun 23 02:28:57 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:5316kB inactive:5396kB present:16384kB
Jun 23 02:28:57 server kernel: protections[]: 10 360 360
Jun 23 02:28:57 server kernel: Normal free:1400kB min:700kB low:1400kB high:2100kB active:117984kB inactive:349112kB present:507840kB
Jun 23 02:28:57 server kernel: protections[]: 0 350 350
Jun 23 02:28:57 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 02:28:57 server kernel: protections[]: 0 0 0
Jun 23 02:28:57 server kernel: DMA: 2*4kB 5*8kB 9*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 02:28:57 server kernel: Normal: 14*4kB 2*8kB 7*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1400kB
Jun 23 02:28:57 server kernel: HighMem: empty
Jun 23 02:28:57 server kernel: Swap cache: add 4549015, delete 4548865, find 2780566/3036254, race 29+140
Jun 23 02:28:57 server kernel: oom-killer: gfp_mask=0x1d2
Jun 23 02:28:57 server kernel: DMA per-cpu:
Jun 23 02:28:57 server kernel: cpu 0 hot: low 2, high 6, batch 1
Jun 23 02:28:57 server kernel: cpu 0 cold: low 0, high 2, batch 1
Jun 23 02:28:57 server kernel: Normal per-cpu:
Jun 23 02:28:57 server kernel: cpu 0 hot: low 32, high 96, batch 16
Jun 23 02:28:57 server kernel: cpu 0 cold: low 0, high 32, batch 16
Jun 23 02:28:57 server kernel: HighMem per-cpu: empty
Jun 23 02:28:57 server kernel: 
Jun 23 02:28:57 server kernel: Free pages:        2840kB (0kB HighMem)
Jun 23 02:28:57 server kernel: Active:1328 inactive:118220 dirty:0 writeback:0 unstable:0 free:710 slab:3204 mapped:122033 pagetables:1561
Jun 23 02:28:57 server kernel: DMA free:1440kB min:20kB low:40kB high:60kB active:5312kB inactive:5400kB present:16384kB
Jun 23 02:28:57 server kernel: protections[]: 10 360 360
Jun 23 02:28:57 server kernel: Normal free:1400kB min:700kB low:1400kB high:2100kB active:0kB inactive:467480kB present:507840kB
Jun 23 02:28:57 server kernel: protections[]: 0 350 350
Jun 23 02:28:57 server kernel: HighMem free:0kB min:128kB low:256kB high:384kB active:0kB inactive:0kB present:0kB
Jun 23 02:28:57 server kernel: protections[]: 0 0 0
Jun 23 02:28:57 server kernel: DMA: 2*4kB 5*8kB 9*16kB 5*32kB 1*64kB 0*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1440kB
Jun 23 02:28:57 server kernel: Normal: 14*4kB 2*8kB 7*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1400kB
Jun 23 02:28:57 server kernel: HighMem: empty
Jun 23 02:28:57 server kernel: Swap cache: add 4549015, delete 4548865, find 2780566/3036254, race 29+140
Jun 23 02:50:31 server -- MARK --

```


that's all i have seen in the log files that i expect to see in, please if you know another thing to look inside tell me the logs are archived

---

