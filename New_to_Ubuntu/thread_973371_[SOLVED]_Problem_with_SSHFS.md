---
title: "[SOLVED] Problem with SSHFS"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by getitright on 2008-11-06
My sshfs file share has gone awry. 

When I enter:

sshfs <username>@<ipaddress>:/<remotepath> ~/<mountfile>

with the same entries that I used previously, successfully, I get the message "Connection reset by peer".

---

### Post by stephanvaningen on 2008-11-06
Some more background info needed.
You have correct network activity? You can ping the target? You can ping localhost? Can you ping your router address?

If ping is ok, is a:
 ```
sudo traceroute ip-address
```
also satisfactory?

---

### Post by getitright on 2008-11-07
I can ping the target address. Trying traceroute I get "sudo: traceroute: command not found"

---

### Post by getitright on 2008-11-07
I have tried file share in the reverse direction and it works correctly.

---

### Post by jaytek13 on 2008-11-07
> **getitright said:**
> I can ping the target address. Trying traceroute I get "sudo: traceroute: command not found"

sudo apt-get install traceroute... although a "connection reset by peer" message indicates you are reaching the server, so a traceroute probably won't help... do you have access to the server logs for the server you are trying to access?

---

### Post by getitright on 2008-11-07
> **jaytek13 said:**
> sudo apt-get install traceroute... although a "connection reset by peer" message indicates you are reaching the server, so a traceroute probably won't help... do you have access to the server logs for the server you are trying to access?

I have acces to the server but am not sure how to obtain the server logs.

---

### Post by getitright on 2008-11-07
> **getitright said:**
> I have acces to the server but am not sure how to obtain the server logs.

Will uninstalling and then reinstalling sshfs help the situation?

---

### Post by _sAm_ on 2008-11-07
Have you just upgraded from 8.04 to 8.10 and kept /home intact?

I did, and got that error message(witch don't tell you much). Google gave me more info; try delete known_hosts in /home/your_username/.ssh and connect again with ssh(it should now warn you about the new host), when that's done close ssh and try sshfs again.

sshfs is working fine on my system after doing that.

---

### Post by hyper_ch on 2008-11-07
could it be, that the remote computer has your IP blacklisted?
could it be, that if you try to go through a firewall that the ports aren't forwarded correctly?

---

### Post by jaytek13 on 2008-11-07
> **hyper_ch said:**
> could it be, that the remote computer has your IP blacklisted?
could it be, that if you try to go through a firewall that the ports aren't forwarded correctly?

"Connection reset by peer" is a response from the server he's trying to connect to. Generally speaking if you are blacklisted by a server you won't reach the point of getting a response, because the response is from the service, and if you're blacklisted you won't have the opportunity to connect to the service. 

Port forwarding... still doubtful. "Connection reset by peer" means you've established a connection, and then the connection was disconnected for one reason or another, and probably nothing to do with port forwarding.

---

### Post by _sAm_ on 2008-11-07
As I said; just delete known_hosts and try ssh again...

---

### Post by getitright on 2008-11-07
I am running Firestarter and have noted that when I use ssh to from my desktop an event is recorded however when I use ssh from my laptop to access my desktop there is no event record, does this cast any light on to a possible solution for my problem.

---

### Post by hyper_ch on 2008-11-07
is there any particular reason why you run firestarter?

---

### Post by getitright on 2008-11-07
> **_sAm_ said:**
> As I said; just delete known_hosts and try ssh again...

On client or server?

---

### Post by getitright on 2008-11-08
> **hyper_ch said:**
> is there any particular reason why you run firestarter?

I suppose that as a recent Windows user I do not feel safe without a firewall. The point I was making re-Firestarter events was that there does not appear to be any contact from the client, I may of course be wildly wrong.

---

### Post by _sAm_ on 2008-11-08
> **getitright said:**
> On client or server?

On client.

---

### Post by getitright on 2008-11-10
> **_sAm_ said:**
> On client.

Deleted known_hosts. When I enter "sshfs <username>@<server ipaddress>:/home/<clientusername> ~/<mountpoint>" The home file on my client is displayed, not that of the server. Using ifconfig the IP addresses of client and server are the same. My server is configured with a fixed IP and my client (wireless) is set to roaming.

---

### Post by getitright on 2008-11-10
Changed the IP address on the server. That has resolved my problem with sshfs. Thanks to all for the help.

---

