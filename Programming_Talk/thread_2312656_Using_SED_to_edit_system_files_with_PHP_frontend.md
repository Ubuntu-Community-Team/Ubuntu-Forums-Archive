---
title: "Using SED to edit system files with PHP frontend"
date: 2016-02-06
forum: Programming Talk
---

### Post by kunal2shgmail.com on 2016-02-06
Hello friends,

Is it possible to use Sed to edit ubuntu system parameters such as hostname or net work config?
And if yes how can php/html5 be used as a front end with sed in a script to change the above required parameters?

Thanks in advance
K

---

### Post by SeijiSensei on 2016-02-06
1) Yes, but it's a pain in the neck.  Are you trying to automate these edits?

2) No.  Apache runs as an ordinary user called "www-data" and cannot make changes to root-owned files like /etc/hosts.

---

### Post by kunal2shgmail.com on 2016-02-06
> **SeijiSensei said:**
> 1) Yes, but it's a pain in the neck.  Are you trying to automate these edits?

2) No.  Apache runs as an ordinary user called "www-data" and cannot make changes to root-owned files like /etc/hosts.


Hey thanks for the prompt reply, I am not trying to automate these edits. We have a mail server web admin panel that we are building. 
Yes i know there is tools like web min but since we are uni students, the challenge was welcome. We have completed most of the we admin 
portal. We wanted a way to edit system hostname so that the terminal doesn't have to be used by the user. They could use the web admin 
portal to change the host name along with vital system settings such as the network config e.t.c

Yes apache runs under www-data, but isn't is okay to to add it to the sudoers file with SPECIFIC privileges (not all privileges but lets say only run specific scripts e.t.c?

Sorry for the many questions, Thanks in advance.
K

---

### Post by matt_symes on 2016-02-06
Hi

> **kunal2shgmail.com said:**
> Hey thanks for the prompt reply, I am not trying to automate these edits. We have a mail server web admin panel that we are building. 
Yes i know there is tools like web min but since we are uni students, the challenge was welcome. We have completed most of the we admin 
portal. We wanted a way to edit system hostname so that the terminal doesn't have to be used by the user. They could use the web admin 
portal to change the host name along with vital system settings such as the network config e.t.c

Thanks for expanding on why you want to edit system files.

> Yes apache runs under www-data, but isn't is okay to to add it to the sudoers file with SPECIFIC privileges (not all privileges but lets say only run specific scripts e.t.c?

This is possible but is a potential (and very real security) risk.

Is the web panel Internet facing ? What verification of the web panel user are you doing ? What validation of the input are you performing ?

What system files do you want to allow the web panel to edit and what other system functionality do you want to give this web panel ?

Kind regards

---

### Post by kunal2shgmail.com on 2016-02-07
> **matt_symes said:**
> Hi



Thanks for expanding on why you want to edit system files.



This is possible but is a potential (and very real security) risk.

Is the web panel Internet facing ? What verification of the web panel user are you doing ? What validation of the input are you performing ?

What system files do you want to allow the web panel to edit and what other system functionality do you want to give this web panel ?

Kind regards

Hello! Yes, It is going to be internet facing and also its a panel to administer the web server, we are students so we are then soon planning to release it as a script as well for people to use with their postfix + dovecot setup. We are using session id's to store the user that is logged in along with a time out, so if the user in active say for x minutes, they get automatically logged out. Also we have used php to check against the SQL database for the username and password, the passwords are encrypted using blow fish. We need the web panel to do basic system editing such as change the hostname of the system so that terminal doesn't have to be used, by changing the hostname the mail server can perform as it has to. Along with that we would like to let the user also change the network configuration such as DNS and IP address of the system.

PS: I was told that the above can be accomplished using CGI ? I have no idea how that would work but input would be appreciated

Please do ask for more details if required, once again thanks in advance to all the forum members that have taken time out to help :)

---

### Post by matt_symes on 2016-02-07
Hi

> Also we have used php to check against the SQL database for the username and password, the passwords are encrypted using blow fish

Don't encrypt your passwords in the database, crypto hash them and use an algorithm were you can set a variable number of iterations ! bcrypt and PBKDF2 are becoming  popular at the moment.

[https://en.wikipedia.org/wiki/Cryptographic_hash_function](https://en.wikipedia.org/wiki/Cryptographic_hash_function)

That's pretty basic. 

I don't want to pour cold water on your idea but have you really though through the security implications of your idea ?

See what others think.

Kind regards

---

### Post by kunal2shgmail.com on 2016-02-07
> **matt_symes said:**
> Hi



Don't encrypt your passwords in the database, crypto hash them and use an algorithm were you can set a variable number of iterations ! bcrypt and PBKDF2 are becoming  popular at the moment.

[https://en.wikipedia.org/wiki/Cryptographic_hash_function](https://en.wikipedia.org/wiki/Cryptographic_hash_function)

That's pretty basic. 

I don't want to pour cold water on your idea but have you really though through the security implications of your idea ?

See what others think.

Kind regards

Hello,

No worries about the valuable input, I am here to learn so I am glad to have this security vulnerability pointed out to me! Yes we will look in to the cryptographic hash function. Any idea about implementing the hostname changes? (as it is thats where we are stuck and regarding the crypto hash, I am sure with more research my team and I can definitely figure out the ultimate solution :)

---

### Post by SeijiSensei on 2016-02-08
I don't understand why you want to let people change the hostname.  Usually that is a fixed characteristic of the machine.  Perhaps you can explain what you mean by "change the hostname."  I honestly cannot see any reason to let users do that.  Besides, if the machine is listed in DNS, you absolutely do not want to let people change the hostname.

---

### Post by matt_symes on 2016-02-08
Hi

> **SeijiSensei said:**
> I don't understand why you want to let people change the hostname.  Usually that is a fixed characteristic of the machine.  Perhaps you can explain what you mean by "change the hostname."  I honestly cannot see any reason to let users do that.  Besides, if the machine is listed in DNS, you absolutely do not want to let people change the hostname.

Agreed.

Can you list what system files you want to change and why ?

Kind regards

---

