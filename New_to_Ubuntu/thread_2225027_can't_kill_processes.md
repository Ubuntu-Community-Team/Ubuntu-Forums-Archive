---
title: "can't kill processes?"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by beelzebufo on 2014-05-19
this makes no sense, I can't kill any processes with the usual commands "kill (PID)" and "killall (Process name)"  Any help would be greatly appreciated.  I use top, find the PID and use kill or killall and nothing happens.  I use these commands all the time, I have no idea why they decided to stop working today.

thanks in advance

Beelzebufo

---

### Post by matt_symes on 2014-05-19
Hi

Are they yours to kill ? Do you own them ?

Can you post the output of

ps -aux | grep <Process_name>

before and after the kill command please so we can see.

Kind regards

---

