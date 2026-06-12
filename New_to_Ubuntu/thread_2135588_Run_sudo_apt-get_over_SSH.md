---
title: "Run sudo apt-get over SSH"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by bfedyk on 2013-04-14
Hi, 

I am new to Ubuntu (a little knowledge of Linux as a whole, not much to speak of), and this is my first post to this Forum so I apologise now upfront if my question has already been answered elsewhere.  Also if I am asking the wrong question in the wrong section, please bear with me. 

I have set up two new servers running 12.04 LTS, for a project for my customer. The servers sit on a private VLAN, they have no HTTP proxy set. To request access to HTTP proxy would take a few days (form filling, requirements request, sign-off) and may not get accepted. 

I have remote access to the new server through client VPN connection (CheckPoint VPN) then use PuTTY to ssh to the servers. Or when working on site I am able to simply ssh to the servers. 

The servers are installed with the base 12.04 LTS, the application that will run on the servers requires certain pre-requisite packages from the repository. It seems that if I cannot get HTTP proxy enabled I will have to run sudo apt-get but route this over mky ssh tunnel? This will be a bit slow I realise. 

So to summarise I want to connect ssh to the Ubuntu servers and be able to run 'sudo apt-get -f install' such that the command uses the ssh tunnel to connect to the repository, which means accessing the repository over the internet from my laptop (my laptop is a Windows 7 platform). 

I have read up on ssh, apt-get etc, and not sure if any of the solutions match my requirements exactly.

I'm sure this can be done, but am not certain exatly how. 

Any help to a newbie much appreciated! 

Thanks in advance.

Bohdan

---

### Post by zrdc28 on 2013-04-14
It is very easy to do if you have linux on your laptop, even with a live cd, I do it all the time.  just ssh hostname@192.178.1,100 or what ever will get you there.

---

### Post by wickedpuppy on 2013-04-14
Have you tried it? You have access to the server in question right? 

Thats the main question. Pls try. If it doesn't work then pls ask here with details so we can work on it. If not it would be as if you want to know if it is ok to go over and say hello to a girl sitting opposite you in a bar. Pls try. Just type the command.

@zrdc28 : I think you meant ssh username@IP/hostname , no?

---

### Post by steeldriver on 2013-04-14
I've never had to do it, but this sounds like what you would need to do: [HOWTO: Reverse proxy through ssh tunnel]("http://ubuntuforums.org/showthread.php?t=1765935")

> Situation:

[LIST]
[*]You got access to a client's computer behind a firewall through ssh. 
[*]The client's computer hasn't got internet access. It's in an intranet. 
[*]You need to install software, so you must give that box internet access for some time. 
[/LIST]


---

### Post by bfedyk on 2013-04-14
@zrdc28: No, I do not have a Linux laptop, not even a live CD. But thanks, this is something I could try.

@wickedpuppy: sorry, I don't understand the reply about trying the command. If the remote Ubuntu servers have no means of accessing the internet how would the apt-get command work? 

@steeldriver: Thanks, sounds like this may be what I need to set up.

---

### Post by wickedpuppy on 2013-04-14
Ah I see .. I must have misread the question then. My apologies.

---

### Post by bfedyk on 2013-05-01
Hi, apologies this is late update .... newbie to forums etc particularly this one. Forgot to update. 

In the end could not get reverse SSH to work, I guess something in the customer's setup. So had to create a local repository copy on my laptop - downloaded all required repository files, the copied to target Ubuntu servers. Used the local repository therefore. 

Thanks for all the comments though, when I get some spare time I will try again to get reverse SSH to work.

---

