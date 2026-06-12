---
title: "Wg111t drops connections .. please help"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by FireSoul on 2008-06-16
hi how are yu all i got wg111t and i am new to ubuntu

i used ndiswrapper and connect throught it .. but after some time it disconnects

please i need your help

---

### Post by FireSoul on 2008-06-17
Please Somebody Answer Me

---

### Post by bumanie on 2008-06-17
I unfortunately can't give you an answer, but I do sympathise with you. My partner's computer has the same adapter and it lasts 5 minutes, then nothing (she uses it for surfing in chinese). It's a wubi install (not sure if that makes any difference), but wireless and ubuntu are not great at present - something that is being worked on for intrepid ibex. Fortunately, I have my own computer downstairs which hooks to the wireless router - so I'm OK. If I find an answer, I'll let you know. Sorry, I can't help.

---

### Post by prshah on 2008-06-17
> **FireSoul said:**
> 
i used ndiswrapper and connect throught it .. but after some time it disconnects

Try using the following commands to turn off power management for your wireless:```

sudo iwconfig eth9 txpower fixed
sudo iwconfig eth9 power off
sudo iwconfig eth9 commit
```

The third command may give an error as "feature not supported" that can be ignored.

Either one of the first two commands should work and will take effect immediately, _until_ your next reboot. 

So give the commands, then surf for an hour or two to check if it is effective. If it is effective, you can add the commands to your "/etc/rc.local" to take effect on every reboot.

Note that in the rc.local file, the last line should not be disturbed (ie, "exit 0")

---

