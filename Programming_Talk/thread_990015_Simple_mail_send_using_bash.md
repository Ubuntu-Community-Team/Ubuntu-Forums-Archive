---
title: "Simple mail send using bash"
date: 2008-11-22
forum: Programming Talk
---

### Post by hctopcu on 2008-11-22
I need a very lightweigt and simple script that will send reports as mail.
I have a mail server on another machine. I need the script use it. (Like using gmail smtp)
I googled and found nail but it turned out to be no more available in ubuntu repots.
I found others but they're all much more than I need for my dedicated mysql server.
I dont know what to use and how to configure.

---

### Post by raf_kig on 2008-11-22
Hi,

i would recommend using msmtp, its a pretty small smtp client and should suit all your needs.

Regards

raf

---

### Post by geirha on 2008-11-22
Have you looked at [apt://mailx](apt://mailx)?

---

### Post by drubin on 2008-11-22
This is what I use a simple perl(Ie almost all servers will have it installed by default) script but has many options.
[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

---

### Post by hctopcu on 2008-11-22
Thank you all.
Drubin I loved sendEmail!

---

### Post by drubin on 2008-11-22
> **hctopcu said:**
> Thank you all.
Drubin I loved sendEmail!

Pleasure it is the greatest simple script ever. I use that for CLI scripts because it means that my "dumb" servers do not need send mail installed.

---

