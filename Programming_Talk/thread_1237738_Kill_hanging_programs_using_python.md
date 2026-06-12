---
title: "Kill hanging programs using python"
date: 2009-08-11
forum: Programming Talk
---

### Post by lian1238 on 2009-08-11
Hi, I'm a python scripter (level: noob). As a practice, I've written a script to monitor the CPU usage of selected programs and restart them if suspected of hanging. :)

I've also included a simple configuration tool to get started.
Warning: I don't check for bad input from the user. For process, enter the name of the process (e.g. **rhythmbox**). For threshold, enter the CPU usage which the process may not exceed. (e.g. **50**) It means, if rhythmbox uses more than 50% of CPU, it will be restarted.

I'm looking for comments about my code. Maybe efficiency or portability. Anything helpful. I'm sure a sh script will be faster :confused:, but I'm not looking to learn that yet.

file: killer.py
```
#!/usr/bin/env python
"""Kills and restarts selected processes if they use CPU above their limit"""
## Version 0.1

##################################################
## Author: Lian
##### Python n00b
##
## Date: Aug 12, 2009
## Email: lian{dot}hui{dot}lui{at}gmail{dot}com
##################################################

import time # for sleep
import os   # for popen
import subprocess # for calling a subprocess

## read the config file
listfile = "killerlist" # the list of processes are stored here 

f = open(listfile,'r')
print "Loading list.."
file = f.read()

processes = file.split('\n') # processes are separated by a newline 

pname = []
limit = []
count = []

sleeptime = 2 # in seconds # time to sleep between each query
tolerate = 10 # number of times to tolerate CPU usage above limit before killing
## for example with sleeptime = 2, tolerate = 10, a hanging process will die after 20 seconds

## get the process name and its limit
for i in processes:
    t = i.split('\t')
    if( len(t) == 2):
        print "found: ",i
        pname.append(t[0])
        limit.append(t[1])
        count.append(0)

print "done" # done loading list

while(True): # this script never ends.. unless an error occurs
    for i in range(0,len(pname)): # loop for each process
        pid = os.popen("pgrep "+pname[i]+" | tail -n 1").readline().strip()
        if pid == "":
            print pname[i],"is not running"
            break

        ## two different ways to get the CPU usage, which one is better?
        # cpu = os.popen('ps -o "%C" -p '+pid+' | tail -n 1').readline().strip()
        cpu = os.popen('top -b -n 1 -p '+pid).read().split('\n')[7][41:45].strip() # get the cpu column

        print pname[i], # print process name
        print pid, # print pid
        print "(cpu",cpu,"with limit",limit[i]+")",
        if(cpu == ""):
            print "couldn't get cpu, skip once"
            break
        over = (float(cpu)>float(limit[i]))
        print over, count[i]
        if(over):
            if(count[i] > tolerate):
                subprocess.call("killall "+pname[i]+"; "+pname[i]+" > /dev/null &", shell=True)
            else:
                count[i] = count[i]+1
        else:
            count[i] = 0 # reset count

    time.sleep(sleeptime)

## EOF
```file: killerconf.py
```
#!/usr/bin/env python
"""A crude configuration tool for killer.py"""
## Version 0.1

##################################################
## Author: Lian
##### Python n00b
##
## Date: Aug 12, 2009
## Email: lian{dot}hui{dot}lui{at}gmail{dot}com
##################################################

listfile = "killerlist" # filename of list

print "Welcome to killer config"

## Menu
def menu():
    print "1) List all"
    print "2) Clear all"
    print "3) Add"
    print "0) Exit"

choice = -1

while(choice != 0):
    menu()
    choice = int(raw_input("Enter choice: "))
    if(choice == 1):
        f = open(listfile, 'r')
        print f.read()
    elif(choice == 2):
        f = open(listfile, 'w')
    elif(choice == 3):
        p = str(raw_input("Enter process: "))
        t = str(raw_input("Enter threshold: "))
        f = open(listfile, 'a')
        f.write(p+"\t"+t+"\n")
    elif(choice == 0):
        print "Exiting"
    else:
        print "Bad choice"

```

---

### Post by slavik on 2009-08-12
how do you decide if a process is hung? I cannot tell from the code. also, ps way is better (IMO).

CPU usage of 100% by a process is a completely useless metric.

---

### Post by PaulFr on 2009-08-12
The appropriate condition IMHO to declare a process hung is to use the stack trace as the condition in your code (see the pstack example in Linux at **_[http://developers.sun.com/solaris/articles/solaris_linux_app.html](http://developers.sun.com/solaris/articles/solaris_linux_app.html)_**).

If the stack trace is identical for those **n** samples, and **n** x **time between samples** is reasonably large,  that would be a strong indicator that the process is **hung**.

---

### Post by lian1238 on 2009-08-12
> **slavik said:**
> how do you decide if a process is hung? I cannot tell from the code. also, ps way is better (IMO).

CPU usage of 100% by a process is a completely useless metric.

In the file "killerlist", there is the process name and the limit. This limit decides whether a process is hanging. In my case, 50 is a good limit for rhythmbox. Since, normal usage takes only 10%, and hanging takes 100% (or above!).

I used ps, but it doesn't show the actual usage at the current time. Here's an extract from man ps:
```
       %cpu      %CPU   cpu utilization of the process in "##.#" format.
                        Currently, it is the CPU time used divided by the time the
                        process has been running (cputime/realtime ratio),
                        expressed as a percentage. It will not add up to 100%
                        unless you are lucky. (alias pcpu).
```

**PaulFr**, thanks for the info. I've installed pstack. Now, I'm just waiting for a hanging process.

---

