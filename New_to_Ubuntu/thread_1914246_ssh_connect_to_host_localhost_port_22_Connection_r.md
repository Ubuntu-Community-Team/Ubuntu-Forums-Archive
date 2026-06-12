---
title: "ssh: connect to host localhost port 22: Connection refused"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by bonda_makers on 2012-01-24
Hello!

I've been battling with this issue for 2 days and I've not been very successful, just yet. I'm simply unable to ssh to even my localhost.

Here's what I've been trying out.
1. Firewall issues: 1. Turned ff the firewall via the UI firewall manager as well as the CLI (IPTABLES commands here [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html))

2. checked, re-checked andupdated my openssh-server.
o/p: apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

3. Eve tried changing the port no from 22 . still, unable to connect.

Problem:

1. ~# /etc/init.d/sshd restart (OR start)
bash: /etc/init.d/sshd: No such file or directory 
However, there's a file called ssh in the same path

So, I tried starting it(SSH). Then did a pgrep SSH(gives the no) but pgrep SSHD returns nothing.
 
My predictions: 1. SSH is not even installed? If so, what should I do now?

PS- I'm a complete newbie to Ubuntu and I'm simply loving t already. I've learned SO much :)
Thanks in advance!

---

### Post by carl4926 on 2012-01-24
How are you trying to connect?
Using a terminal?
or Nautilus > Connect to server?
or other?

---

### Post by papibe on 2012-01-24
Could you post the result of these commands?
```
sudo service ssh restart

ps aux | grep -i ssh
```
Regards.

---

### Post by bonda_makers on 2012-01-24
I'm using the terminal to connect ie ssh localhost

Also,
#sudo service ssh restart 
restart: Unknown instance: 

And
ps aux | grep -i ssh
root      1577  0.0  0.0   3348   200 ?        Ss   Jan21   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
hduser   13685  0.0  0.0  10932  3672 pts/8    T    10:20   0:00 vim /etc/init.d/sshd
root     14154  0.0  0.0   4012   780 pts/11   S+   10:56   0:00 grep --color=auto -i ssh

In case this helps I was trying out commands on the CLI and i'd done this previously:
$ sudo addgroup hadoop $ sudo adduser --ingroup hadoop hduser

---

### Post by papibe on 2012-01-24
Is looks like the service is down (restart cannot be performed).

Try starting it:
```
sudo service ssh start
```
Then check if it is running again:
```
ps aux | grep -i ssh
```
You should see a process named '/usr/sbin/sshd' running. If so, try to connect again.

Hope it helps.
Regards.

---

### Post by bonda_makers on 2012-01-24
Thanks for the help. However, I still seem to face the same issue:
1. tried starting ssh. worked fine
2. ps aux|grep -i ssh
root      1577  0.0  0.0   3348   200 ?        Ss   Jan21   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
hduser   13685  0.0  0.0  10932  3672 pts/8    T    10:20   0:00 vim /etc/init.d/sshd
root     14486  0.0  0.0   4012   780 pts/11   S+   11:14   0:00 grep --color=auto -i ssh

Help, please?

---

### Post by Nethos on 2012-03-01
I was having a similar problem on my work computer, I found that removing and reinstalling OpenSSH fixed it for me. Not sure if it will work for you, but it's worth a shot.

remove OpenSSH: ```
sudo apt-get remove openssh-client openssh-server
```install OpenSSH again: ```
sudo apt-get install openssh-client openssh-server
```Hope this helps!

---

### Post by xxclear on 2012-04-23
> **Nethos said:**
> I was having a similar problem on my work computer, I found that removing and reinstalling OpenSSH fixed it for me. Not sure if it will work for you, but it's worth a shot.

remove OpenSSH: ```
sudo apt-get remove openssh-client openssh-server
```install OpenSSH again: ```
sudo apt-get install openssh-client openssh-server
```Hope this helps!

This fixed it for me! who would have guessed it was that simple eh? Thanks man!

---

### Post by EricStJean on 2012-05-25
> **xxclear said:**
> This fixed it for me! who would have guessed it was that simple eh? Thanks man!

Thanks for me also...:)

---

### Post by steveBloodaxe on 2012-10-05
> This fixed it for me! who would have guessed it was that simple eh? Thanks man! And for me as well, Nethos Thank you very much !!

---

### Post by pterosky on 2013-02-06
I am testing out Ubuntu 12.04.1 on a VirtualBox, this is how I managed to SSH into it after installing:

[LIST]
[*]In the client (virtual) Ubuntu, install OpenSSH with ```
sudo apt-get install openssh-client openssh-server
```
[*]Follow the instructions on this page: [http://christophermaier.name/blog/2010/09/01/host-only-networking-with-virtualbox](http://christophermaier.name/blog/2010/09/01/host-only-networking-with-virtualbox)
[*] That's it :-)
[/LIST]

---

### Post by seriouscat on 2013-03-03
Uninstalling and reinstalling worked for me :D 
Thanks
-Matt

---

