---
title: "mail server"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by ub007 on 2008-07-03
I got the following error when i tried installing a mail server
telnet mail.ubuntu.surrey.ac.uk 25
***error msg:couldnot resolve mail.ubuntu.surrey.ac.uk/25: Name or service....

What could be wrong here?

These r the steps followed:
sudo apt-get install postfix
sudo apt-get install mailx

sudo useradd -m -s /bin/bash fmaster
sudo passwd fmaster

testing it -all works fine: telnet localhost 25......(...su - fmaster
mail....)

Step 2)

sudo postconf -e "home_mailbox = Maildir/

sudo postconf -e "mailbox_command 

sudo /etc/init.d/postfix restart

Step 3)
sudo apt-get install courier-pop
sudo apt-get install courier-imap

sudo postconf -e "mydestination = mail.ubuntu.surrey.ac.uk, localhost.localdomain, localhost, ubuntu.surrey.ac.uk"

sudo postconf -e "mynetworks = 127.0.0.0/8, 192.168.1.0/24"
sudo postconf -e "inet_interfaces = all
sudo postconf -e "inet_protocols = all"
sudo /etc/init.d/postfix 

telnet mail.ubuntu.surrey.ac.uk 25
***error msg:couldnot resolve mail.ubuntu.surrey.ac.uk/25: Name or service....

Info on my network:
Its an intranet-6 pcs connected to a dell 5424 switch
Got Ubuntu server installed on 1 machine and thats where I have set up the mail server....For installing purposes I have unplugged this comp from the switch and plugged it into the uni n/w which got internet connection:

I have used surrey as an example.Also the ip that i get leased when i plug into the uni n/w is "131.'.'.'

could anyone tell me what configuration changes I need to make...
You would find the same post in server forum,plz ignore that..thought would post here as its a newbie question

Cheers
David

---

### Post by hyper_ch on 2008-07-03
```

ping mail.ubuntu.surrey.ac.uk

```

---

### Post by ub007 on 2008-07-03
Thanks mate,
I added ubuntu.surrey.ac.uk to /etc/hosts and it works fine...

---

### Post by hyper_ch on 2008-07-03
one just needs to read the error message... mostly they do give some strong hint on what's wrong ;)

---

