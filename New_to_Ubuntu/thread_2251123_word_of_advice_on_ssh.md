---
title: "word of advice on ssh?"
date: 2014-11-02
forum: New to Ubuntu
---

### Post by adj3 on 2014-11-02
Hello people,

 I'm soon going to use ssh to connect to my computer remotely and access my samba server and do other stuff... Do you have any word of advice for me "security" wise? Also does it matter if I have a more "complex" domain name as opposed to a simpler one?

kind regards :)

---

### Post by Lars Noodén on 2014-11-02
Well, it is recommended to turn off root login and to disable password login in general, using keys instead.  Some also propose switching to a non-standard port to quiet the logs somewhat, but that's all it does.  The scanners find it regardless of port, so keys and no root login are your best bet.  

sshguard or fail2ban are also popular, but extra, to block repeated attempts to break in.  Again, keys are no root login are the way to go.

---

### Post by flaymond on 2014-11-02
SSH transmitting password across the Internet unencrypted. I suggest you to use OpenSSH. It 'encrypted' your password to avoid connection hijacking,eavesdropping and other attacks. You can read more here:

[http://www.openssh.com/](http://www.openssh.com/)

---

### Post by Lars Noodén on 2014-11-02
> **InterProg said:**
> SSH transmitting password across the Internet unencrypted. 

That would be telnet rather than any program implementing the SSH protocols.  [SSH is the protocol](https://tools.ietf.org/html/rfc4253) and uses strong encryption.  OpenSSH and Tectia are two examples of packages that implement that protocol.  Of the two packages, only OpenSSH is in the repository and Free software.  Tectia while it is fine as far as proprietary goes, it neither Free nor in the repository.

---

### Post by Habitual on 2014-11-02
Security works best in *layers*, so fail2ban, disabled root logins and ssh keys only work great, I also utilize the practice of deny all and allow explicit for ssh access using
```
/etc/hosts.allow:sshd: 127.0.0.1 <your_home_ip> <maybe_one_other>
/etc/hosts.deny:sshd: ALL

```
no reboot or service restart needed.

---

### Post by Lars Noodén on 2014-11-02
> **Habitual said:**
> I also utilize the practice of deny all and allow explicit for ssh access using

Just a heads up, OpenSSH after version 6.6 no longer supports the venerable [TCPwrappers](http://manpages.ubuntu.com/manpages/utopic/en/man5/hosts_access.5.html) (tcpd).

[http://www.openssh.com/txt/release-6.7](http://www.openssh.com/txt/release-6.7) 

I guess the main option would be to do those restrictions with UFW/IPtables or else xinetd.  

If you are on 14.04 LTS, everything is ok with tcpd, but later versions of Ubuntu will be affected and any eventual backports that might happen.

---

### Post by Habitual on 2014-11-02
Lars: 
Thanks for that. I already utilize ufw as part of the layers I mentioned.
I have one box running  6.6p1-2ubuntu2 on Ubuntu 14.04.1 LTS... so far so good.
I can't find an inetd.conf nor an xinetd.conf, so I'm guessing that if openssh-server gets upgraded, I'd have to install xinetd to make use of those restrictions using "only_from" in xinetd.conf?

Thanks.

---

### Post by Lars Noodén on 2014-11-02
Yes, "only_from" in xinetd.conf would do it, if you install xinetd.  But I think just UFW/IPtables would be enough on its own these days.  Packet filtering has come a very long way since tcpd was first popular.   My memories are that there were generally no filters at all back then.  For an idea how much has changed, notice the examples for tcpd include use of the once ubiquitous "finger".  However, with an LTS, I'm pretty sure that openssh-server will stay the same version for the whole life of the release  and just take patches for that version.  For 14.04 LTS that would be 6.6.  So if I understand correctly, 6.7 and later would only be available in the backports repository, if ever, for 14.04 LTS.

---

### Post by Habitual on 2014-11-02
Thanks Lars

---

### Post by matt_symes on 2014-11-03
> **Habitual said:**
> Thanks Lars

I second this. Thanks Lars.

---

### Post by adj3 on 2014-11-05
> **Lars Noodén said:**
> Well, it is recommended to turn off root login and to disable password login in general, using keys instead.  Some also propose switching to a non-standard port to quiet the logs somewhat, but that's all it does.  The scanners find it regardless of port, so keys and no root login are your best bet.  

sshguard or fail2ban are also popular, but extra, to block repeated attempts to break in.  Again, keys are no root login are the way to go.

Thanks Lars for your response. I have been doing some studying on ports and port forwarding (to anybody out there looking to learn about ports and port forwarding refer to the following website -----> [http://portforward.com/](http://portforward.com/) this website really explains a lot) I was just wondering for ssh should I open a port on TCP or UDP? also can you point me me to a website or kindly explain more about root login options on ssh and how to disable or enable it? I had one more concern when you refer to "keys" are you referring to using apps such as keepass?

Regards

---

### Post by Lars Noodén on 2014-11-05
> **adj3 said:**
> Thanks Lars for your response. I have been doing some studying on ports and port forwarding (to anybody out there looking to learn about ports and port forwarding refer to the following website -----> [http://portforward.com/](http://portforward.com/) this website really explains a lot) I was just wondering for ssh should I open a port on TCP or UDP? also can you point me me to a website or kindly explain more about root login options on ssh and how to disable or enable it? I had one more concern when you refer to "keys" are you referring to using apps such as keepass?

Regards

SSH uses only TCP, so UDP does not need to be opened.  

At this point I would propose ed25519 keys instead of RSA, but that does not matter so much.  The gist is that you generate a keypair using [ssh-keygen](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-keygen.1.html) and transfer the *public* key up to the server and put it in the file ~/.ssh/authorized_keys by default.  There are many ways to make that transfer, including copy and paste, but often [ssh-copy-id](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-copy-id.1.html) is used to make the transfer.  

There is a verbose description here:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

*Please, make sure your keys work before removing password access*

RootLogin options are explained in the manual pages for [sshd_config](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html), which on Ubuntu refers to the file /etc/ssh/sshd_config.  That is the most authoritative source of information about sshd configuration and, though manual pages in general vary in quality, the ones for OpenSSH are on the high end.  The details are in **PermitRootLogin**.  Basically set that to "no" if you are not doing anything unusual with remote scripting requiring root access.  

About the keys, once you have them working, set **PasswordAuthentication** to "no".  There are more options, but that is the basic idea.  

Once you make changes to sshd's configuration, the service has to be restarted on the remote server.  

```

sudo service ssh restart

```

About using the keys, if you are constantly logging into and out of the server using the keys, you might make use of the key agent that Ubuntu runs by default.  A graphical program to manage such keys is "seahorse" also known as "passwords and keys" in the Dash.  I'm not sure a password manager would be relevant, but I'd avoid Keepass and look at Keepassx instead, it is built using Qt not Mono.  Anyway, Seahorse will do the job of holding your key in memory so you can re-use it.  I think (but have not tried it) that it works with Gnome Keychain so that if you choose it, Seahorse's keys are unlocked for you by Gnome Keychain when you log into Ubuntu.  Howver, I have not tried that yet myself.  I just use the agent.

---

### Post by adj3 on 2014-11-17
Hey Lars, I did study the links you attached in your previous post they were extremely useful, thanks. I did set everything up but I can not connect to my remote machine I get the following error: "ssh : connect to host [hostname] port 22: Connection refused" this is also odd because I never opened port 22 and also I change the "what ports to listen to" parameter in sshd_config (on the remote machine) to the port I forwarded. Any advice?

Thank you :)

---

### Post by Lars Noodén on 2014-11-18
What is the exact line you are using to connect?  If you changed to a non-standard port, you will have to tell that to the client when you try to connect.  Otherwise it will always try port 22 and, if nothing is listening on port 22 or it is not open, you will get that kind of error.  You can specify the port with the option **-p** in [ssh](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html).  If you are always connecting from the same machine, then you could make a shortcut in [~/.ssh/config](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html).

---

