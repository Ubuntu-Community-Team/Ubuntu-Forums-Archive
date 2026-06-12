---
title: "show burden of workstation"
date: 2009-09-04
forum: Programming Talk
---

### Post by flylehe on 2009-09-04
Hi,
I just jammed our workstation yesterday. I submit way too many jobs at the same time and somebody was running some intensive program so the machine quickly got unresponsive and rebooted. 

I wonder how you guys do the check before submitting your jobs? The only thing I know is "top" and look at the mem  total, used and free. If the free one is decreasing dramatically, I'd better to kill my jobs asap before it is too late. 

And I have little idea to pre-estimate the performance of my program.

Thanks and regards!

---

### Post by Arndt on 2009-09-04
> **flylehe said:**
> Hi,
I just jammed our workstation yesterday. I submit way too many jobs at the same time and somebody was running some intensive program so the machine quickly got unresponsive and rebooted. 

I wonder how you guys do the check before submitting your jobs? The only thing I know is "top" and look at the mem  total, used and free. If the free one is decreasing dramatically, I'd better to kill my jobs asap before it is too late. 

And I have little idea to pre-estimate the performance of my program.

Thanks and regards!

If there are several people using it, I might ask ("workstation" seems like not quite the right word then). There is also the little tool xload, which shows the current load. But that's CPU usage only, not memory.

---

### Post by flylehe on 2009-09-04
Thanks! 

xload is a cool gadget but not working under terminal.

How do you call the machine then? You caught me on this. I am quite lame at the wording such as server, workstation,.... The one we are using is for running programs.

> **Arndt said:**
> If there are several people using it, I might ask ("workstation" seems like not quite the right word then). There is also the little tool xload, which shows the current load. But that's CPU usage only, not memory.

---

### Post by Arndt on 2009-09-04
> **flylehe said:**
> Thanks! 

xload is a cool gadget but not working under terminal.

How do you call the machine then? You caught me on this. I am quite lame at the wording such as server, workstation,.... The one we are using is for running programs.

I don't know. If it's on someone's desk and used with screen and keyboard, I call it a workstation, but it may very well be used by others remotely as well. If no one works directly on it, I call it a server. What the operating system release has in its name may also be a factor. As long as you and your colleagues understand each other, it doesn't matter.

So how do you submit jobs to the workstation? Using ssh? Then you can login remotely, set the DISPLAY variable (unless there are security issues) and run xload remotely.

---

### Post by tgalati4 on 2009-09-04
uptime shows local machine load.

ruptime shows remote machine load.

apt-cache search uptime

sudo apt-get install rwho rwhod

Now ruptime will show all the machines on the network running rwhod with their load.

Don't forget to add IP's of watched machines in /etc/hosts.

You will get something like:

tgalati4@tubuntu2:~$ ruptime
minty3      down   41+21:02
minty4      down   34+16:17
tpad-Gloria7  up    1+20:45,     2 users,  load 0.91, 0.81, 0.90
tubuntu2      up   32+18:46,     1 user,   load 0.00, 0.04, 0.02
washme      down   10+16:58

Works on macs as well.

I found another:

apt-cache search rstat

But I haven't used it.

---

### Post by lensman3 on 2009-09-04
The "w" command will tell you the load on a system.  There is also a remote "w" command, except at this time I can't find it.

Look at the uptime command for what "units" the load is in.

---

