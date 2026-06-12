---
title: "Kill process at startup"
date: 2014-07-12
forum: New to Ubuntu
---

### Post by 3dmatrix on 2014-07-12
I am starting this thread as I did not receive any reply to my following post since long time.

[http://ubuntuforums.org/showthread.php?t=2209909&page=2&p=12984948#post12984948](http://ubuntuforums.org/showthread.php?t=2209909&page=2&p=12984948#post12984948)

I am modifying my question as :

[LIST]
[*]If at startup, I need to kill any process (which is running as root) when what should I write in a script and how to execute it at start up ?

[*]I would also like to know how is **kill process** different from **end process**.
[/LIST]

---

### Post by ajgreeny on 2014-07-12
Can you give an example of the process(es) that you want to stop, or is this just a general question about how it is possible to do such things?

As an example, I have openssh-server installed on my main box, but for security as I seldom need it running, I have it set to run only when I want it to with command ```
sudo service ssh start
```  There are two ways in which I can achieve this; either stop it running in the first place by commenting out the line, as follows
**# start on filesystem or runlevel [2345]**
in /etc/init/ssh.conf which will stop it before it starts, or
add the line
**service ssh stop**
to /etc/rc.local which will stop it after it starts.

Better to stop it first in my opinion, and maybe the same will apply to you, but it will help to know what we are dealing with in detail, though if this is still about your running Quake, I can not really help, though my example may give you some possible clues.

---

### Post by 3dmatrix on 2014-07-12
> **ajgreeny said:**
> Can you give an example of the process(es) that you want to stop, or is this just a general question about how it is possible to do such things?

As an example, I have openssh-server installed on my main box, but for security as I seldom need it running, I have it set to run only when I want it to with command ```
sudo service ssh start
```  There are two ways in which I can achieve this; either stop it running in the first place by commenting out the line, as follows
**# start on filesystem or runlevel [2345]**
in /etc/init/ssh.conf which will stop it before it starts, or
add the line
**service ssh stop**
to /etc/rc.local which will stop it after it starts.

Better to stop it first in my opinion, and maybe the same will apply to you, but it will help to know what we are dealing with in detail, though if this is still about your running Quake, I can not really help, though my example may give you some possible clues.

Yes it is about my Quake server which keeps running in the background.
What command should be written in the terminal to kill any process (say the quake process) ?
If the code has sudo then how can we make a script file do that work ?

---

### Post by papibe on 2014-07-12
Hi 3dmatrix.

I can think of two ways:
[LIST]
[*]Using the /etc/rc.local, as ajgreeny suggested, or
[*]Using a @reboot entry in root's crontab.
[/LIST]
As for the proper code it would depend on how the quake service/daemon is launched.

For instance, if it has upstart scripts:
```
service quake stop
```
if it is just a process sent into the background:
```
killall quake
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by sandyd on 2014-07-12
nvm

---

### Post by 3dmatrix on 2014-07-13
sudo killall -v quake-engine-server
[sudo] password for user: 
Killed quake-engine-server(1273) with signal 15

The above code works in terminal but how can I make a script file and execute it. 
If possible without it asking for a password.

---

### Post by ajgreeny on 2014-07-13
Add the line
```
killall -v quake-engine-server
```
to the /etc/rc.local file just above the **exit 0** line (as administrator) by using ```
sudo nano /etc/rc.local
``` You will not need the sudo prefix as rc.local is already run as root at boot.
I am not sure if the -v option in the **killall** command is needed, as that will show verbose output in terminal, and as the system is not running it in terminal it is probably superfluous.

---

