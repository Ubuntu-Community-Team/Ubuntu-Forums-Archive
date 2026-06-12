---
title: "How to send email using bash?"
date: 2007-03-02
forum: Programming Talk
---

### Post by mesh2005 on 2007-03-02
I tried mail -s 'subject' email but I didn't receive anything! I tried sendmail and I didn't receive anything too! Please help

---

### Post by azazel00 on 2007-03-02
sendmail should work. 

But it depends on having setup the mailboxes adequately (if I remember correctly). It's been like two years since I used sendmail (I was doing a Postfix install).

If you are trying to send an external email, you may have to do some configuring. (SMTP and stuff like that)

---

### Post by Mr. C. on 2007-03-02
The mail command relies on an MTA to send mail.  Sendmail is an MTA.  You can use either to handoff to sendmail, or talk directly to sendmail.

Either way, the system needs to be configure to relay mail.  If its not, the mail command will just drop your letter ino an outgoing queue, where it sits waiting.

If the system is not configure with an MTA, you'll need to use another (like your ISPs).

MrC

---

### Post by mesh2005 on 2007-03-03
so how to configure it to work ?

---

### Post by Mr. C. on 2007-03-03
Install and configure your MTA of choice (postfix, sendmail, ...).

Have you installed either of these ?

MrC

---

### Post by riotxix on 2008-03-17
Hi,

this had me perlexed for days. mail doesn't work, or give an error (unless I do it through my hosting company). Why? Because mail does not allow you to specify an smtp sever to relay your mail through, and unless you can go through the the grief of setting up you machine as a bonafide mail server, you're attempts will get rejected by the recepient as spam (without informing you).

Solution:
use nail, which does allow you to specify an smtp server to relay your mail through. You don't need to go through any sendmail config files.

[http://forums.fedoraforum.org/showthread.php?t=143690](http://forums.fedoraforum.org/showthread.php?t=143690)
"Rupert Pupkin"
<i>The problem with the standard 'mail' command is that it assumes that the machine it is running on is a full-fledged SMTP server. So unless you've configured your machine to be a bonafide mail server (or to act as an SMTP relay), then your mail will not go anywhere outside your machine (i.e. it will only work for addresses local to your machine, e.g. some_user@localhost). There is no way to specify an external SMTP server (like your ISP's) to use with the 'mail' command. That's why you're getting a dead letter.

If you want a command-line mailer that does support using an external SMTP server, then get nail from Fedora Extras. Nail supports specifying an external SMTP server. You can do this on a per-mail basis, like this:

nail -r "myaddress@something.com" -s "Some subject" -S smtp=some.smtp.server [email]info@company.com[/email] < msg.txt

or you can permanently set the SMTP server in your ~/.mailrc file (or /etc/nail.rc if you want to set it system-wide), which removes the need for using the "-S smtp=..." option on the command-line:

set smtp=some.smtp.server

See the nail man page for more details. In my opinion, no one should be using 'mail' anymore, nail is vastly superior."</i>

---

### Post by ruy_lopez on 2008-03-17
A lot of mail servers will reject mail unless it has a valid DNS PTR record. With postfix, failed attempts should appear in the logs.

---

