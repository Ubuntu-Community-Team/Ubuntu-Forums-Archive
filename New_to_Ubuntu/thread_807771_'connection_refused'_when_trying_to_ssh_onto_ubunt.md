---
title: "'connection refused' when trying to ssh onto ubuntu server"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by MicMichael on 2008-05-26
When I attempt to ssh onto my ubuntu server I get a 'connection refused' error.
I can ssh into other machines, but always connection refused with this one. I'm tired so I might be forgetting something simple, but yeah. 
If someone could give me a hand that would be great, thanks.

---

### Post by kesman on 2008-05-26
Have you installed ssh server on the ubuntu box? =D

---

### Post by Xiong Chiamiov on 2008-05-26
If it was working before, but not now, it's probably due to the ssh vulnerability that's in the news recently.  Y'know, [the thing that's announced at the top of every page]("http://ubuntuforums.org/announcement.php?f=326")?

---

### Post by MicMichael on 2008-05-26
the ssh server is installed on the machine, yes.
and as for the vulnerability, only just installed ubuntu server...
(will update system packages soon~)

I'll muck around with it a bit and get my brother to take a look. 
~out for the next 24 hours.

---

### Post by aev on 2008-05-27
I have the same problem. After one of the updates on Hardy it simply stopped connecting. Also, using hardy  to connect to another unix box through SSH it used to log me in right into the specified directory - e.g., /home/username/ . Now it shows the whole tree of the public server - a bit annoying because it is a huge one and takes several clicks to get to my folder.

machine AMD64 x2 .

---

### Post by spiderbatdad on 2008-05-27
I believe ssh uses port 22 by default. Is port forwarded by your router? I've heard some isp's block the port.

---

### Post by AngryMallard on 2008-05-28
I don't think it's an issue with an ISP. I have several computers on my LAN, all with SSH installed. All computers but one have 32-bit Ubuntu 8.04 installed and the other has 64-bit Ubuntu 8.04. When I have port forwarding on my firewall and my router set up to forward port 22 to a 32-bit machine, everything works well. When I try to forward to the 64-bit machine, the connections gets closed immediately. Sometimes it just closes the connection, other times I get this:

```
bryan@TOWEL-UBUNTU:~/.ssh$ ssh everyone@xx.xx.xxx.xxx
Read from socket failed: Connection reset by peer

```

However, I can ssh to the 64-bit computer from the LAN, just not from the internets. 

Perhaps it is a problem with the 64-bit version?

---

### Post by Iowan on 2008-05-28
> **kesman said:**
> Have you installed ssh server on the ubuntu box? =DI realize I'm beating the same horse with a different stick, but... is the **sshd** daemon running? Does the machine have a firewall blocking ssh?

---

### Post by AngryMallard on 2008-05-29
OK, everything should work, but it isn't. My earlier post about it being an issue with the 64-bit version was not even close, I'm not sure if I was just confused as to what computer I was on or if the problem fixed itself, but now the same problems is happening for me on a regular 32-bit ubuntu 8.04. 

I can SSH from this computer to anywhere else but when I try to do "ssh localhost" or SSH to it from another computer I get the "connection refused" message.

I tried "killall sshd" and it killed something, then I restarted, but I'm not sure how to restart sshd if it isn't running already. I also tried removing the SSH package and reinstalling. Nothing seems to take.

---

