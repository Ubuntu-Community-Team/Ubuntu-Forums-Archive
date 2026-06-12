---
title: "mailserver with administration tool"
date: 2014-10-26
forum: New to Ubuntu
---

### Post by fabianus76 on 2014-10-26
Hello everybody !

I am looking for an easy to install mailserver solution that includes an administration tool (we use ubuntu server 10.04.4). 
Thanks for any feedback for a simple package ... that is powerfull :-)

Best regards, 
Fabianus

PS I do not need an advanced anti-spam solution as my users fetch emails into gmail and then retrieve them from there. And Gmail does the anti-spam stuff very well for us. Thus we do not need any web interface to read and write emails (like roundcube).

---

### Post by sandyd on 2014-10-27
Before I continue, note that Ubuntu 10.04 will no longer be supported in April 2015 next year.

Try (in this order)
Postfixadmin
Axigen
iRedMail

Postfixadmin would be the only one out of the three that can be easily installed without installing additional software other than postfix (iRedMail includes clamav, etc ,etc). However, I have found iRedMail quite complicated to upgrade.
Axigen uses its own software.

I have removed Zimbra from the list as it uses 2G RAM and is probably overkill

---

### Post by nerdtron on 2014-10-27
We used iredmail on my previosu company. [http://www.iredmail.org/](http://www.iredmail.org/)
Quite good and nice web gui for administration. Package also installs spamassassin and clam anti-cirus along with fail2ban for added security.
Very easy to install too. [http://www.iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://www.iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)

---

### Post by Alireza_Zamani on 2014-10-31
> **sandyd said:**
> Before I continue, note that Ubuntu 10.04 will no longer be supported in April 2015 next year.

Try (in this order)
Postfixadmin
Axigen
iRedMail

Postfixadmin would be the only one out of the three that can be easily installed without installing additional software other than postfix (iRedMail includes clamav, etc ,etc). However, I have found iRedMail quite complicated to upgrade.
Axigen uses its own software.

I have removed Zimbra from the list as it uses 2G RAM and is probably overkill


good

---

