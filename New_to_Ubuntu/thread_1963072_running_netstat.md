---
title: "running netstat"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by sniper8752 on 2012-04-21
I am trying to learn to use the terminal, and entered # netstat -pt.  shouldn't something be listed there?  i was looking at these commands: [http://www.thegeekstuff.com/2010/03/netstat-command-examples/](http://www.thegeekstuff.com/2010/03/netstat-command-examples/).  it just asks me for my next prompt.  shouldn't it show which programs are running on which ports?

---

### Post by raja.genupula on 2012-04-21
but the command  ```
netstat -pt
``` gave us the outcome which programs are using internet now . 

to find port numbers and like that look at 9 & 10 points in the link you have provided .

---

### Post by d3v1150m471c on 2012-04-21
preference:
```

sudo bash
apt-get install sockstat
sockstat
exit

```

---

### Post by Old_Grey_Wolf on 2012-04-22
> **sniper8752 said:**
> I am trying to learn to use the terminal, and entered # netstat -pt.  shouldn't something be listed there? 

The # is not part of the command. It is the prompt showing that the person posting the instructions was running as root. The equivalent command for Ubuntu is ```
sudo netstat -pt
```
The prompt in Ubuntu looks like "[username]@[computername]:~$", so, on Ubuntu the command line if cut from the terminal and pasted into instructions would look something like owner@owner-laptop:~$ sudo netstat -pt

---

