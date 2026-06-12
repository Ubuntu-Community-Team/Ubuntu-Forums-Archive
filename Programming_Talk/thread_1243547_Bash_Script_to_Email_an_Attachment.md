---
title: "Bash Script to Email an Attachment"
date: 2009-08-18
forum: Programming Talk
---

### Post by rbishop on 2009-08-18
All, 

Forgive me if this is a duplicate post, but I have not been able to find a complete answer as of yet.  I am working on a script to email a file, below is the code.  I am not sure what I am doing wrong so any help would be greatly appriciated.  I can get the email, however the file that I want to include as an attachment is not there, it only shows the path to it.

Thanks in advance for any help you guys and gals can provide.

```


#!/bin/bash
SUBJECT="Script Email"
TO="my@email1.com"
FROM="metoo@email2.com"
ATTACH="/backups/Listing.txt"

/usr/bin/mail -f ADDRESS [$FROM] -s "$SUBJECT" "$TO" -a FILE [$ATTACH] <<EOF


Time: `date`
EOF



```

---

### Post by ahmatti on 2009-08-18
I use sendEmail for this and it works fine and is in the repos. You can also specify an external SMTP server for it if you don't want to set up one yourself.

---

### Post by jpkotta on 2009-08-19
```
sudo apt-get install mutt
```
```
echo body | mutt -i additional_body.txt -s subject -a attachment.zip name@host.tld
```

---

### Post by lomash on 2009-09-29
I can run mutt from the command line to send an email, and it works fine:
echo 'This is the email text' | mutt -s 'Hello there' [email]name@someemail.com[/email]
 

If I run it from a php script, I get error message in the apache error log. This is how I run it from php:
exec("echo 'This is the email text' | mutt -s 'Hello there' [email]name@someemail.com[/email]");

This is the apache error log entry:
/var/www/sent: Permission denied (errno = 13)

I then created new folder /var/www/sent, chown it to www-data:www-data and 755 permission, and got this error log entry:
/var/www/sent is not a mailbox.

I checked /etc/Muttrc, but there is no entry with /var/www/sent, so I'm not sure where mutt is finding it from.
I couldn't find any other mutt config file in the system.

Why am I getting these errors and how to fix them? I did a lot of searching but couldn't find an answer. 

I am just trying to send an email from a php script, and not intending to setup mutt as my desktop email client. Most of the how-to's I came across were focusing on the latter. I want to use mutt from the script because it makes it much easier to send an attachment (well, I guess once I figure out how to send a simple email first)

TIA

---

### Post by diesch on 2009-09-29
I guess mutt wants to save the sent mail in ~/sent - and as mutt is run as www-data that is /var/www/sent.

Most likely there are better ways to send mails from PHP than using command line tools like mutt (but I don't know much about PHP).

---

### Post by kenene on 2009-11-12
Hi [lomash]("http://ubuntuforums.org/member.php?u=921313"),

After a lot of searching I found out a way to solve this problem. Mutt is indeed trying to save a copy of sent messages in the home directory of the user www-data. The copies are stored in the file '/var/www/sent'. You could either:

[LIST=1]
[*]add 'set copy=no' to the system wide configuration for Mutt (/etc/Muttrc). This setting tells Mutt not to bother to save a copy of sent messages. This will affect all users of the system.
[*]to avoid affecting all system users with the solution above, make an individual ~/.muttrc file for www-data. Add 'set copy=no' to this configuration file, and run mutt (as www-data) with the option -F to point to the special ~/.muttrc file for www-data.
[/LIST]
I found the solution at this link [http://www.mail-archive.com/nagios-users@lists.sourceforge.net/msg06536.html](http://www.mail-archive.com/nagios-users@lists.sourceforge.net/msg06536.html)

See also [http://markmail.org/message/23fgohiuxxegb3nm](http://markmail.org/message/23fgohiuxxegb3nm)

Greetings!

---

### Post by lomash on 2010-04-19
Thanks kenene for your research and reply.

I actually ended up writing a php script to send multipart email (for the attachment).
Althogh I didn't test your suggestion, I'm sure it works nicely.

---

