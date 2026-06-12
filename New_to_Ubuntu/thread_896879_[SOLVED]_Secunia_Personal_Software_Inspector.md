---
title: "[SOLVED] Secunia Personal Software Inspector"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by smith_fan on 2008-08-21
I am wondering how to use the Secunia Personal Software Inspector to scan my linux box for vulnerabilities.  I see that the System Requirements calls for only Windows-based machines, but, from searching to try to figure-out how to get it running on this laptop running Gutsy, I also see that they have official listings for the documented Ubuntu vulnerabilities.  So, I'm sure that what I am trying to do is in some way possible.  However, I am not finding how I can do it.

Should I just be satisfied with waiting for updates until they make it through to Synaptic or can anyone tell me how I can get it working under Ubuntu?:confused:

Thanks!,:)
~D~

---

### Post by django0909 on 2008-08-21
The first thing I would do is upgrade your Ubuntu install to something newer than Gutsy, preferable Hardy. Second of all, I would use Avast for dealing with the very minimal vulnerabilities a fully updated installation of Ubuntu will suffer from.

But that's just me :)

---

### Post by cariboo on 2008-08-21
Your windows software will not work in Linux. Remember Linux is not Windows. All of the programs you use to secure your windows computers are not needed when using Ubuntu. There are no Linux viruses out in the wild and a dead stock Ubuntu installation has only one open port, and that is only accessible from your own computer.

The premise behind windows malware and viruses does not work in Linux. You have to be root to install all programs except those that you install in your home directory, and anything in your home directory can not effect anything else in the rest of the system. Ubuntu uses sudo (Super User Do) to take the place of logging in as root. Running as root all the time can cause problems if you are not careful, you have the power to completely disable the system if you use commands that you don't understand.

The only reason I would recommend an anti-virus program is if you are forwarding a lot of email originating form windows computers, and a firewall is not needed unless you start installing services like ssh, apache2 or ftp.

There is a good article on Ubuntu security here:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

After you read the article you will see that most security just needs plain old common sense.

Jim

---

### Post by brian_p on 2008-08-21
> **smith_fan said:**
> 

Should I just be satisfied with waiting for updates until they make it through to Synaptic or can anyone tell me how I can get it working under Ubuntu?:confused:

From [https://psi.secunia.com/:](https://psi.secunia.com/:)

> **How can you protect yourself from software vulnerabilities?**

You simply need to keep your software updated. The only real solution, to avoid becoming a victim of a hacker exploiting software vulnerabilities, is to install the latest security updates that the software vendors release. In other words, make sure that you always have the latest secure versions of the software that you have installed on your computer.

Ubuntu's updates are timely so the security of your software is in good hands.

---

### Post by smith_fan on 2008-08-22
Thank you all very much for your input! ;)
~D~

---

