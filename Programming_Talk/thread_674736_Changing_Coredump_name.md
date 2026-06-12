---
title: "Changing Coredump name"
date: 2008-01-22
forum: Programming Talk
---

### Post by hqduong on 2008-01-22
Can someone please tell me how do I change it so Ubuntu dumps a core file with its name, PID, and a timestamp? 

I looked into the apport python script, but this is a language I haven't really picked up yet.

---

### Post by mshamma on 2009-09-18
Any luck solving the problem?

---

### Post by MadCow108 on 2009-09-18
to just set the pid appending you can change
/proc/sys/kernel/core_uses_pid
to 1

more complicated patterns are saved in:
/proc/sys/kernel/core_pattern

pattern:
%p:       pid
%<NUL>:   '%' is dropped
%%:       output one '%'
%u:       uid
%g:       gid
%s:       signal number
%t:       UNIX time of dump
%h:       hostname
%e:       executable filename
%<OTHER>: both are dropped

[http://www.linuxhowtos.org/Tips%20and%20Tricks/coredump.htm](http://www.linuxhowtos.org/Tips%20and%20Tricks/coredump.htm)

---

