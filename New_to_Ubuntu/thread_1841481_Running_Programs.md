---
title: "Running Programs"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by mbaker2311 on 2011-09-09
I am trying to determine what a Linux server is running so I can identify it's use to the company. How can I determine what functions and programs a Linux server is executing? For example, in Windows, I would look at the Task Manager, to see what programs were running, and might also peek at running processes. I would also look under the share manager, to see if was a file server. Ditto for printers/print server. I would also look under programs to see what programs are installed. Finally, I would look at msconfig to see what services are running and what's set to launch at boot. I know *top* shows running processes, but it's hard to say if that's a program, or just part of the OS. How would you go about finding out a Linux server's function in a company from the command line?

---

### Post by TeoBigusGeekus on 2011-09-09
Try with
```
ps aux
```

---

### Post by mbaker2311 on 2011-09-09
> **TeoBigusGeekus said:**
> Try with
```
ps aux
```
 
Well, yes, like *top*, it shows me what processes are running, their PID, which is useful, but it doesn't tell me if this sis a file server, or a print server, or an app server, and which files/printers/apps are loaded.  There must be some way to see which non-operating system programs/files have been installed after the fact, or if it is being used as a file server, or a web server, or an app server?

---

### Post by gdonwallace on 2011-09-09
top or the more graphical htop are the tools you want to use.

What you are describing is looking in task manager and seeing whats running, knowing what those program names are and what they run.  

top / htop does the same thing, just familiarity with the programs names.  As for what printers are installed, if its a file server, web server and what services are running, your best bet is to check the different log files located in /var/log/.  This will show you what is happening during boot up.  As for what is installed on the machine, it can be done from the command line using dselect.  But you may need to install that program.  dselect works much like synaptic manager, only dselect is written to run in a non-gui environment.  There is an option in both to see what has already been installed, just be prepared for a lot of information because everything on that linux box is in actuality a file.

---

### Post by mbaker2311 on 2011-09-09
Thanks!  Well, not good news, I suppose, but it is what it is.  All this CLI, it's taking me back to DOS!  MS may do a lot of things poorly, but I have to give 'em props for some of their reporting tools.  On the other hand, somewhere out there, some smart cookie has surely put together some kind of reporting tool that I want - I just have to find it.  Thanks again.

---

### Post by oldos2er on 2011-09-10
Maybe what you're looking for is ```
sudo service --status-all | less
``` ?

---

### Post by The Cog on 2011-09-10
**sudo netstat -plntu**
will list the listening network ports and their owning processes. Dont' worry about the ones listening on ::1 or 127.0.0.1 as these aren't accessoble over the network.

Of course that won't show the programs that are running that aren't network services, or those that only run occasionally as a scheduled task. /etc/crontab lists the scheduled tasks.

---

