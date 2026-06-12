---
title: "I need to stop a running service, then edit its run/conf file"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by docJ on 2013-04-20
Hello,

I recently installed CrashPlan (a backup program) on my new computer running Ubuntu 12.04 x64 desktop.

 The initial backup has stopped when it reached around 40/45%, with a program specific error.
Googling it gave me this seemingly easy 2 steps solution: stop the service & edit one number in its run config file.
Being such a Ubuntu noob, I am uncertain how to stop the service, and therefore unable to edit the config file.

The how to fix is at: [http://askubuntu.com/questions/128053/crashplan-and-samba-printing-problems-after-upgrade-to-12-04](http://askubuntu.com/questions/128053/crashplan-and-samba-printing-problems-after-upgrade-to-12-04) (look for [Christian Riedel]("http://askubuntu.com/users/65172/christian-riedel")'s answer)

[B]The how to stop the background engine service "recipe" is at the bottom of [http://support.crashplan.com/doku.php/recipe/stop_and_start_engine?redirect=1](http://support.crashplan.com/doku.php/recipe/stop_and_start_engine?redirect=1)
[/B]
When I navigate to usr/local/crashplan/bin, I see the file "CrashPlanEngine", but then what am I supposed to do there?
I have 4 options: Run in terminal, Display, Cancel, and Run

---

### Post by Cheesemill on 2013-04-20
First you need to navigate correct directory...
```
cd /usr/local/crashplan/bin
```
Then issue the stop command...
```
./CrashPlanEngine stop
```

---

### Post by docJ on 2013-04-20
I dont't know if I'm doing something wrong, here's the result:
```
jlr@ub3:~$ cd /usr/local/crashplan/bin
jlr@ub3:/usr/local/crashplan/bin$ ./CrashPlanEngine stop
Stopping CrashPlan Engine ... Still running, killing PID=19807 ... 
./CrashPlanEngine: line 150: kill: (19807) - Operation not permitted
OK
jlr@ub3:/usr/local/crashplan/bin$ 


```

---

### Post by Cheesemill on 2013-04-20
Sorry, you need to run the command with root privileges...
```
sudo ./CrashPlanEngine stop
```

---

### Post by docJ on 2013-04-20
```
Stopping CrashPlan Engine ... Still running, killing PID=21293 ... 
OK
```
:cool:
Thanks !
Now step2:
I need to go to: /usr/local/crashplan/bin/run.conf and edit a number, when I try with Nautilus I get a message its read only and I can't edit it. What do I type on the terminal to edit?

PS: Is it stopped for good (until I restart it only same way but with start instead of stop), or just rebooting would restart it, as far as you know?

---

### Post by docJ on 2013-04-20
OK, I managed by going gksudo nautilus, I was then able to edit the file.
I will restart the service and see if I got rid of my program error...

---

### Post by docJ on 2013-04-20
I think doing it with gksudo was not good, I now have an edited run.conf file and next to it a run.conf.save that seems a copy of the original unedited file

---

### Post by docJ on 2013-04-20
I compared the files, they were identical but for the single edited number (and file name)
I have deleted the (copy) run.conf.save and all is well

Thanks for now, I have to increase number a bit, try again, if no joy: increase a bit again and try again, and so on...

---

