---
title: "Beginners Guide to Security?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Lorelei- on 2008-08-13
Having recently switched from using Windows XP to a laptop with Ubuntu I'm completely flumoxed by the security features that Ubuntu offers. Coming from a Windows background, I've never really given security any thought beyond installing free anti-virus software and a firewall. So I was wondering if anyone could sign post me to somewhere that will explain a) what security is recommended for Ubuntu (in terms of anti-virus programmes/firewalls etc if applicable), b) explain how things like encryption and PGP keys work and c) how to install & set up all these things.

Thanks.

---

### Post by lisati on 2008-08-13
Have a look at [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338) - in particular look at the thread "Ubuntu Security" at [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by Nepherte on 2008-08-13
A pretty much complete explanation of the security in Ubuntu (versus Windows): [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by SunnyRabbiera on 2008-08-13
Well for your first one by default Linux in general is much more secure then windows, for one you really dont need antivirus/ antispyware/ antiaddware/ antimalware etc as the linux security model is very different then that in windows.
In windows it allows all users root access so it makes the system insecure as soon as you turn it on.
In linux that is different, the root user and the main user are seperated making things more secure.

---

### Post by hyper_ch on 2008-08-13
- generally you don't need antivirus (there are cases in which you want to use antivirus)
- generally you don't need to worry about a firewall - you have one installed, called iptables but it's set to let everything pass

- generally security is an ongoing process, you really only have to think about it when you start installing services (ssh server, webserver, ftp server, samba server, ....)

- generally the root of most problems is the user itself. Get used to the way ubuntu uses "sudo", what the file permissions are for, etc.

---

