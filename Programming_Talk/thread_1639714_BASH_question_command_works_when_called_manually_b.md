---
title: "BASH question: command works when called manually but not when called by a program"
date: 2010-12-07
forum: Programming Talk
---

### Post by daqron on 2010-12-07
I have a strange BASH script problem. There is a command in my script that works fine when the script is called from the command line, but doesn't work if the script is called by another program. Here is the simplified code. 

```
#!/bin/bash
echo `date` >> debug.log
echo `heyu status A1` >> debug.log

```

When I type "bash script.sh" in the terminal, the debug.log file shows the date and the output of the heyu command. When the script is triggered by a program, the log only gets the date; no output from the command is captured. 

"heyu" is a command-line interface to the X10 automation system. Without worrying about the particulars of heyu, is there a reasonable explanation for why a command within a script can work when the script is run manually, but not when it's run automatically? I thought maybe it had to do with the script running as root, but if I do "sudo bash script.sh" from the terminal, I also get the command output.

Any help is appreciated!

---

### Post by DaithiF on 2010-12-07
Could be a path issue ... where is heyu executable -- is it in your PATH?  Try an explicit path to heyu.

also, i don't know why you use echo and a backtick command when you could just run the command itself, ie.
```
date >> file
```
rather than
```
echo `date` >> file

```

---

### Post by daqron on 2010-12-07
> **DaithiF said:**
> Could be a path issue ... where is heyu executable -- is it in your PATH?  Try an explicit path to heyu.

Thanks for the response. Yes, I did try the full path. I also made sure my logfile was pointing to the absolute path. The heyu path is /usr/local/bin/heyu.

> **DaithiF said:**
> also, i don't know why you use echo and a backtick command when you could just run the command itself

Because I'm dumb. I changed that too and it didn't fix the problem. 

I did some further troubleshooting and discovered:[LIST]
[*]All the heyu processes run under my account, not root
[*]Same problem occurs if I do this with a perl script
[*]The heyu activity monitor shows the status command being executed even when the script is triggered automatically, which means that the status command was successfully given by the script, but its output is not getting captured. [/LIST]
This is driving me crazy. If it just didn't work at all I'd probably have given up 3 hours ago, but it's killing me that it works when I manually execute the script.

---

### Post by DaithiF on 2010-12-07
strange.  what is the other program that is calling the script?

---

### Post by yeleek on 2010-12-07
Try something like htop, lsof etc to see what its doing when run?

---

### Post by Milliways on 2010-12-07
> **daqron said:**
> I have a strange BASH script problem. There is a command in my script that works fine when the script is called from the command line, but doesn't work if the script is called by another program. Here is the simplified code. 

```
#!/bin/bash
echo `date` >> debug.log
echo `heyu status A1` >> debug.log

```

When I type "bash script.sh" in the terminal, the debug.log file shows the date and the output of the heyu command. When the script is triggered by a program, the log only gets the date; no output from the command is captured. 


I am not an expert on bash, but this would not work under Windows.

I suggest you try redirecting the output of the program which calls your script, rather than trying to perform multiple redirects within the script.

---

### Post by daqron on 2010-12-07
Thanks for the additional suggestions. I tried all of them and still no luck with this. I've done some more experiments and I'm fairly confident that it's a problem with heyu and not a shell scripting issue.

My best guess is that the heyu daemon is busy and can't address the status request because it's doing something else (i.e., waiting for the script it just called to finish executing).

Is it possible to issue a command to run a shell script but not wait for its output or completion? I tried "/path/to/script.sh &" but that didn't work.

Answers to your questions:

> **DaithiF said:**
> strange.  what is the other program that is calling the script?
It's some combination of two heyu daemons (heyu_engine and heyu_relay). I believe the engine is what triggers scripts to run when certain events occur. 
[QUOTE=yeleek]Try something like htop, lsof etc to see what its doing when run?[/QUOTE]
htop shows that the bash script runs, but that's all I can see. Since the heyu daemons are already running, presumably no new process is created to issue the 'status' command. Does that make sense or am I missing some obvious functionality of htop that could tell me more?
[QUOTE=Milliways]I suggest you try redirecting the output of the program which calls your script, rather than trying to perform multiple redirects within the script.[/QUOTE] 
I am not sure what you are suggesting ... I need the script to issue a command and record its output in a log. That is a fairly straightforward and common task for a bash script. You're right about the multiple redirects being sloppy; I have fixed that per DaithiF's suggestion (removed *echo* and added explicit paths) so the line looks like this:
```
/usr/local/bin/heyu -c /path/to/x10config status A1 >> $log

```The argument "-c /path/to/x10config" explicitly sets the path to the heyu config file, in case there were any environment issues there.

