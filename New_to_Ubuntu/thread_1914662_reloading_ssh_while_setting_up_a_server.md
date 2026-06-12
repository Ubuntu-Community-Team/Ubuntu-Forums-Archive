---
title: "reloading ssh while setting up a server"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by brossen on 2012-01-24
Hi, 
I'm trying to set up an ubuntu server and am definitely an absolute beginner. I've learned a bit about using the command line and know a little bit about navigating linux, but I've never set up a server before. I'm setting up a LAMP stack on the rackspace cloud and have been following their setup instructions so far (found here: [http://www.rackspace.com/knowledge_center/index.php/Ubuntu_Hardy_-_Setup,]("http://www.rackspace.com/knowledge_center/index.php/Ubuntu_Hardy_-_Setup") but have run into an error that I don't know how to solve. 

I have created a firewall and adjusted some rules in iptables.  I want to reload the ssh configuration to use the new ports and settings. 

I tried running: 

```
/etc/init.d/ssh reload 
```

but was told to use the "service(8)" command. 

So I tried running: 

```
service ssh reload 
```

but it tells me "reload: unknown instance:" 

any help as to what I should do would be much appreciated!

---

### Post by SuaSwe on 2012-01-24
Evening!

I think you need:

```

/etc/init.d/sshd restart

```

(Note, sshd rather than ssh, standing for ssh daemon)

---

### Post by brossen on 2012-01-24
I tried running that, but it gave me 

```
-bash: /etc/init.d/sshd No such file or directory
```

---

### Post by SuaSwe on 2012-01-24
Ah, my bad. :D Puzzled that neither of those work though - my own server which has SSH installed gives a positive response of "Reloading OpenBSD Secure Shell server's configuration sshd            [ OK ]" when sent '/etc/init.d/ssh reload'.

Silly question but do you know for a fact that SSH is correctly installed? What does 'which ssh' give you?

Oh yeah, and exactly what does the "use service command instead" error say?

---

### Post by mwd5650 on 2012-01-24
On my Ubuntu server this is the command to restart ssh-server

sudo service ssh restart


not service sshd restart

I'm running 10.04 LTS but I don't think it has changed.

---

### Post by brossen on 2012-01-24
ssh should be installed -- i went through the whole process first and it seemed to work. 

which ssh returns: 

```
/usr/bin/ssh
```

---

### Post by brossen on 2012-01-24
Also -- the exact error is: 

```
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g., service ssh reload.

Since the script you are attempting to invoke has been connected to an Upstart job, you may also use the reload(8) utility, e.g., reload ssh
reload: Unknown instance. 
```

---

### Post by azmyth on 2012-01-24
> **mwd5650 said:**
> On my Ubuntu server this is the command to restart ssh-server

**sudo service ssh restart**


not service sshd restart

I'm running 10.04 LTS but I don't think it has changed.

See in bold

---

### Post by brossen on 2012-01-24
Sorry, I should have written that I attempted using "sudo service ssh restart" and that similarly returned "Unknown instance".

---

### Post by brossen on 2012-01-25
Any possible explanation why ```
sudo service ssh restart
``` isn't working here? All signs seem to suggest to me that this should fix the issue, but it isn't working!

---

### Post by Azdour on 2012-01-25
Hi,

Just a thought. Maybe ssh cannot start because there is an error in your ssh conf file? You could check your logs to see if there are any messages in your auth.log.

---

### Post by azmyth on 2012-01-25
You must have an issue with ssh (see post above)

sudo service ssh start

will give you an error if there's a problem.

---

### Post by brossen on 2012-01-25
Agree it seems like something must be wrong with SSH, but ```
sudo service ssh start
``` appears to work fine and returns: 

```
ssh start/running, process 1548
```

---

### Post by mwd5650 on 2012-01-25
what happens if you try 
 
```
 
sudo service ssh stop
sudo service ssh start

```
 
I'd be curious if the ssh stop gives you an error.
 
Matt

---

### Post by brossen on 2012-01-25
sudo service ssh stop returned " stop: unknown instance"

---

### Post by mwd5650 on 2012-01-25
What does 
 
```
sudo apt-get install openssh-server 
``` 
 
return?

---

### Post by brossen on 2012-01-25
```
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.
```

Question -- I'm running all of these on ubuntu -- not on my local terminal. I set up the private/public keygens on my local computer already, but do I need to be running anything locally to get ssh to connect?

---

### Post by mwd5650 on 2012-01-25
All of what we are telling you should be done on the Ubuntu server that you are trying to setup openssh-server.


So on the same system you ran the sudo apt-get install openssh-server command you as saying if you run sudo service ssh restart you get unrecognized service?

Matt

---

### Post by brossen on 2012-01-25
That's what I figured - just wanted to make sure. 

I get unkown instance, not unknown service, when i try to run the ssh restart command. 

I did make some changes to the SSH config to make it more secure -- could any of these be causing the issue? 

```
Port 30000                           <--- change to a port of your choosing
Protocol 2
PermitRootLogin no
PasswordAuthentication no
UseDNS no
AllowUsers demo
```

---

### Post by mwd5650 on 2012-01-25
what happens if you ```
kill -9 1548
``` and then try ```
service ssh start
```

---

### Post by brossen on 2012-01-25
```
bash: kill: (1548) no such process
```

:(

---

### Post by mwd5650 on 2012-01-25
If sudo service start gives you ```
ssh start/running, process 1548
``` 

and you don't have a process 1548, that doesn't make sense.

do

```
ps aux | grep sshd
```



Do you get a line something like this?

```
root       938  0.0  0.8   5552  2128 ?        Ss   19:28   0:00 /usr/sbin/sshd -D
```

Matt

---

### Post by brossen on 2012-01-25
It gives me: 

```
root     17396  0.0  0.2   6296   592 hvc0     S+   02:02   0:00 grep --color=auto sshd
```

"sshd" is printed in red, if that matters

---

### Post by mwd5650 on 2012-01-25
If that is the only line it gives you back then ssh server is not running.

You are running this command on the actual Ubuntu Server right?

Matt

---

### Post by brossen on 2012-01-25
Yes, I'm running all of these commands on the Ubuntu server, not on my local terminal.

---

### Post by azmyth on 2012-01-26
Your ssh must be starting then something is causing it to stop

Run ssh in debug mode

sudo service ssh stop
sudo /usr/sbin/sshd -d

Any errors from the second command?

---

