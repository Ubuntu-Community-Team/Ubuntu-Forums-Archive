---
title: "Need help in accessing the Linux Server"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by blythescat on 2008-07-07
:(Hi folks
Due to some rather odd circumstances I have to manage a server running Linux. Having zero experience I was told I could access the server from my home computer using Putty.
Well it didn't work.
Any help would be appreciated.
Sorry if this is a daft question.

---

### Post by jamesrfla on 2008-07-07
Maybe they are hosting the ssh server on a diferent port.

---

### Post by hrod beraht on 2008-07-07
Which part didn't work?
When you start up PuTTY and type in the host name or IP address and then click the 'open' button, did that get a response from the server?

Bob

---

### Post by The Cog on 2008-07-07
How do you access it from work? Do you use putty there? If you don't use putty from work, it may be that an SSH service isn't running.

What version of Linux is it?

A linux server will often have an SSH server running which you can connect to with putty. I don't have any windows machines around to try at the moment, but I seem to remember that with putty you just specify the destination IP address and port 22 - it figures out for itself that 22 is SSH.

Assuming an SSH server is running on port 22, you still have to arrange for incoming connections to port 22 to make it through the firewall (maybe arranging to forward that port through a NAT gateway) and be passed on to the server. Have you arranged firewall access and NAT forwarding?

You say it didn't work. Does this mean that you do know the address and port number to try and connect to from the Internet?

To see if an ssh server is running, log onto the box and enter the command **netstat -lnt** . This lists the open listening TCP ports - see if port 22 is mentioned. If not then you need to install an SSH server. How to do this depends on the version of Linux. For Ubuntu and derivatives, the command **sudo aptitude install openssh-server** will do the trick.

---

### Post by blythescat on 2008-07-07
The repsonse I get is network error timed out.
I do not acces from work.
I have altered the firewall as suggested.
Ubuntu 8.04 LTS 'Hardy' x64 is the version of linux running.
There is nothing on port 22 and 
sudo aptitude install openssh-server returned a message ssh is not reconized.
Thanks for the ideas folks.
Still stuck:(

---

### Post by The Cog on 2008-07-07
If it's hardy, then 
```
sudo aptitude install openssh-server
```
should do the trick. Can you post the exact error message?

Or if you have a GUI working, System->Administration->Synaptic Package Manager and search for openssh-server and install it from there - the result should be the same as the command line.

---

### Post by blythescat on 2008-07-07
All I get is sudo is not reconized as an internal or external command.

---

### Post by Cypher on 2008-07-07
Do you have physical access to this Linux machine? If so, you will want to install the SSH server with the "sudo" command above and THEN try to access it using PuTTY from your Windows machine..

---

### Post by blythescat on 2008-07-07
I do not have physical access to the server....and if I did being in a wheelchair would make geting to it a bit difficult anyway!

---

### Post by hrod beraht on 2008-07-07
> **blythescat said:**
> The repsonse I get is network error timed out.

If that's the response when you start up PuTTY and type in the host name or IP address and then click the 'open' button, then either a) you have the wrong host name/IP address, or b) the server isn't running SSH.

I would contact whomever said you could access it with PuTTY and specifically verify that it is running SSH and that you have the right address.

> **blythescat said:**
> sudo aptitude install openssh-server returned a message ssh is not reconized.
Where exactly are you typing *sudo aptitude install...*? In PuTTY? Anything like that isn't going to work until you first are able to log into the server. (but of course none of it would be needed if you could actually log into the server).

Bob

---

### Post by Cypher on 2008-07-07
> **blythescat said:**
> I do not have physical access to the server....and if I did being in a wheelchair would make geting to it a bit difficult anyway!

It is likely that if there is a SSH server running on this machine, it's running on a non-standard port. So you might want to get more detailed information from whoever is asking you to administer this server.

---

### Post by The Cog on 2008-07-07
> **blythescat said:**
> All I get is sudo is not reconized as an internal or external command.

Sorry if it sounds rude, but are you sure it's running Ubuntu? I ask for two reasons:
1 - sudo is fundamental to Ubuntu - any Linux, I think
2 - that quote sounds like a windows response - when I try to use an unknown command (nonesuch) in Ubuntu, I get: > bash: nonesuch: command not found

P.S. 
Here's a thought: what exactly is the prompt you see at the command line?
For example, maybe something like one of these:
**cog@Dingly:~$**
or 
**C:\>**

---

### Post by blythescat on 2008-07-07
Thanks Bob for all your help.
I will confirm with hosting company what they have done or not done!
Best wishes
Ali

---

### Post by blythescat on 2008-07-07
On my own machine when I try to open the Putty after giving the Ip address it just displays a blank screen and then times out after a while.
Yes the server is definately Ubunto.
:(
when putty tries to connect I get a bright green square in the upper left of the screen. But I cannot write anything next to it or in it.

---

### Post by The Cog on 2008-07-09
Then I think you have a network problem. You should either get connection refused (if the server is not listening for SSH connections), or a connection accepted followed by some kind of prompt, or maybe some message saying your user/password is wrong. Just a timeout means either your connection request is not reaching the server, or the reply is not reaching you.

---

### Post by apostate on 2008-07-09
> **blythescat said:**
> All I get is sudo is not reconized as an internal or external command.

That is a Windows error message, where are you typing this in?

---

