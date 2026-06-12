---
title: "when i shut down its restarting"
date: 2021-09-01
forum: New to Ubuntu
---

### Post by mithileshgrandhi on 2021-09-01
Hi there,
I am using Ubuntu 20.04.2 LTS. I have recently installed this. Ever since i have installed, i am unable to poweroff. Every time i click on poweroff, it simply restarts.

Would be helpful if anyone can solve this issue.

Thanks in advance.

---

### Post by grahammechanical on 2021-09-01
As a test open the terminal and run either of these commands

```
sudo shutdown -h now
sudo shutdown -P now
sudo shutdown --poweroff now
```

It will not fix this problem but we will find out if it is possible to power-off this machine. I am guessing that when we select PowerOff/Log Out, and then Power Off two more times a script is run that includes one of those commands.

Regards

---

