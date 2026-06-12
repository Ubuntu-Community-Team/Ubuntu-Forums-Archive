---
title: "Any &quot;log utility&quot; I can use to keep track of what Ubuntu is doing?"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-28
I have a problem with my system freezing from time to time. So far, it has only done so while Firefox is running (other programs open at the same time) and then not consistently. I do get system errors that crop up long before the system freezes.

I think it would help if I knew more about how to explore the errors as they occur... I'm so new I don't know how to do that. Also, if there was some utility that would create, and store, a log of what Ubuntu is doing, such as module calls, I think that would provide more insight as well if such a thing exists. The log file would grow rapidly and would have to be deleted often but, it could prove useful, I think.

Any ideas out there?

---

### Post by tgalati4 on 2013-04-28
There's a few in /var/log.  You can increase the amount of logging with some switches.

tgalati4@Mint14-Extensa ~ $ apropos syslog
logger (1)           - a shell command interface to the syslog(3) system log module
rsyslog.conf (5)     - rsyslogd(8) configuration file
rsyslogd (8)         - reliable and extended syslogd
syslog (2)           - read and/or clear kernel message ring buffer; set console_loglevel
syslog (3)           - send messages to the system logger
vsyslog (3)          - send messages to the system logger

```
man rsyslog.conf
```

It's a bit heavy reading, but you can search the forums for* rsyslog* for some ideas.

```
dmesg | tail -100
```

Post any error messages that you don't understand.

---

### Post by Bashing-om on 2013-04-28
alhefner; Hi !

'buntu already incorporates great logabilities. The easiest way to peruse the log files is from the log file viewer utility (dash; search term log file). Look through dmesg and syslog and kern.log for starters.
```
ls -la /var/log
``` yields a list of many of the system logs.

The sad thing might be that when your system does freeze up, the system can no longer log any events. This does make it difficult to isolate a fault ![INDENT=3]just try'n to help

[/INDENT]

---

### Post by alhefner on 2013-04-29
All I can says WOW! There's a lot of info in there! Think I found some things to look at, when I find out how... new thread on the way!

---

### Post by Bashing-om on 2013-04-29
alhefner; Hey,

So long as the subject remains logging, there is no need to start another thread.

I find I prefer the "log file viewer" for viewing files. Not a lot of help in the related help files, but enough to point ya in the right direction.
It took me a while to figure out how to load other log files rather then just the defaults.( difference between versions 10.04 and 12.04).

When one gets real bored, the logs can make interesting reading -> prompts for curiosity's sake.
[INDENT]
we are here to help you over the hurdles

[/INDENT]

---

### Post by alhefner on 2013-04-29
Yep, that log file viewer works pretty well! I was under the mistaken impression that the logs were purged at each new boot-up... boy, was I wrong! I am pretty well able to go back through things and find where my system froze each time and look at the logs about that.

The new thread is specific to the freeze issue and it seems that it's an ongoing bug and the team is on it.

---

### Post by Bashing-om on 2013-04-29
alhefner;
Roger that, You do well.

I will catch up with you on a flip side.[INDENT]
keep on keep'n on

[/INDENT]

---

