---
title: "SSH howto"
date: 2005-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by crazybill on 2005-04-15
Please note that the default configuration for SSH on the Obuntu 5.04 (hoary hedgehog) Linux server does not permit logon with older versions of  Putty or WinSCP.  This may be a ssh1/ssh2 problem.  The best solution is to upgrade the windows machines on your network with the latest versions of   [putty](ftp://ftp.cvc.org/putty) and [winscp](ftp://ftp.cvc.org/winscp). If you are on a private network, you can change Password Authentication to text... but it is not recommended for public IP addresses.  The setup testing and configuration of SSH is simple.

If you can not reach your Ubuntu server with putty or WinSCP,  here is the testing procedure.

First, make sure you have the SSH service installed
**apt-get install ssh** 

After installing you should  see SSHd as a running process  with **top**  or **ps aux** . If you have a lot of processes running, try 

# ** ps aux | grep ssh**

If the process is running and you still can not connect, the configuration file has probably not been  modified. You will need to do the following:

1. **cp /etc/ssh/sshd_config  /etc/ssh/sshd_config_backup**  (backup your sshd configuration file first)
2.  **vi /etc/ssh/sshd_config**   or **gedit /etc/ssh/sshd_config**  from Gnome (edit your sshd_config file)
3. change **PasswordAuthentication no ** to  **PasswordAuthentication yes**  if you want clear text passwords -- but only do this on private networks -- not on servers with public IPs.
4. Make sure your configuration does not allow root login
4. save
5.**/etc/init.d/ssh restart** (Restart your sshd daemon)

Now you will be able to log in to your server with putty and/or WinSCP  ... or gftp from another Linux computer via port 22. :)

---

### Post by Dromio on 2005-04-15
I think something else is going on there.   I do not have PasswordAuthentication turned on, but I am able to access my machine using Putty and WinSCP.  But I am not running sshd on port 22.

---

### Post by crazybill on 2005-04-15
Putty and WinSCP defaults to port 22.

Make sure you  **ps aux**  and examine the  details for sshd

---

### Post by Dromio on 2005-04-15
[QUOTE=crazybill]Putty and WinSCP defaults to port 22.

Make sure you  **ps aux**  and examine the  details for sshd[/QUOTE]
 I know that.  I'm saying that sshd DID work out of the box for me, I didn't have to make the change you spcified in your initial post.  Then I moved my sshd to run on another port, but that's not really relevant.  I shouldn't have mentioned it.

I do not have PasswordAuthentication turned on (because I do not need cleartext passwords), and am able to connect using Putty and WinSCP without issue.

Sorry if it wasn't clear.  I just wonder if this change is really necessary.  Or is my sshd server not using /etc/ssh/sshd_config?  Or maybe something else in my config is still allowing password authentication.

---

### Post by crazybill on 2005-04-23
I see what you are saying.  Basically, if it is not necessary, dont change your sshd_config. With some machines on my network to work, I had to make those changes. However, they were not running the latest versions of putty and WinSCP. 

My suggestion to anyone is to make sure you have the latest versions of WinSCP and putty on your windows machines first. They do a better job of deciding between ssh1 and ssh2. You may not have to make any configuration changes on your Ubuntu Linux server if you do that.

---

### Post by blueplazma on 2005-04-23
You might have installed different packages during the install process which could be why one of you had SSHD running out of the box and the other didn't.

---

### Post by dewey on 2005-04-23
Just apt-getting it from the ubuntu repos worked out of the box for me.  After I ensured it was working, I edited my config to NOT permit root logins.  Even though I haven't activated the root account, I may in the future, and then forget to disable root logins in sshd.  Disabling root logins is a huge security boost, because that's the primary account that the worms target.

---

### Post by crazybill on 2005-04-24
The problem with using ssh to log onto Ubuntu servers lies not really with the out of the box Ubuntu settings but with older versions of putty and WinSCP.  I have over 400 computers on our network. Some of them were not able to log onto the server initally. This was a puzzle, at first, because some machine could log on fine and some could not. By changing the configuration to clear text passwords, some of the Windows 2K machines that could not log on with putty or WinSCP could do so. However, when I installed the newest versions of these freeware programs, I had no problems even without clear text password authentication. Thus, I configed /etc/ssh/sshd_config back to

PasswordAuthentication no

All computers on the network (that I tested) were able to log on with both putty and WinSCP, including those that were not able to do so before.

