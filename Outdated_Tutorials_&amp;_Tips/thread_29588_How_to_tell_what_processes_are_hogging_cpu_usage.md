---
title: "How to tell what processes are hogging cpu usage"
date: 2005-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by crazybill on 2005-04-24
So your computer is going really slow and you don't know who the resource hog is.

Try this.

Open a terminal window.
Type **top** 

The "top" application  will ouput to your monitor the current processes running and updates every second. Hit the following key strokes at any time:

**M **    Sorts by current resident memory usage

**T**   Sorts by total ( or cummulaative) CPU usage

**p** Sorts by current CPU usage (this is the default refresh)

**?**   Displays a usage summary for all top commands

This is very important information to obtain when problem solving why a computer process is running slowly and making decisions on what processes to kill / software to uninstall.

---

### Post by Cal on 2005-04-25
You can also use the Monitor tool in the Applications - System Tools menu.  
Click the % sign to organize the processes by CPU usage
Change the "Show" setting to All Process to see if any system tools are causeing a problem.

---

### Post by shakin on 2005-04-26
While we're on the subject, there are lots of top-like tools for monitoring many things on your computer.

kerneltop - shows kernel usage in the same way that top shows process usage.
apachetop - monitors an apache web server: requests per second, bytes per second, etc.
htop - an improved version of top. You can scroll the list vertically and horizontally and kill processes without knowing the pid.
iftop - monitors bandwidth usage on a single interface.
mtop and mytop - both these tools monitor a mysql server.
ntop - top for your network. Can monitor networked machines and has a web interface.
dnstop - monitors dns traffic

I don't know of any tools that can monitor when a process is hitting the hard drive or to monitor various email servers. Hopefully somebody else can add tools for hdd and email server monitoring and that would pretty much complete the list for most monitoring needs.

---

### Post by crazybill on 2005-04-28
What shakin says is true. Those are all good tools. However, they are not installed out of the box with Hoary. They can be installed manually. "**top**" on the otherhand is ready to go.  Of course there is **ps**, too.    I often use **ps auwx | grep process_I_am_looking for** . For example **ps auwx | grep ssh**  to see if sshd is running and see info on it.

---

### Post by crazybill on 2005-04-28
What shakin says is true. Those are all good tools. 

However, they are not installed out of the box with Hoary. They can be installed manually... and with apt-get.... such as **apt-get install iftop** .

 "**top**" on the otherhand is ready to go.  

Of course there is **ps**, too.    I often use **ps auwx | grep process_I_am_looking for** . For example **ps auwx | grep ssh**  to see if sshd is running and see info on it.

---

