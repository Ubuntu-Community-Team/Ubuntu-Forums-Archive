---
title: "How to get firebird on Ubuntu Server?"
date: 2015-04-14
forum: New to Ubuntu
---

### Post by andreipoznak on 2015-04-14
Hi. 

Completely new to servers and Linux. Installed Ubuntu Server on my older PC. Need to get Firebird on Ubuntu Server -
need complete instructions, since I am new at these things. Thanks in advance.

Andrei.

---

### Post by TheFu on 2015-04-14
Google found this: [https://help.ubuntu.com/community/Firebird2.5](https://help.ubuntu.com/community/Firebird2.5) ... but that might not be the version you want.

---

### Post by andreipoznak on 2015-04-15
Tried this.Throws out mistake after first line: [COLOR=#333333][FONT=UbuntuMono]sudo add-apt-repository ppa:mapopa[/FONT][/COLOR]

---

### Post by TheFu on 2015-04-15
> **andreipoznak said:**
> Tried this.Throws out mistake after first line: [COLOR=#333333][FONT=UbuntuMono]sudo add-apt-repository ppa:mapopa[/FONT][/COLOR]

From the "*teaching you to fish*" perspective ... take the exact error (copy/paste it) and put it into google (or post it here), remove anything that is probably specific to your machine/network (hostname, IPs, timestamps), then search. I'm guessing it is because the command wasn't found or permissions were denied. So, you need to install the package that has add-apt-repository.

When asking for help here, always copy/paste the command AND the *relevant* output to get help. Also, use "code tags" - in AdvReply has a button "#" for that, so things line up nicely. Please and thank you.

If you'd like to avoid frustrations like this going forward, spend about 3 hrs doing some directed, learning ... the first 5 items [in this list]("http://blog.jdpfu.com/2014/12/28/learning-linux") are the shortest ways I know. There are some great links to Ubuntu User Guides there too - desktop and server.

---

### Post by gordintoronto on 2015-04-15
[http://www.firebirdsql.org/manual/ubusetup.html](http://www.firebirdsql.org/manual/ubusetup.html)

---

### Post by Vladlenin5000 on 2015-04-15
The PPA is actually **[B]ppa:mapopa/ppa**[/B], not just ppa:mapopa (it could never work like that). So, this is wrong and should be edited ASAP: [https://help.ubuntu.com/community/Firebird2.5](https://help.ubuntu.com/community/Firebird2.5)

---

