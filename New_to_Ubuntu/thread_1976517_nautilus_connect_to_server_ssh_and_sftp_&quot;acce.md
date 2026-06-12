---
title: "nautilus connect to server ssh and sftp &quot;access denied&quot;"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by iansane on 2012-05-08
Hi,

This is the first time I tried to use nautilus to connect to sftp or via ssh and I'm having an issue.

It never asks me for my password but just instantly tells me
"Could not display "sftp://lotus@10.0.0.124/".
access denied"

I tried typing in the location bar
sftp://lotus@10.0.0.124

Also tried the "connect to server" using ssh protocol.

However, I think I have everything set up right on the ssh server because winscp from windows, ssh in cli from both windows and linux, and filezilla sftp all work perfectly.

I'm thinking it has to do with neither option giving me a chance to enter the password but have no idea why or how to fix it.

Thanks

---

### Post by papibe on 2012-05-08
Hi iansane.

By any chance did you change the default port (22)? You would have to reflect that also on the nautilus url. For instance:
```
sftp://lotus@10.0.0.124**[COLOR="Red"]:2222[/COLOR]**/home/lotus
```
Regards.

---

### Post by iansane on 2012-05-08
> **papibe said:**
> Hi iansane.

By any chance did you change the default port (22)? You would have to reflect that also on the nautilus url. For instance:
```
sftp://lotus@10.0.0.124**[COLOR="Red"]:2222[/COLOR]**/home/lotus
```
Regards.

Well actually even though the default port is 22, my laptop is trying to use 2222 to connect even when I type in 22 in the "connect to server" dialogue.

I thought I had tried ssh in terminal but had only been using putty, filezilla, and cli on windows. When I tried it in terminal without specifying a port it automatically used 2222.

So I went to the server and added port 2222 to the ssh_config and now it works.

Any idea why my laptop is defaulting to port 2222 when trying to connect?

Thanks

---

### Post by papibe on 2012-05-08
That is weird.

The default ports assigned for each service are in this file:
```
/etc/services
```
For example, you should be able to see the default ssh port like this:
```
grep ssh /etc/services 
```
Regards.

---

### Post by iansane on 2012-05-08
that is definitely weird.

the grep command tells me ssh is using 22.
```
lotus@lotus-laptop:~$ grep ssh /etc/services
ssh		22/tcp				# SSH Remote Login Protocol
ssh		22/udp
```

To make sure I didn't miss something I removed the port 2222 agian and left only port 22 on the server and this is what I get.
```
lotus@lotus-laptop:~$ ssh 10.0.0.124
ssh: connect to host 10.0.0.124 port 2222: Connection refused
```

What ever on the laptop is defaulting to 2222 must be what is causing the "connect to server" to get denied before asking for password but when I add 2222 back to sshd_config everything works fine.

This is probably good anyway because I'll start specifying port 2222 on my win machine but will be trying to figure out what's going on here on my laptop with ubuntu.

---

### Post by papibe on 2012-05-08
Interesting.

The other place where the port can be changed, on the client side, is the ssh client configuration file:
```
/etc/ssh/ssh_config
```
There the default port to 'make the call' can be set too. To easily see if it changed:
```
grep -i port /etc/ssh/ssh_config 
```
Regards.

---

### Post by iansane on 2012-05-08
> **papibe said:**
> Interesting.

The other place where the port can be changed, on the client side, is the ssh client configuration file:
```
/etc/ssh/ssh_config
```
There the default port to 'make the call' can be set too. To easily see if it changed:
```
grep -i port /etc/ssh/ssh_config 
```
Regards.

That's it! The client side is set to use port 2222. I have no idea why but am guessing that at some point in time I may have been trying to figure out ssh and set it to 2222? I don't know. But I'd say that solves my issue :-)

Thanks for all your help papibe

---

