---
title: "using Kill -INT in a shutdown script"
date: 2016-11-21
forum: New to Ubuntu
---

### Post by swirlyraindrop on 2016-11-21
I am trying to shutdown a rosnode using a script that runs at shutdown/reboot. Currently this node does not automatically close during the shutdown/reboot.

My script is super simple

#!/bin/sh

echo "scriptrunning"| wall

kill -INT $(pidof imu_3dm_gx4)

sleep 5

echo "killed" | wall

I used chmod 755 "scriptname" to turn script into executable, file is save in init.d and created a link in rc0.d and rc6.d as K99scriptname. I have tried many different flavors of K and S and cannot get the "kill" portion of the script to run

---

### Post by kingneutron on 2016-11-30
> I am trying to shutdown a rosnode using a script that runs at shutdown/reboot. Currently this node does not automatically close during the shutdown/reboot.

--I am not familiar with rosnode, but I found this while googling it:

[http://wiki.ros.org/rosnode](http://wiki.ros.org/rosnode)

--If this is correct, why are you using a "keyboard interrupt" KILL signal (according to ' man 7 signal '**) instead of the ' rosnode kill ' command?

```

** man 7 signal:
Signal     Value     Action   Comment
       &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
       SIGHUP        1       Term    Hangup detected on controlling terminal
                                     or death of controlling process
       SIGINT        2       Term    Interrupt from keyboard
       SIGQUIT       3       Core    Quit from keyboard
       SIGILL        4       Core    Illegal Instruction
       SIGABRT       6       Core    Abort signal from abort(3)
       SIGFPE        8       Core    Floating point exception
       SIGKILL       9       Term    Kill signal
       SIGSEGV      11       Core    Invalid memory reference
       SIGPIPE      13       Term    Broken pipe: write to pipe with no
                                     readers
       SIGALRM      14       Term    Timer signal from alarm(2)
       SIGTERM      15       Term    Termination signal
       SIGUSR1   30,10,16    Term    User-defined signal 1
       SIGUSR2   31,12,17    Term    User-defined signal 2
       SIGCHLD   20,17,18    Ign     Child stopped or terminated
       SIGCONT   19,18,25    Cont    Continue if stopped
       SIGSTOP   17,19,23    Stop    Stop process
       SIGTSTP   18,20,24    Stop    Stop typed at terminal
       SIGTTIN   21,21,26    Stop    Terminal input for background process
       SIGTTOU   22,22,27    Stop    Terminal output for background process

```

--General advice: Use the "logger" command instead of "wall" - this will use syslog instead of sending a message to everyone on the system.

Example: 

killpid=`pidof imu_3dm_gx4`
' logger -s "INFO: Killing rosnode $killpid" '
#( do your kill here )
sleep 5
ps h $killpid # see if it's still there

--Also the version of Ubuntu you are running may be important, in my experience 14.04 is easier to work with when it comes to init scripts.

---

