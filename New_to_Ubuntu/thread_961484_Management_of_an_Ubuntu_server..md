---
title: "Management of an Ubuntu server."
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Tsu on 2008-10-28
I would like to hear what commands people generally use in order to manage an ubuntu server.

An example would be my current situation.

1>	I have recently moved from Freebsd over to Ubuntu. I am trying to see a generalized resource usage by the systems processes. I have run the “Top” command how ever find that not all the process are viewable on my screen. (I connect to the server via SSH and have increased the number of lines displayed on my system.)

How would I go about displaying all the processes on my screen?

2>	I would then like then like to locate a service and shut it down. I understand that the “kill all” command followed by the services name is sufficient or “kill” then the PID number. What I am actually after the knowledge of being able to understand how each service and process passes information on ubuntu. So I know where the scripts or programs are. How they use other services and call other services. As well as how they interface with the base system that is Ubuntu.
Thank for your assistance.

I have some experience using the "ps" command. Was hoping someone could elaborate on how this command works as reading the man is hurting my head.

---

### Post by Sarmacid on 2008-10-28
> **Tsu said:**
> I would like to hear what commands people 
1>	I have recently moved from Freebsd over to Ubuntu. I am trying to see a generalized resource usage by the systems processes. I have run the “Top” command how ever find that not all the process are viewable on my screen. (I connect to the server via SSH and have increased the number of lines displayed on my system.)

How would I go about displaying all the processes on my screen?

```
ps ax
```
> **Tsu said:**
> 
2>	I would then like then like to locate a service and shut it down. I understand that the “kill all” command followed by the services name is sufficient or “kill” then the PID number. What I am actually after the knowledge of being able to understand how each service and process passes information on ubuntu. So I know where the scripts or programs are. How they use other services and call other services. As well as how they interface with the base system that is Ubuntu.
Thank for your assistance.

To find out if a process is running```
pgrep -l processname
```
And the scripts for the services are located at /etc/init.d/

---

### Post by cariboo on 2008-10-28
Most of the services are in /etc/init.d. The way I stop a service is to enter:

```
sudo /etc/init.d/apache2 stop
```

The above command will stop apache2 to start a service:

```
sudo /etc/init.d/apache2 start
```

to restart a service because you made a configuration change:

```
sudo /etc/init.d/networking restart
```

This will shutdown networking and restart the service.

I just started playing with Dragonfly BSD and aside from trying to get my head around the packaging sytem, I've found that a lot of the commands work the same way.

As you have noticed I use sudo for all commands. Ubuntu has the root password is locked, for reasons that are to long to go into here. If you want to find out more go here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Jim

---

### Post by Tsu on 2008-11-04
Thanks for all your help guys

---

