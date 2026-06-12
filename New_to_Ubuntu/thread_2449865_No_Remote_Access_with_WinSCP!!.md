---
title: "No Remote Access with WinSCP!!"
date: 2020-09-03
forum: New to Ubuntu
---

### Post by quazimotto on 2020-09-03
Greetings All,

I have a small problem with Unbuntu 20 running on VMWare.  I can not  access it using WinSCP.  I get an error saying the connection was  denied.  I have looked in the settings and didn't find anything.  Is  there a command in Linux to allow  WinSCP?

Thank You,
Quaz


I am a total Newbie at Linux.

---

### Post by CelticWarrior on 2020-09-03
Welcome.

It depends on the VM's network settings and the protocol you're trying to use. Just mentioning a "[COLOR=#4D5156][FONT=arial]SFTP, SCP, Amazon S3, WebDAV, and FTP client for Windows" tell us nothing about what you're trying to do.
Please give more information.[/FONT][/COLOR]

---

### Post by Impavidus on 2020-09-03
I don't know winscp. Is it a file copy tool for Windows using ssh? Make sure you've got openssh-server installed (that allows for incoming connections; openssh-client is for outgoing connections and is installed by default), configure your firewall (if you enabled it) and setup the network connection from your virtual machine.

---

### Post by TheFu on 2020-09-03
winscp is an scp/sftp client on Windows.  It supports drag-n-drop much like a normal Linux file manager supports the sftp:// URL to connect to other systems.  It has a 2-panel setup, but Exploder can be used too.

So ... when troubleshooting there are a few considerations.  We will deal only with a client and server on the same LAN. Over the internet has some additional settings required in the WAN router and firewalls.

Using a virtual machine means that the correct style of VM networking must have been selected.  Host-only and NAT won't work.  The VM should use "bridged" networking.

Next, the client and the server both need to have their firewalls allow outbound or inbound ssh traffic.  sftp/scp use the same port and authentication that normal ssh uses.  If ssh works (putty or ssh CLI command), but sftp doesn't work, please tell us. That is an important distinction.  Also, be certain that sftp is the selected protocol in WinSCP. That is easy to miss.  ssh, sftp, scp all use the same port.

Lastly, did you install ssh-server or openssh-server on the Ubuntu system?  Just installing it, should enable it and if you didn't setup a firewall rule to block everything already, then the sftp-server will be available for any userid on the Ubuntu system that allows logins.  Root cannot be used on a typical Ubuntu system, since remote connections to root aren't supported for security reasons.

Claro?

What is "Unbuntu"?

---

### Post by quazimotto on 2020-09-03
Guys,

Many thanks for the replies.  I installed ssh-server and enabled ssh on the box and it works great.

Thanks again,
Quaz

---

