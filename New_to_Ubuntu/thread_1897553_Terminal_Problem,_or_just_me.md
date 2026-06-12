---
title: "Terminal Problem, or just me?"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by JoanJohnson on 2011-12-19
I've been trying to learn my way around the Terminal command prompt, and since I just downloaded Ubuntu and switched permanently from Windows a few days ago, I'm pretty much back at Newb level again. 
So, I'm sorry if this is a stupid question or something, but I genuinely want to know...
Every time I try to finger or telnet something, it doesn't...go through. The connection just eventually times out. I mean, every time. I'm wondering if I need a shell account, or if the problem is me and the way I'm doing it. 
I appreciate any help I can get.

---

### Post by kanikilu on 2011-12-19
Could it be that the host is not listening for telnet connections? Do a quick scan with nmap to see if port 21 is even open...

//Edit - oops, I meant 23...21 is FTP.

---

### Post by CharlesA on 2011-12-19
What are you trying to telnet to? The telnet daemon isn't installed by default.

---

### Post by Lars Noodén on 2011-12-19
> **JoanJohnson said:**
> Every time I try to finger or telnet something, it doesn't...go through. The connection just eventually times out. 


I think the tutorials might be a bit dated.  finger and telnet largely went away.  

Telnet was replaced by SSH, so you can connect using SSH instead.  That is secure, telnet is insecure as it transmits the entire session including the username and password as unencrypted text.  Ubuntu comes with the [OpenSSH client](http://en.wikibooks.org/wiki/OpenSSH/Overview) by default.

---

### Post by JoanJohnson on 2011-12-19
I already downloaded the telnet daemon, and I have NO idea what a nmap is. 
:/ 
Someone told me to telnet llama.swcp.com 79 and then give a specific command-they said I would learn something from it but since I can't telnet it, I'm a little stuck.

Edit// I tried SSH...it didn't work for some reason. It says the command isn't valid.

---

### Post by Lars Noodén on 2011-12-19
> **JoanJohnson said:**
> I already downloaded the telnet daemon, and I have NO idea what a nmap is. 

[nmap](http://nmap.org/) is a network scanner which can be used find open ports.

---

### Post by CharlesA on 2011-12-19
> **JoanJohnson said:**
> I already downloaded the telnet daemon, and I have NO idea what a nmap is. 
:/ 
Someone told me to telnet llama.swcp.com 79 and then give a specific command-they said I would learn something from it but since I can't telnet it, I'm a little stuck.

Edit// I tried SSH...it didn't work for some reason. It says the command isn't valid.

Port 79 is for the finger protocol, which isn't used much if at all any more.

The only reference I found to llama.swcp.com was in two articles by the same author and posted in 1996.

Who told you to run those commands? I wouldn't trust them tbh.

---

### Post by Lars Noodén on 2011-12-19
> **JoanJohnson said:**
> Edit// I tried SSH...it didn't work for some reason. It says the command isn't valid.

The protocol and the application are "SSH" in uppercase but the actual program is "[ssh](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ssh.1.html)" in lowercase.

---

### Post by JoanJohnson on 2011-12-19
Wow. That's an eye opener. 
Thanks, everyone. This is a steep learning curve and I'm still learning. 
Solution: Abandon telnet and finger, use SSH instead. (and the command is ssh in lowercase) 
:3 Got it.

---