---

### Post by Milliways on 2010-12-07
> **daqron said:**
> Thanks for the additional suggestions. I tried all of them and still no luck with this. I've done some more experiments and I'm fairly confident that it's a problem with heyu and not a shell scripting issue.

I am not sure what you are suggesting ... 

I would have called the script like:-
```
bash test.sh >> debug.log

```

I don't claim this will fix your problem, but this has 2 advantages
1. You can run the script without redirection to test
2. It is easier to change the name of the target file.

---

### Post by saulgoode on 2010-12-07
> **daqron said:**
> I am not sure what you are suggesting ... I need the script to issue a command and record its output in a log. That is a fairly straightforward and common task for a bash script. You're right about the multiple redirects being sloppy; I have fixed that per DaithiF's suggestion (removed *echo* and added explicit paths) so the line looks like this:
```
/usr/local/bin/heyu -c /path/to/x10config status A1 >> $log

```The argument "-c /path/to/x10config" explicitly sets the path to the heyu config file, in case there were any environment issues there.

I would question which directory **$log** is being saved in (i.e., what is the working directory from which the script is invoked) -- better still provide an absolute path such as /tmp/heyu.log or /var/log/heyu/errors.log

---

### Post by daqron on 2010-12-07
So I reconfigured it again. Still makes no sense.

- Running the command directly works (root or not)
- Running the command via a script from terminal works (root or not)
- Having cron run the script does not work
- Having heyu run the script does not work

Doesn't cron run as root? How can root run a script and get a different result than cron!? All commands and file locations use explicit paths.

---

### Post by saulgoode on 2010-12-08
> **daqron said:**
> So I reconfigured it again. Still makes no sense.

- Running the command directly works (root or not)
- Running the command via a script from terminal works (root or not)
- Having cron run the script does not work
- Having heyu run the script does not work

Doesn't cron run as root?
Each user has his own cron table. The command will run as the user who added the job (to his crontab). 

> How can root run a script and get a different result than cron!? All commands and file locations use explicit paths.
Though the user may be the same, the environment may be different. (There can even be some differences in the environment depending upon whether the user is running under sudo, and on how sudo has been configured.)

Now that all of your paths are explicit, this is not likely to be a problem (assuming that the user who create cron job has the necessary permissions to any files or directories). If there is an environment problem, you should examine whether your 'heyu' program depends on or uses any environment settings.

I am not that familiar with the cron implementation used by Ubuntu (Vixie?). I use Dillon's cron which is a bit more straightforward. Under Dillon's cron any output to stdout or stderr produced by the job gets collected and mailed to the user. 

I would not expect a re-direction to a log file to be included in, or interfere with, such a mailing but it might be worthwhile for you to investigate this for *your* cron implementation (it may even be a problem with my cron implementation, but I have never tried implementing logging in that manner). Your system's cron implementation may even provide some explicit logging mechanism.

Also, you might also double-check whether the output produced by 'heyu' is to stdout and not stderr; or combine both pipes ("2>&1") before appending them to the log file.

---

### Post by daqron on 2010-12-08
> **saulgoode said:**
> Also, you might also double-check whether the output produced by 'heyu' is to stdout and not stderr; or combine both pipes ("2>&1") before appending them to the log file.
Thanks for the explanation on cron. What you articulated about its behavior is what I assumed to be the case. I think your last note was the key. I already had the script piping stdout and stderr into an output string that is reported to the log. For whatever reason, that directive is what didn't work in cron (even though it worked when I ran the script manually). 

So it's working now. It seems that I was dealing with two separate problems. With the original shell script I posted, I still don't know what the problem was. I researched the heyu engine some more and it is fully capable of multiple parallel operations, so my hypothesis about it being too busy was probably wrong. After re-writing in perl and testing with cron, the problem seems to have been trying to capture stderr and stdout.

Of course, these explanations could still be completely wrong, but it's working now so I'm calling it solved.

Thanks again to everyone who provided input. I really appreciate your time.

Cheers,
Jeremy

---