---

### Post by foxy123 on 2005-04-25
it's a nice howto for those who know how to use ssh in general. not my case.

well, I've got ssh running. What next? I want to be able to access my home pc from work, when I need it. What steps should I take to do it? Please, if you want to answer, do not assume that I know much about networking and ssh. I have no idea, for example, how to find my PC in the Internet. Should I type my ip address or there are other means of identifying it? And so on...

Help will be very appreciated.

---

### Post by slipp3dstr3am on 2005-04-26
I will second that question ... 

any info would help

---

### Post by jiyuu0 on 2005-04-26
[http://ubuntuguide.org/#sshserver](http://ubuntuguide.org/#sshserver)

---

### Post by crazybill on 2005-04-27
Concerning your request, I have a tutorial at [http://home.cvc.org/ac/learningUNIX.htm](http://home.cvc.org/ac/learningUNIX.htm)

First, you need to install the latest versions of  putty and WinSCP for your windows computer. You can download them from our FTP server ( [ftp://ftp.cvc.org/putty](ftp://ftp.cvc.org/putty)  and [ftp://ftp.cvc.org/winscp](ftp://ftp.cvc.org/winscp).)

Putty opens up a terminal with which you can log onto your Hoary Ubuntu Linux computer. 
The name comes from Put tty (tty is your terminal). When putty opens, you need to type in the IP address of your Ubuntu computer (Can I assume you know how to find this information? Type ifconfig on your Hoary computer), click on SSH radio button, and make sure the port is port 22 (which is the default port for SSH). Next a terminal will open, just like the terminals on your Ubuntu computer. You use it the same. You will NOT see a Gnome desktop. You will, however, see the terminal that you would use on a Ubuntu Linux computer. A website that I made for my students (see above) gives you terminal commands and what they do.

WinSCP allows you to easliy move files between your Windows computer and your Linux computer. It produces a window on the left side which is your Windows computer (local machine) and you Ubuntu computer (remote machine) on the right side. It is easy to use and obvious. When you first open WinSCP, you type in the IP address of your Ubuntu computer (Can I assume you know how to find this information? See above paragraph), your ubuntu username, and your ubuntu password. After logging in, you navigate your Windows computer on the left and your Ubuntu computer on the right. Highlight the file you want to copy from one computer to the other and click on copy. Really easy to use.

Using SSH is a secure means to talk between computers.

If you are talking about logging onto your Ubuntu computer at home from your Windows computer at work... more information is needed. If you have a broadband connection (cable, DSL, Satellite,etc) and have a router between your home computer and your ISP connection, you will need to open a port 22 hole in your router so that you can use the router's public  IP address, yet communicate with your computer. You would use the router's public IP address, not your computer's private IP address. However, if you are not using a router, type "ifconfig" in a terminal window on your Ubuntu computer. If you are in Gnome, you can also type ctl-alt-F2 to get to a terminal and the ctrl-alt-F7 to return to Gnome -- or simply open a terminal window in Gnome  to discover your home Ubuntu computer's IP address. Write down that IP address and that is what you would use from your work computer.

Hope this helps some and answers your questions.

---

### Post by whocarez on 2005-05-27
[QUOTE=crazybill]
2.  **vi /etc/ssh/sshd_config**   or **gedit /etc/ssh/sshd_config**  from Gnome (edit your sshd_config file)
3. change **PasswordAuthentication no ** to  **PasswordAuthentication yes**  if you want clear text passwords -- but only do this on private networks -- not on servers with public IPs.
[/QUOTE]
[quote=ssh man page]
If other authentication methods fail, ssh prompts the user for a pass-
     word.  The password is sent to the remote host for checking; however,
     since all communications are encrypted, the password cannot be seen by
     someone listening on the network.
[/QUOTE]
I'm pretty sure that enabling password authentication **doesn't** send the password in clear text. I believe it's been disabled because of security flaws in SSH1. One still has keyboard-interactive in SSH2, which is more or less equivalent to password authentication.

I think some ssh-clients broke because of the **PasswordAuthentication no** default setting because they didn't try or implement keyboard interactive.

---

### Post by foxy123 on 2005-05-27
[QUOTE=crazybill]Concerning your request, I have a tutorial at [http://home.cvc.org/ac/learningUNIX.htm](http://home.cvc.org/ac/learningUNIX.htm)

First, you need to install the latest versions of  putty and WinSCP for your windows computer. You can download them from our FTP server ( [ftp://ftp.cvc.org/putty](ftp://ftp.cvc.org/putty)  and [ftp://ftp.cvc.org/winscp](ftp://ftp.cvc.org/winscp).)

Putty opens up a terminal with which you can log onto your Hoary Ubuntu Linux computer. 
The name comes from Put tty (tty is your terminal). When putty opens, you need to type in the IP address of your Ubuntu computer (Can I assume you know how to find this information? Type ifconfig on your Hoary computer), click on SSH radio button, and make sure the port is port 22 (which is the default port for SSH). Next a terminal will open, just like the terminals on your Ubuntu computer. You use it the same. You will NOT see a Gnome desktop. You will, however, see the terminal that you would use on a Ubuntu Linux computer. A website that I made for my students (see above) gives you terminal commands and what they do.

WinSCP allows you to easliy move files between your Windows computer and your Linux computer. It produces a window on the left side which is your Windows computer (local machine) and you Ubuntu computer (remote machine) on the right side. It is easy to use and obvious. When you first open WinSCP, you type in the IP address of your Ubuntu computer (Can I assume you know how to find this information? See above paragraph), your ubuntu username, and your ubuntu password. After logging in, you navigate your Windows computer on the left and your Ubuntu computer on the right. Highlight the file you want to copy from one computer to the other and click on copy. Really easy to use.

Using SSH is a secure means to talk between computers.

If you are talking about logging onto your Ubuntu computer at home from your Windows computer at work... more information is needed. If you have a broadband connection (cable, DSL, Satellite,etc) and have a router between your home computer and your ISP connection, you will need to open a port 22 hole in your router so that you can use the router's public  IP address, yet communicate with your computer. You would use the router's public IP address, not your computer's private IP address. However, if you are not using a router, type "ifconfig" in a terminal window on your Ubuntu computer. If you are in Gnome, you can also type ctl-alt-F2 to get to a terminal and the ctrl-alt-F7 to return to Gnome -- or simply open a terminal window in Gnome  to discover your home Ubuntu computer's IP address. Write down that IP address and that is what you would use from your work computer.

Hope this helps some and answers your questions.[/QUOTE]

thanks a lot for tutorial. I have not been subscribed on this thread, so came across it only now.

I will try to do it at home. I have broadband at home via router. I guess I have to open 22 port in router and firewall.

What about the firewall at work? Will it block ssh connection? Any walkaround?

Another thing, is there any way to test ssh connection from the same PC. I mean I've got only on computer at home, so I want to be able to test ssh when I install and configure it. How can I do it?

---

### Post by bpilgrim1979 on 2005-05-27
[QUOTE=whocarez]I'm pretty sure that enabling password authentication **doesn't** send the password in clear text.[/QUOTE]
It is clear text, but clear text tunneled through the encrypted ssh connection.  The terms can be a little confusing.  The default sshd_config file has the following comment:

```
# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication yes
```

---

### Post by slimb on 2005-05-29
[QUOTE=foxy123]I will try to do it at home. I have broadband at home via router. I guess I have to open 22 port in router and firewall.[/QUOTE]

yep - you most likely will have to add one entry in your port forwarding section

> 

What about the firewall at work? Will it block ssh connection? Any walkaround?



depends on your work firewall.  most places of employment dont block SSH outbound.  if they do - you *could* find a port that you can get out on and then tell your ssh server at home to listen on that port (it doesn't HAVE to be 22).  but if you're going through that kind of trouble, methinks your employer wouldn't be too happy about it.

> 

Another thing, is there any way to test ssh connection from the same PC. I mean I've got only on computer at home, so I want to be able to test ssh when I install and configure it. How can I do it?

from your commandline on the machine at home you can always just ssh localhost

this'll tell you if SSH is working.  however it won't test your router / firewall at all.  you can try ssh 1.2.3.4   where 1.2.3.4 is your own IP address (the one assigned to your router by your internet provider).

---

### Post by foxy123 on 2005-05-29
[QUOTE=slimb]
from your commandline on the machine at home you can always just ssh localhost

this'll tell you if SSH is working.  however it won't test your router / firewall at all.  you can try ssh 1.2.3.4   where 1.2.3.4 is your own IP address (the one assigned to your router by your internet provider).[/QUOTE]

localhost connection works fine. However, I cannot connect to my ip address :-(

---

