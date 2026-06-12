---
title: "Beginner's confusion"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by eawz9999 on 2012-02-13
I have an Ubuntu 11.04 Natty running a home server with a dynamic IP. I set up ssmtp as a simple communicating tool to my ISP smtp server. This works fine from the command line 'ssmtp [email]user@comcast.net[/email]'. This user is a system Ubuntu user who has an account at comcast.net
I also have a Joomla family page that send mail using sendmail without problem.
I cannot get my (root) crontab jobs to send mail. The mail error log is "Not our client", however from the command line the emails go through.
Where does the root crontab job get the senders name and password?
What am I doing wrong?:icon_frown:
Thank you, Enrique

---

### Post by androssofer on 2012-02-13
> **eawz9999 said:**
> I have an Ubuntu 11.04 Natty running a home server with a dynamic IP. I set up ssmtp as a simple communicating tool to my ISP smtp server. This works fine from the command line 'ssmtp [email]user@comcast.net[/email]'. This user is a system Ubuntu user who has an account at comcast.net
I also have a Joomla family page that send mail using sendmail without problem.
I cannot get my (root) crontab jobs to send mail. The mail error log is "Not our client", however from the command line the emails go through.
Where does the root crontab job get the senders name and password?
What am I doing wrong?:icon_frown:
Thank you, Enrique


Humm, does it need to be sent as root?

what happens when you send it using your own profiles crontab?

---

### Post by eawz9999 on 2012-02-13
No, it does not. I will create a crontab under another user's name and try.

---

### Post by eawz9999 on 2012-02-14
No go. Regardless of whose crontab is, I keep on getting the same message. "Not our costumer".
My confusion is that from the command line I can ssmtp from every account (the ssmtp has the correct settings). How could I tell cron to use ssmtp? And where is it getting the email information, (sender, password, etc)?

---

### Post by eawz9999 on 2012-02-14
I must be very close. I installed Cron-Apt and this program email me with the results of UPDATE with no problem.
It is still crontab that cannot do it.
I was looking into /etc/alternatives and found a link mailx

root@myserver:~# update-alternatives --display mailx
mailx - auto mode
  link currently points to /usr/bin/heirloom-mailx
/usr/bin/bsd-mailx - priority 50
  slave Mail: /usr/bin/bsd-mailx
  slave Mail.1.gz: /usr/share/man/man1/bsd-mailx.1.gz
  slave mail: /usr/bin/bsd-mailx
  slave mail.1.gz: /usr/share/man/man1/bsd-mailx.1.gz
  slave mailx.1.gz: /usr/share/man/man1/bsd-mailx.1.gz
/usr/bin/heirloom-mailx - priority 60
  slave Mail: /usr/bin/heirloom-mailx
  slave Mail.1.gz: /usr/share/man/man1/heirloom-mailx.1.gz
  slave mail: /usr/bin/heirloom-mailx
  slave mail.1.gz: /usr/share/man/man1/heirloom-mailx.1.gz
  slave mailx.1.gz: /usr/share/man/man1/heirloom-mailx.1.gz
/usr/sbin/ssmtp - priority 20
Current 'best' version is '/usr/bin/heirloom-mailx'.

I added the last line "/usr/sbin/ssmtp" which is probably wrong.
Enrique

---

### Post by androssofer on 2012-02-14
> **eawz9999 said:**
> No go. Regardless of whose crontab is, I keep on getting the same message. "Not our costumer".
My confusion is that from the command line I can ssmtp from every account (the ssmtp has the correct settings). How could I tell cron to use ssmtp? And where is it getting the email information, (sender, password, etc)?

when you run from command line what do you type? (remove any sensitive stuff like passwords)

and describe what happens after you hit enter.. any output that shows up, or windows that open...

---

### Post by eawz9999 on 2012-02-14
I type ssmtp [email]dest@comcast.net[/email] < email

the file email contains:

To:  [email]dest@comcast.net[/email]
Subject: Ubuntu Server
From:  [email]sender@comcast.net[/email]

Test of ssmtp in ubuntu

This email goes to my smtp.comcast.net with no problem and I get it in my win7 PC.

---

### Post by androssofer on 2012-02-14
> **eawz9999 said:**
> I type ssmtp [email]dest@comcast.net[/email] < email

the file email contains:

To:  [email]dest@comcast.net[/email]
Subject: Ubuntu Server
From:  [email]sender@comcast.net[/email]

Test of ssmtp in ubuntu

This email goes to my smtp.comcast.net with no problem and I get it in my win7 PC.

i take it your cron job is something like:

```
01 04 * * * ssmtp dest@comcast.net < email
```

is so perhaps we could make a script to do the work?

```
#!/bin/sh

ssmtp dest@comcast.net < email

```

then put that in the folder with your 'email' file (give it execution permission with: chmod +x scriptFile.sh). 

and run it from cron using the scriptFiles absolute path?

```
01 04 * * * /home/username/folder/scriptFile.sh
```

**note**; names and cron timings are for example purposes only, and i haven't tested the script...

---

### Post by eawz9999 on 2012-02-14
Would this be important?
In /etc/alternatives I don't have a MTA installed.

(CRON) error (grandchild #4800 failed with exit status 127)
Feb 14 10:30:01 myserver CRON[4798]: (CRON) info (No MTA installed, discarding output)

---

### Post by androssofer on 2012-02-14
> **eawz9999 said:**
> Would this be important?
In /etc/alternatives I don't have a MTA installed.

(CRON) error (grandchild #4800 failed with exit status 127)
Feb 14 10:30:01 myserver CRON[4798]: (CRON) info (No MTA installed, discarding output)

Code 127 indicates a 'command not found error', so my guess is thats its having trouble finding ssmtp.

so i did a bit of searching and found this:

[http://serverfault.com/questions/260731/what-minimal-smtp-client-will-allow-me-to-relay-cron-output-to-an-external-email](http://serverfault.com/questions/260731/what-minimal-smtp-client-will-allow-me-to-relay-cron-output-to-an-external-email)

it suggests using msmtp for your email needs

---

### Post by eawz9999 on 2012-02-14
Now this part works! Thank you Androssofer
0/2 * * * * /usr/sbin/ssmtp [email]dest@comcast.net[/email] < /email

I had to add the full paths.
Now beside the text in email file, I need to receive the results of my cron jobs. Basically databace backups, sync, firewall, etc


0 0 * * *        /usr/scripts/backupDB.sh
15 0 * * *       /usr/scripts/backupscript.sh
0 1 * * *        /usr/scripts/syncfiles.sh
30 1 * * *      /usr/scripts/countries_block.sh
0 2 * * *       /usr/sbin/ufw enable
10 2 * * *      /sbin/iptables-save > /etc/iptables.rules
20 2 * * *      /usr/scripts/refreshdlna.sh

# testing
0/2 * * * * /usr/sbin/ssmtp [email]dest@comcast.net[/email] < /email

---

### Post by eawz9999 on 2012-02-18
I spent 20 minutes to set up **SSMTP**. I was able to send emails from the command line. I spent 5 weeks trying to make it my default **MTA**. I could not find any guides on internet or anywhere else. Maybe it cannot be done or I don’t have sufficient knowledge.
Next it took me 3 days to setup **Postfix**, my main problem was to set up the generic database.
Now **Postfix** is working fine and sending me notifications of problems. Since I don’t need a full mail server, my **ISP** would not allow me to have one and port 25 is use for worms and viruses, I blocked port 25 on my router and on my **UFW**. I use port 587.
**Postfix** is a huge and complex program. To use it just to send notification appears to be too much but it is one that works for me.

---

