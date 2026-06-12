---
title: "how do I set up an ssh server?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-14
it shows in synaptics that openssh-server is already installed...I dont understand. running 8.10

---

### Post by ohzopants on 2008-11-14
It's installed, but not necessarily running

In order to start it run:
```

sudo /etc/init.d/sshd start

```

Then you should be able to connect to that computer using SSH.

---

### Post by Titan8990 on 2008-11-14
Sounds like you are already running it.

To verify that the ssh-server daemon is running:


ps aux | grep sshd

---

### Post by rampageoberon on 2008-11-14
okay if openssh server is installed do the following to check if it is running.

```
sudo aptitude install nmap
nmap -A localhost -p 22
```

If you see the OpenSSH running all is well, you can connect to it using putty or ssh in terminal.

To modify the configuration you need to edit "/etc/ssh/sshd_config". Hope thats what you're after.

---

### Post by drs305 on 2008-11-14
Here is a link to basic SSH from ubuntu documentation:
[SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

And Advanced:
[AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")

---

### Post by B34ST1Y on 2008-11-14
I have run BOTH commands, and this is the respective output: 
```
syn3rgy@zer0cool:~$ ps aux | grep sshd
root     18540  0.0  0.0   5392  1036 ?        Ss   15:10   0:00 /usr/sbin/sshd
syn3rgy  18737  0.0  0.0   3236   804 pts/0    S+   15:16   0:00 grep sshd
syn3rgy@zer0cool:~$ sudo /etc/init.d/sshd start
sudo: /etc/init.d/sshd: command not found
syn3rgy@zer0cool:~$ 

```


so that means its running...but I can't configure it?? o.O 

when I try to ssh to my ip, it immediately says the connection is refused

---

### Post by B34ST1Y on 2008-11-14
nvm. I put two and two together...now it works. Thank you! *solved* and *thanks all around*

---

### Post by rampageoberon on 2008-11-14
Ok so the daemon isrunning. Are you trying external ip or network ip?

Does "ssh localhost" work or does that fail too. If it fails it'd be useful to see the "/etc/ssh/sshd_config" file.

PS: the command to start the server is

```
/etc/init.d/ssh start
```

---

### Post by ohzopants on 2008-11-18
Thanks for the correction.  I guess I've become something of a tab-completion addict and can't remember actual command names (particularly from a windows machine).

---

