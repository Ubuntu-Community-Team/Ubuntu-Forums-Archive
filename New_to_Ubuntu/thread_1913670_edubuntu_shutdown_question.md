---
title: "edubuntu shutdown question"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by cabz on 2012-01-22
please pardon the newb  here:D 
I have a question about shotting down , when I power off my laptop with edubuntu 11.10 on it I notice in between flashes of the edubuntu spalsh screen some text in the back  ground . how can I slow the shut down up and see whats back there? I ask because I hit pause/break key and notice some sort of error but, pasue only last so long and I can't read all the text.
sorry if this seems odd , but i am used to reading the post screens in windows to look for issues and or errors.

---

### Post by ubudog on 2012-01-23
Hi there, welcome to the forum!  

If everything is working properly, the error is probably nothing to worry about.  However, if you want to view the (kernel) log, do this:
```
sudo cat /var/log/kern.log
```

I *think* that would give you the information you're looking for.

Best, 
ubudog

---

### Post by cabz on 2012-01-24
thank I'll give it a try.:D

---

### Post by cabz on 2012-01-24
OK I tried that command and it seems to give me the start up list , it list everything that starts up and loads Whew that was a long list. it was kind of like a windows start up post in DOS. what i need is the opposite. I want  is to see what's shutting down behind the white edubuntu window .
sorry of this is a PIA request , just curiousity on my part

---

### Post by ubudog on 2012-01-24
Hmm, according to [this]("http://askubuntu.com/questions/68563/how-can-i-log-shutdown-console-text"), the shutdown (and boot) log is located at /var/log/syslog.  So:
```
sudo cat /var/log/syslog
```

I hope this helps - if not, someone out there probably can.
- ubudog

---

