---
title: "Do I need to install putty?"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by Deniz343 on 2012-06-23
Hi everyone I'm new in Ubuntu 12.04 LTS. And I'm just asking should I need to install PuTTY to my pc. Can I do PuTTY's work on terminal.

Hope you understand
Best Regards

---

### Post by CharlesA on 2012-06-23
You would only need Putty if you are trying to connect via SSH from a Windows box.

If you are using Ubuntu, just open a terminal and go nuts.

---

### Post by Paqman on 2012-06-23
> **Deniz343 said:**
> Can I do PuTTY's work on terminal.


Yep, sure can. For example:
```
ssh username@IP.of.server
```
...will establish an SSH connection.

---

### Post by Deniz343 on 2012-06-23
> **CharlesA said:**
> You would only need Putty if you are trying to connect via SSH from a Windows box.

If you are using Ubuntu, just open a terminal and go nuts. Thanks for your very fast reply. 

> **Paqman said:**
> Yep, sure can. For example:
```
ssh username@IP.of.server
```
...will establish an SSH connection. Thanks and can I file transfer with SSH.

---

### Post by CharlesA on 2012-06-23
> **Deniz343 said:**
> Thanks for your very fast reply. 

 Thanks and can I file transfer with SSH.

Yes, sftp, and scp work the same as they do on Windows.

I prefer rsync over ssh when transferring files from linux to linux tho.

rsync /path/to/source user@host:/path/to/destination

---

### Post by HiImTye on 2012-06-23
rsync is my favorite tool for even transferring locally to say a pen drive

---

### Post by Deniz343 on 2012-06-23
Okey then this is my last question: Can I reach my Ubuntu server from anywhere in world.

---

### Post by CharlesA on 2012-06-23
> **Deniz343 said:**
> Okey then this is my last question: Can I reach my Ubuntu server from anywhere in world.
If you have openssh-server installed and the proper ports forwarded, yes.

However, if you do decide so allow ssh access to the internet, please secure it properly. See the Security link in my signature.

---

### Post by Deniz343 on 2012-06-23
> **CharlesA said:**
> If you have openssh-server installed and the proper ports forwarded, yes.

However, if you do decide so allow ssh access to the internet, please secure it properly. See the Security link in my signature.

I found two links to secure SSH: 
[http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/](http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/)
[http://www.farinspace.com/secure-login-linux-server/](http://www.farinspace.com/secure-login-linux-server/)

And I watched a few YouTube videos about forwarding port. Let's say the SSH is secure and I setup the port forwarding. Then what should I do.

---

### Post by CharlesA on 2012-06-23
You can make sure it is open by checking at canyouseeme.org and if that is ok, you are good to go.

---

### Post by Deniz343 on 2012-06-23
Thanks for everything. I have one more question: Is there a login screen coming after I enter external ip and port number to internet explorer?

---

### Post by CharlesA on 2012-06-23
> **Deniz343 said:**
> Thanks for everything. I have one more question: Is there a login screen coming after I enter external ip and port number to internet explorer?
You can't use IE, you would have to use Putty or another SSH client and that would only give you shell access.

---

### Post by Deniz343 on 2012-06-23
> **CharlesA said:**
> You can't use IE, you would have to use Putty or another SSH client and that would only give you shell access.

Im using [http://itunes.apple.com/us/app/issh-ssh-vnc-console/id287765826?mt=8]("http://itunes.apple.com/us/app/issh-ssh-vnc-console/id287765826?mt=8") app on iPad. Can I control my Ubuntu with SSH client.

---

### Post by CharlesA on 2012-06-23
Yes.

---

### Post by Deniz343 on 2012-06-24
I need to enter host, port, login, command. I know host and port but what is the "command". And I think "login" is "username" am I right. 

Thanks

---

### Post by CharlesA on 2012-06-24
Login is usename, port should be 22 if you use the default and as far as I know you do not need to give it a command to just login.

---

### Post by Deniz343 on 2012-06-24
> **CharlesA said:**
> Login is usename, port should be 22 if you use the default and as far as I know you do not need to give it a command to just login.

I will change my port to another 4-digit number. For more security. And thanks for your security guide. I will use HIDS to secure my pc.

---

### Post by CharlesA on 2012-06-24
HIDS is overkill normally as it is only a reactive intrusion detection system.

Read this too:
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by Deniz343 on 2012-06-24
> **CharlesA said:**
> HIDS is overkill normally as it is only a reactive intrusion detection system.

Read this too:
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

I read it but this URL only help me to figure port forwarding not security. What should I do for more secure pc. And i need to figure port forwarding thanks :D

---

### Post by CharlesA on 2012-06-24
Read this:
[http://www.debian-administration.org/articles/87](http://www.debian-administration.org/articles/87)

---

### Post by Deniz343 on 2012-06-24
> **CharlesA said:**
> Read this:
[http://www.debian-administration.org/articles/87](http://www.debian-administration.org/articles/87)

Is this enough to secure SSH.

---

### Post by CharlesA on 2012-06-24
For the most part, yes.

I have SSH locked down by username, and only have a couple IPs whitelisted.

---

### Post by Deniz343 on 2012-06-26
> **CharlesA said:**
> For the most part, yes.

I have SSH locked down by username, and only have a couple IPs whitelisted.

Let's say my nas server in France and I want to connect my nas server from USA. How can I add my devices (iPad, pc etc.) to ```
etc/hosts.allow/
``` Could you please check this link as well it would help [http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/]("http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/")

---

### Post by CharlesA on 2012-06-26
> **Deniz343 said:**
> Let's say my nas server in France and I want to connect my nas server from USA. How can I add my devices (iPad, pc etc.) to ```
etc/hosts.allow/
``` Could you please check this link as well it would help [http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/]("http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/")
You would only need to allow whatever external IP you are going to be connecting from. If you are going to be using your stuff at cafes and wifi hotspots, you might as well just leave SSH open to the internet but add rules such as this one:

```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH --rsource -j ACCEPT
sudo iptables -A INPUT -m recent --update --seconds 600 --hitcount 8 --rttl --name SSH --rsource -j DROP
```

Change --dport 22 to whatever port you are using for ssh. This helps limit traffic on that port by blocking a connecting IP for 10 minutes after 8 "hits" or connection attempts, which would be commonly used for bruteforcing a service.

More infos are here:
[http://bodhizazen.net/Tutorials/SSH_security](http://bodhizazen.net/Tutorials/SSH_security)

---

### Post by Deniz343 on 2012-06-26
> **CharlesA said:**
> You would only need to allow whatever external IP you are going to be connecting from. If you are going to be using your stuff at cafes and wifi hotspots, you might as well just leave SSH open to the internet but add rules such as this one:

```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH --rsource -j ACCEPT
sudo iptables -A INPUT -m recent --update --seconds 600 --hitcount 8 --rttl --name SSH --rsource -j DROP
```

Change --dport 22 to whatever port you are using for ssh. This helps limit traffic on that port by blocking a connecting IP for 10 minutes after 8 "hits" or connection attempts, which would be commonly used for bruteforcing a service.

More infos are here:
[http://bodhizazen.net/Tutorials/SSH_security](http://bodhizazen.net/Tutorials/SSH_security) Thanks for everything. This article help me a lot for everything I need.

---

