---
title: "iptables and router settings for proftpd"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by lambdafox on 2014-12-14
I am trying to set up an ftp server on my desktop running Ubuntu GNOME 14.04 [amd64].

I want to access the server using xdrive on my laptop that runs Windows Vista.  I would also like to be able to run xdrive on my Windows XP VM running in QEMU on my desktop.

My half-baked understanding is that I have to set port forwarding on for the listening port on TCP in my router.  So, I have set port forwarding on in the virtual servers section for tcp on port 21 on 192.168.0.100 -- my desktop's fixed IP address.  

As a linux noobie, the iptables rules are still pretty much a mystery to me.  I read [this thread on unix stackexchange]("http://unix.stackexchange.com/questions/110018/ftp-and-iptables-connection-fails-but-ports-are-open") about setting up iptables for proftpd.  The end says:

> ...This was the solution. Dont know why other configs did not work!

# allowing active/passive FTP

iptables -A OUTPUT -p tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 1024: --dport 1024: -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp --sport 1024: --dport 1024: -m state --state ESTABLISHED,RELATED,NEW -j ACCEPT

Are these the correct iptables rules for proftp I should use in Ubuntu also?

If I understand what those rules mean, port 21 would be the listening port, port 20 would be the active data port and port 1024 is the passive data port.  If I wanted a range for passive, I just replace 1024: with 1024:1124 or whatever.  Is that correct?

---

### Post by nerdtron on 2014-12-15
So you need you need to have access on the ftp from the public internet?

If so, I suggest first the following:
1. Turn off firewall on Ubuntu server. (no iptables etc.)
2. Test locally first. Have you correctly setup proftpd on the server?
3. Test your Vista and XP machine if hey can acess the proftpd server on the local network. You can use the fixed private IP of the server when you are doing this.
4. Now when you are sure that everything is working locally, try port forwarding on the router. If you are behind a home router, then I think that is enough already. You don't have to setup any iptables on the server. Routers with port forwarding by default will close all other ports effectively acting as a firewall in your home.

If you really want to enable firewall on the Ubuntu machine, it's easier to user UFW.
To open the FTP port:
```
sudo ufw allow 21
```
To open the SSH/SFTP port:
```
 sudo ufw allow 22
```

---

### Post by JKyleOKC on 2014-12-15
> **lambdafox said:**
> I am trying to set up an ftp server on my desktop running Ubuntu GNOME 14.04 [amd64].

I want to access the server using xdrive on my laptop that runs Windows Vista.  I would also like to be able to run xdrive on my Windows XP VM running in QEMU on my desktop.If you only need to access it from inside your local network, including the VM, you don't need FTP at all -- and because it's definitely a serious security risk, should NOT use it. Rather, NFS (Network File System) is a much better way to go.

However, if you need to access the server from outside your local net, thus making it available to the whole world including the Bad Guys, then one must accept the risk and create an FTP server. As it happens, I'm in this boat, so do have Proftpd installed and working.

Most of your initial assumptions are correct, but you'll be better off using/requiring "passive" rather than "active" mode for all FTP transfers. The difference is that Port 20 is then only used during the initial dialog with a client; data transfer goes through one of the defined passive ports instead. This eliminates many problems otherwise introduced by firewall coding at both ends of the circuit.

The major one of these problems is that ports below 1024 are restricted to use by root processes; that includes port 20. Using those around 1024 is also a bad idea, since many userland services already claim them. My own working server uses 51200-51299 since high port numbers are less likely to conflict with other services. You must add this definition into /etc/proftpd/proftpd.conf as well.

Here's the rule that I include in my own iptables rule set:```
-A INPUT -p tcp -m tcp --dport 51200:51299 -j ACCEPT

```That's part of a text file I use to set up iptables at boot time; I find this far simpler than using scripts as so many folk do.

[COLOR="#FF0000"]EDIT: I've realized that by posting that line, I just opened my own security. I've changed it a bit, and won't post the change, but it's an area in which to be extra watchful for unintended consequences![/COLOR]

The line for /etc/proftpd/proftpd.conf is ```
PassivePorts                  51200 51299

```It's also a good idea to be extremely conservative about allowing permissions to FTP users. The single major invasion I've suffered in the past 10 years or so came via the FTP server, where I had inadvertently allowed a user with root permission capability to log in when configuring a backup system. The invader discovered that user, logged in, and thence managed to subvert the entire box; I had to reformat the drives and reinstall everything from scratch.

Here's the part of my /etc/proftpd/proftpd.conf file that restricts permissions:```
<Limit LOGIN>
 DenyAll
</Limit>

# Anonymous configuration.

<Anonymous ~ftp>
 <Limit LOGIN>
   AllowAll
 </Limit>

# Limit everything except navigation everywhere in the anonymous chroot
 <Limit CWD CDUP PWD>
   AllowAll
 </Limit>
 <Limit ALL>
   DenyAll
 </Limit>
 
 <Directory incoming>
   AllowOverwrite on
   <Limit STOR CWD CDUP PWD SIZE REST>
     AllowAll
   </Limit>
   <Limit ALL>
     DenyAll
   </Limit>
 </Directory>

 <Directory public>
   <Limit RETR CWD CDUP PWD DIRS>
     AllowAll
   </Limit>
   <Limit ALL>
     DenyAll
   </Limit>
 </Directory>

 <Directory private>
   <Limit RETR CWD CDUP PWD>
     AllowAll
   </Limit>
   <Limit ALL>
     DenyAll
   </Limit>
 </Directory>

</Anonymous>


```This prohibits everyone from logging in except as user "anonymous" and then highly restricts that user from doing anything damaging. Even directory browsing is disabled. Incoming traffic is restricted to the "incoming" subdirectory, where nobody but myself can see it. Outgoing traffic can be via either of the other two subdirectories, but in the "private" area, directory listing is disabled so files there can be reached only via a link that I send to the recipient separately. Even the existence of such a directory is hidden from the outside world.

Since I've set up my own group to have r/w/x access to all the directories, I can do whatever I like at this end. The restrictions above have no effect on my actions.

Even so, security isn't perfect, and I get hundreds of invasion attempts each week. I've installed the "fail2ban" package (available in the repositories) to reduce them somewhat, but they're still a nuisance.

Keep in mind, too, that security is a process, not a package. You have to keep it always in mind, and follow up any suspicious happenings immediately, to keep from becoming an unknowing member of the spambot armies!

Hope this helps!

---

