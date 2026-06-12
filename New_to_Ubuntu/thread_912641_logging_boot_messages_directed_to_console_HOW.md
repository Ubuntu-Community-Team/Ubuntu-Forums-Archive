---
title: "logging boot messages directed to console? HOW?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by roadrun777 on 2008-09-06
Hello, I have been reading the forums for a few hours now and I am confused on some issues.
I am currently running Intrepid and I have read that Upstart replaced sysinitv system and now uses logd to "supposedly" log all boot messages.

My problem is that during boot up I see several error messages but I can not find any log file that contains these messages. 

"man logd" only gives a very basic description and nothing more of it's use.
I need a way to view the boot up messages so I can find the errors and see what is happening. It goes by way to fast and all I can make out is something regarding a read-only file and resolvconf issue.

I have seen several people post that dmesg logs everything, but it clearly does not. When I hit ctrl-alt-f8 I can see the tail end of all the boot console messages but I can't shift-pageup and scroll back up to see what the messages are. I also don't know where or what config file controls how this terminal functions (I.E. it's buffer size and what keys can scroll it). 

So can anyone help here? I am just looking for a reliable and simple way to view ALL of the boot-up messages so I can spot where the errors are. Currently these messages are not appearing in DMESG and the boot log file is completely empty. The systems starts up way to fast for me to catch the error messages. Is there an option somewhere that can enable logd to output all the messages of the consoles from the very start?

Thank you!

---

### Post by roadrun777 on 2008-09-07
I found a config file located at /etc/init.d

'/etc/init.d/logd'

-- with this in it --

```
# logd
#
# This service is started automatically by init so that the output from
# other services can be logged.

description	"service logging daemon"
author		"Scott James Remnant <scott@ubuntu.com>"

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

console output

exec /sbin/logd
respawn

```

Is there a command I can put in this file to force everything to a file instead of console? Or am I not understanding the function of the command?

Thank you for you assistance.

---

### Post by roadrun777 on 2008-09-07
Hmmmm, I will let you pet my hamster if you help me!
:lolflag:

---

### Post by HousieMousie2 on 2008-09-15
> **roadrun777 said:**
> Hmmmm, I will let you pet my hamster if you help me!
:lolflag:

I'll see your hamster and raise you my cat if anyone will help us... any takers?  They are really cute cats too, you can take your pick, or pet all of them if you like...

---

### Post by freefrags on 2008-10-02
Hey, 

im looking for the same thing here. i ran an update which caused some errors at boot time yet the messages dissappear so quick i cant read them. 

Does anybody know where i can view the logs of the boot process??

i read something about using dmesg however this doesnt show the messages shown during boot.

hope you can help

---

