---
title: "How to create Daemon (if possible some examples)"
date: 2007-06-20
forum: Programming Talk
---

### Post by ran_foru on 2007-06-20
HI ...

Hey i new to ubuntu. I got a small project in which i have to create a daemon using shell script. i went through many link but every where only discussion r there . can someone  put some small example to create daemon with brief explanation or give some link or book. 

Thx in Advance :(:(

---

### Post by Mr. C. on 2007-06-20
How about any open source project available on sourceforge?  You can have your pick of any of the hundreds of daemonizing servers.

MrC

---

### Post by ran_foru on 2007-06-20
> **Mr. C. said:**
> How about any open source project available on sourceforge?  You can have your pick of any of the hundreds of daemonizing servers.

MrC

Hi..

thx for quick reply.
Hey we cant use others  tool  even it is open source for our project according to company policy. so i have to write my own script and since it is used in many more places so i have to clear concept about every thing

---

### Post by Mr. C. on 2007-06-20
If you really want to learn, pick up a couple of Unix/Liinux programming books.  There is just too much material to be covered in a forum such as this.

MrC

---

### Post by meatpan on 2007-06-20
A daemon is a process that is not associated with a terminal.  Rather than writing output to a tty, simply direct your program output to a log file of some sort.   Instant daemon!

---

### Post by Mr. C. on 2007-06-20
Hmmm... not quite.

```
while : ; do 
  echo
done > /dev/null
```
is not a daemon nor is:
```

( ls -R / > /dev/null < /dev/null 2>&1 )
```

A daemon has a number of properties; terminal dissociation is but one.

MrC

---

### Post by ran_foru on 2007-06-20
> **Mr. C. said:**
> If you really want to learn, pick up a couple of Unix/Liinux programming books.  There is just too much material to be covered in a forum such as this.

MrC


hi..

if u have any ebook give me the link and also the link or  forum discussion. 

Actually there is a small server program which runs fine but detaching from terminal we need deamons and also we cant use rcconf tool because it should be a part of program.

---

### Post by eentonig on 2007-06-20
rather than talking about semantics, what is it that you want to achieve? I doubt your company wants to run a daemon, just for the fun of having a daemon running?

The source code that Mr. C referred to, doesn't mean you have to use those programs. It means that you can look in to their code and see how they did it. And then createyour code based on those ideas.

---

### Post by HackingYodel on 2007-06-20
> **ran_foru said:**
> hi..

if u have any ebook give me the link and also the link or  forum discussion. 

Actually there is a small server program which runs fine but detaching from terminal we need deamons and also we cant use rcconf tool because it should be a part of program.

These may help:
[http://www.linuxboxadmin.com/articles/tools-and-utilities/a-bourne-again-daemon.html](http://www.linuxboxadmin.com/articles/tools-and-utilities/a-bourne-again-daemon.html)
[http://www.linuxjournal.com/article/2335](http://www.linuxjournal.com/article/2335)

The information is not exhaustive, by any definition, but should point you in the general direction.

I hope that helps!

---

### Post by hasimir44 on 2007-06-21
here's a pointless example using bash and perl. you could use cron to schedule the start and check scripts. use the kill script if you need to kill it before 11pm.. 

```
#!/bin/bash
# start_daemon.sh

echo $$ > /tmp/daemon_pid
now=`date '+%H'`
# stop running at 11:00pm 
while [ $now -lt 23 ]
do
  # this is a pointless example
  tail /var/log/auth.log |grep -i error >> /tmp/errors.log
  sleep 5
  now=`date '+%H'`
done
rm -f /tmp/daemon_pid

```

```
#!/usr/bin/perl
# check_daemon.pl

my $msg  = "The daemon is dead, head for the hills!!\n";
if (-s '/tmp/daemon_pid') {
  my $pid  = `cat /tmp/daemon_pid`;
  print $msg unless `ps -ef |grep $pid`;
} else {
  print $msg;
}

```

```

#!/bin/bash
# kill_daemon.sh

if [ -s /tmp/daemon_pid ]
then
        kill -9 `cat /tmp/daemon_pid`
        rm -f /tmp/daemon_pid
fi

```

demo: 

```

prompt> ./start_daemon.sh &
[1] 11647
prompt> ./check_daemon.pl 
prompt> ./kill_daemon.sh 
[1]+  Killed                  ./start_daemon.sh
prompt> ./check_daemon.pl 
The daemon is dead, head for the hills!!

```

---

### Post by Mr. C. on 2007-06-21
Its not clear exactly what the OP wanted; but your code does not represent a "daemon".  It is merely a background process.  It is *still* attached to STDIN and STDERR, and associated with the shell's process group, and is under the control of the shell (eg. job control).  See what happens when start_daemon.sh tries to read from STDIN.

MrC

---

### Post by hasimir44 on 2007-06-22
>  Its not clear exactly what the OP wanted; but your code does not represent a "daemon". It is merely a background process.

fair enough. would you mind posting a true example of a daemon? the op didn't specify much, but they did ask for examples.. 

this quote ([wikipedia]("http://en.wikipedia.org/wiki/Daemon_%28computer_software%29")) is interesting as it implies more than mere input/output redirection: 

> Daemons usually become daemons by forking a child process and then having the parent process immediately exit, thus causing init to adopt the child.

---

### Post by Mr. C. on 2007-06-22
Fox examples, look at any open source service, such as apache, vsftpd, postfix, or even perl based amavisd-new.  There's not much sense in repeating the basic fork/exec sequences.

The wikipedia definition and my statement are in agreement.  Perhaps you took "It is merely a background process" out of context.  The "it" in the statement was your code; ie. your code was merely a background process, not a daemon.

MrC

---

### Post by hasimir44 on 2007-06-22
I wasn't disagreeing with you. I posted the quote to back your statement up. Some of us aren't driven by ego alone :)

I am wondering though.. does a backup process still run if the terminal is closed? If so, this would sever the stdin,stdout, and stderr.  Would it then be considered a daemon?

---

### Post by Mr. C. on 2007-06-22
A process that is backgrounded can close its STDIN, STDOUT, and STDERR file descriptors; this has no impact on the processes run-ability. Background processes that are running when the parent shell exits are dealt with according to the setting of the shell's **nohup** option.

A sub-process' open file descriptors are not affected by the parent process once the process is running; therefore, the closing of the terminal (eg. the shell) does not sever the the sub-process' ties with the three standard descriptors.

Prove this to yourself:

```
(0<&- 2<&- 1<&-  sleep 20 &);  ps -ef | grep sleep
```

Did the sleep command not run because the descriptors were closed ?

Now do the same:

```
(0<&- 2<&- 1<&-  sleep 40 &); exit
```

but run the following command on another terminal:

```
ps -ef | grep sleep
```

MrC

---

### Post by zazuge on 2008-01-29
People forget sometimes the essential and start arging about the details

A daemon is just program that is the direct child of init process and it have his ouput and input not directed to a stdin (he can read from a file or a fifo ) & stdout (perhaps to a log file or the null device)

to have a programe to be the child of init process he must be orphaned so the init process will adopt him (Oh, poor little programe :3 )

the daemon have to handle signals correctly so he can be stoped & started cleanly

those are the basic rules of a daemon programme, apart from these basic rules other things are just black magic. :-p

---

