---
title: "such a thing as linux API?"
date: 2010-04-17
forum: Programming Talk
---

### Post by cgb223 on 2010-04-17
hey I'm looking for an API or something like it that will let me get info about the system my C++ program is running on like say my when wireless strength is weakened to 5% then disconnect from that and connect to next one, or if hard drive is almost full, then dump these files, and so on and so forth. I figure there is probably some sort of linux API for these sorts of things. if there is how do i install it, or is it already installed? and also any good places or books or docs to learn how to use it?

---

### Post by slavik on 2010-04-18
for wifi, look at iwconfig
for disk space, look at df

you can get the source code for both and see how they do it.

---

### Post by Portmanteaufu on 2010-04-20
> **slavik said:**
> for wifi, look at iwconfig
for disk space, look at df

you can get the source code for both and see how they do it.

Combine these tools with [cron]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html") and you can write a script that will check disk usage / wifi status every so often and react accordingly. ('du' is another disk usage utility that you could look at.)

Do you know any scripting languages (e.g. Perl/Python)? Are you familiar with Bash at all? (Or sed, awk, or similar?) If not, these would be the best place to start -- you'll find that tasks like you're describing are far, far easier to accomplish in a scripting language than in a lower-level language like C/C++. While C++ gives you the awesome power to micro-manage memory usage and write blazing-fast code, scripting languages often allow you to perform high-level ideas ("check the wifi signal", "make an array using this file's lines" or "see who's logged into this machine") in one or two lines of code.

---

### Post by slavik on 2010-04-20
don't use cron. use something meant for the job (nagios, for instance).

---

### Post by phrostbyte on 2010-04-20
It's called the Linux Wireless Extensions API, but that seems to have been (recently?) depreciated.

You can read more over here on the new way to query this information:

[http://wireless.kernel.org/en/developers/Documentation/nl80211](http://wireless.kernel.org/en/developers/Documentation/nl80211)


Or just get the source code for iwconfig

apt-get source iw

It uses this API.

---

### Post by Portmanteaufu on 2010-04-21
> **slavik said:**
> don't use cron. use something meant for the job (nagios, for instance).

I'm not sure I understand you when you say that "cron isn't meant for the job." I'm not familiar with nagios, but cron would do exactly what I said it would. You can schedule a program to to check on the status of something every X seconds and respond accordingly.

Perhaps you could clarify?

---

### Post by StephenF on 2010-04-21
DBUS deserves a mention since it provides in supported applications the power to automate.

---

### Post by slavik on 2010-04-22
> **Portmanteaufu said:**
> I'm not sure I understand you when you say that "cron isn't meant for the job." I'm not familiar with nagios, but cron would do exactly what I said it would. You can schedule a program to to check on the status of something every X seconds and respond accordingly.

Perhaps you could clarify?
cron is for scheduling. yes.
nagios is a commercial grade open source monitoring utility/framework.

if you are concerned with only 1 system, by all means, go ahead with cron. if you might expand to 10, 20, 50 ... then good luck keeping all cron jobs updated properly when you want to add features.

---

