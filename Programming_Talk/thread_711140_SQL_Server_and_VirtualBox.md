---
title: "SQL Server and VirtualBox"
date: 2008-02-29
forum: Programming Talk
---

### Post by WadiJM on 2008-02-29
Hi All! I need to use ms sql for a program i'm doing. I need to connecto from netbeans to the database so I installed virtualbox, windows xp and then I tried to connect with the ip given fro,m virtualbox(10.0.2.15) but it throws an unknow host exception. Does anyone how to share the sql server from virtualbox to ubuntu? 
Thanks in advance,
regards,
Wadi

---

### Post by twistedtwig on 2008-02-29
can you ping the VM machine at all?

check you can connect to the machine, hopefullly this will remove one posisble error, i.e. machine is not accessible.  Then it would be MS SQL Server that is the issue.  I found that i had to turn the Firewall off to get my VM box to play nice

---

### Post by WadiJM on 2008-02-29
Firewall is deactivated. I cannot ping , I tried 10.0.2.15, 10.0.2.2, "colosus"(the name if the vmachine, etc. I really don't want to restart and use my ide in windows xp. Do I have to configure something else?How do you ping your vm? I tried localhost to. 
Any help??
Thanks in advance,
Wadi

---

### Post by WadiJM on 2008-02-29
With the net utilities I figured out that the port 445 is open ( microsoft-ds) but it throws a timeout if i try to connect....:(

---

### Post by seamless on 2008-02-29
You need to use Host Networking instead of NAT. [This]("http://ubuntuforums.org/showthread.php?t=346185") should help you get it working.

---

### Post by VorDesigns on 2008-02-29
> **seamless said:**
> You need to use Host Networking instead of NAT. [This]("http://ubuntuforums.org/showthread.php?t=346185") should help you get it working.

An after you do that, tke a look at a few things and answer a few questions:
1.  If the system is XP post SP2; check your Windows firewall settings and see if there is an exception for port 445 open.  the Windows firewall blocks most ports by default.
2.  If the system has an A/V application that includes a firewall component, check for application in/out settings.  It depends what you are running.
3.  You stated MSSQL but you didn't qualify what version; ie., MSDE (desktop MSSQL), SQL Standard, SQL Enterprise, SQL2005 Studio, etc.,.  I ask because some of the versions don't automatically run the TCP/IP stack.
4.  How did you install the MSSQL server?  Is it the default instance which would connect directly to the IP and port or, is it a named instance which would use the IP, instance name and port.

I Hope this helps.

---

### Post by WadiJM on 2008-03-26
Thank you all, I downloaded the latest version of virtualbox after removing the installed via apt-get. All the info was great, this link also help me to get things to work [http://libre-web.blogspot.com/2007/12/instalar-virtualbox-en-debian-lenny.html]("http://libre-web.blogspot.com/2007/12/instalar-virtualbox-en-debian-lenny.html")

Thanks!

---

