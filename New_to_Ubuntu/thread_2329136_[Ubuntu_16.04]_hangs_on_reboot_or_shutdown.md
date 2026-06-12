---
title: "[Ubuntu 16.04] hangs on reboot or shutdown"
date: 2016-06-28
forum: New to Ubuntu
---

### Post by isidoro4 on 2016-06-28
Hi,
Sometimes Ubuntu hangs on reboot or shutdown. The screen shows a blinking cursor and the charge bar of ubuntu...
What log file can I check?
Can you help me?

---

### Post by grahammechanical on 2016-06-28
Does it eventually shut down/reboot? Or do you give up waiting? I have found that give the OS time and it will complete the task. Something is blocking the shutdown and the OS is waiting for a response for the shutting down of some service and it is not getting it. So, the OS waits and then over-rides the process and finishes shutting down.

Sometimes doing a hard power off or reset will disturb the shut down profile. And a few normal shut downs will set a clean profile and the problems goes away.

You might want to try shutting down from the command line and watching the messages. Ctrl+Alt+F1 to get the command line. Log in  and to shut down

```
sudo shutdown -h now
```

to restart

```
sudo shutdown -r now
```

Regards.

---

