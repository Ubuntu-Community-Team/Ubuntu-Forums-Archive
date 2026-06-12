---
title: "UFW - problems running any help?"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by alexosydney on 2012-09-21
Hello, thank you in advance. Managed to install ufw manually using the python command. I installed ufw-0.33. When I type sudo ufw enable at the command prompt (as root), i get as follows:

I can work out initially that I have a permissions issue but beyond that I am at a loss
to work out where I can even start to check to resolve the problem...

I am new to Ubuntu and was trying to install a firewall.

Ubuntu 10.04.1 

--------------------------------------------------------------------------------------
WARN: /etc/default/ufw is group writable!
WARN: /lib/ufw/ufw-init is group writable!
WARN: /etc/ufw/ufw.conf is group writable!
WARN: /usr/sbin/ufw is group writable!
WARN: /etc/ufw/applications.d/ufw-bittorent is group writable!
WARN: /etc/ufw/applications.d/ufw-dnsserver is group writable!
WARN: /etc/ufw/applications.d/ufw-printserver is group writable!
WARN: /etc/ufw/applications.d/ufw-directoryserver is group writable!
WARN: /etc/ufw/applications.d/ufw-chat is group writable!
WARN: /etc/ufw/applications.d/ufw-mailserver is group writable!
WARN: /etc/ufw/applications.d/ufw-proxyserver is group writable!
WARN: /etc/ufw/applications.d/ufw-loginserver is group writable!
WARN: /etc/ufw/applications.d/ufw-webserver is group writable!
WARN: /etc/ufw/applications.d/ufw-fileserver is group writable!
Traceback (most recent call last):
  File "/usr/sbin/ufw", line 95, in <module>
    ui = ufw.frontend.UFWFrontend(pr.dryrun)
  File "/usr/local/lib/python2.6/dist-packages/ufw/frontend.py", line 153, in __init__
    self.backend = UFWBackendIptables(dryrun)
  File "/usr/local/lib/python2.6/dist-packages/ufw/backend_iptables.py", line 45, in __init__
    ufw.backend.UFWBackend.__init__(self, "iptables", dryrun, files)
  File "/usr/local/lib/python2.6/dist-packages/ufw/backend.py", line 88, in __init__
    nf_caps = ufw.util.get_netfilter_capabilities(self.ip6tables)
  File "/usr/local/lib/python2.6/dist-packages/ufw/util.py", line 734, in get_netfilter_capabilities
    raise OSError(errno.ENOENT, out)
OSError: [Errno 2] [Errno 2] No such file or directory


Thanks a lot for assistance, does anyone know where the problem could be at?


Alex

---

### Post by newb85 on 2012-09-21
Welcome!

Why did you try to install UFW with a python command?  UFW is in the repositories...and installed by default.

---

### Post by alexosydney on 2012-09-21
I installed ufw by downloading the package and then i placed in tmp. Then
ran a python command with setup.py

I am new to ubuntu and i got a vps server. When I was trying to enable ufw
it happen that the package was not installed by default.

I was not aware either that I could get the package via the sources list even
though I had to manually add the websites.

Should I uninstall the ufw?

Regards, 

Alex O.

---

### Post by s1baker on 2012-09-21
I have just started to learn about firewalls and using ufw.
I installed gufw ( the graphical user interface for ufw ) from the snaptic package manager.

It is so much easier to learn and use than the terminal commands.

Also, the ubuntu security forum is the place you want to go for ufw questions.
Here are some good links from that forum:

[http://ubuntuforums.org/showthread.php?t=1871177]("http://ubuntuforums.org/showthread.php?t=1871177")


[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by KegHead on 2012-09-27
Hi!

Does anyone know of a guide to what ports should be open or closed?

Thanks!

KegHead

---

### Post by newb85 on 2012-09-27
> **KegHead said:**
> oes anyone know of a guide to what ports should be open or closed?

This is my understanding, and probably needs some correcting:

There's a difference between ports being closed and ports being blocked.  
All ports are closed by default, and the appropriate ports are opened at appropriate times automatically (and similarly re-closed).
A firewall blocks certain ports (according to rules), meaning they can't be opened.  UFW's default rules will probably work for you, provided you're not using the machine as a server.

---

### Post by HiImTye on 2012-09-28
> **KegHead said:**
> Does anyone know of a guide to what ports should be open or closed?
all ports that you don't explicitly open should be closed, unless you are either connecting to another server, or hosting a server yourself.
any program that allows incoming connections is a server. one example would be SMB, the protocol used for sharing files and printers between Windows machines, as well as Linux machines, by way of SAMBA. another type of server is CUPS (Common Unix Printing System). your computer needs to be able to accept connections from any network printer that you are using.
the way to figure out if a program is a client or a server is by determining how the program is used. if you initiate a connection to a remote computer, then usually it is simply a client. if you wait for a remote computer to connect to your computer, then it is a server. the list of ports you need open is entirely dependant on the server. usually you can do some Googling to find the exact port numbers and protocols that you need to have open. if you have any questions, feel free to start a new thread.

---

### Post by KegHead on 2012-09-28
Hi!

Closed by default works for me!

Thanks to all!

KegHead

---

### Post by KegHead on 2012-09-29
Hi!
just a follow up.

I'm using pglgui and gufw.

Am I covering all of the bases?

KegHead

---

