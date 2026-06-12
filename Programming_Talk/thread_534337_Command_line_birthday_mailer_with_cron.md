---
title: "Command line birthday mailer with cron"
date: 2007-08-25
forum: Programming Talk
---

### Post by stefanborremans on 2007-08-25
Hello,

I have completely switched to Ubuntu for about half a year now. And I'm very happy with it. But since my windows server had a hardware failure, I also have installed ubuntu on it. 

On my windows server I had a custom written program that I called birthday mailer. Basicly it opened an access database, looked in the list if it was anyone's birthay, and sent an email to myself for each person that has his birthday.

What i'm trying to do now is making the same program on my ubuntu system. I have done some research that I need cron to do a job each night. So that seems quite similar to scheduled tasks.

The first problem I face is, how can I send emails from the terminal command line? I have found that I can use the command MAIL for it, so I tried it, no luck. And I could not find any logfiles, this is the script I used:

```

#!/bin/bash
# script to send simple email
# email subject
SUBJECT="Verjaardagsmail"
# Email To ?
EMAIL="xxx@xxx.xxx"
# Email text/message
EMAILMESSAGE="/tmp/emailmessage.txt"
echo "This is an email message test">$EMAILMESSAGE
echo "This is a second line">>$EMAILMESSAGE
echo "This is a third line">>$EMAILMESSAGE
# send an email using /bin/mail
/usr/bin/mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE

```

So my questions are:

[LIST]
[*]Where do I find the postfix or mail log files?
[*]I'm using bash now, is there a better way to program this application?
[/LIST]

All suggestions are more than welcome.

Stefan

---

### Post by apetresc on 2007-08-25
It's probably easier to use a Python script. For example, [check here](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/67083) for a Python script that can send multipart plaintext/HTML e-mails. Just fill in your own SMTP server, recipients, etc, and use.

---

### Post by brcre on 2007-09-12
[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)  <- This answered the questions I had about a similar type problem.  What I wanted to do was set up a crontab that would send an email to my roommate as a bill reminder for shared bills.  However I couldn't get the email part of the crontab working and have been searching for the answer.

I'm using gmail and Ubuntu 7.04 and I use Evolution for normal emailing tasks
The short answer for me was this:
Most of the programs were already installed these are what I lacked:

sudo apt-get install ssmtp
sudo apt-get install mailutil

Configure the ssmtp:  /etc/ssmtp/ssmtp.conf
root=your-user-name@gmail.com         # Your email address
mailhub=smtp.gmail.com:587         # Address and port number to send mail to
UseSTARTTLS=YES                    # Send SSL/TLS messages to Gmail
AuthUser=user-name               # Your Gmail Username
AuthPass=password                  # Your Gmail Password
rewriteDomain=gmail.com            # So the message appears to come from Gmail
FromLineOverride=YES               # So the message appears to come from Gmail
hostname=localhost.localdomain     # Hostname: use hostname -f in a Terminal

at this point I haven't figured out how to send mail only using ssmtp (i.e. ssmtp -s Test [email]email-address@server.com[/email] <enter>
but I can use the mail program you have listed in your program to do it for me:
mail -s Test [email]email-address@server.com[/email] $EMAILMESSAGE

I new the moment I got the config file set up correctly that things were working because all the test messages I'd been writing while figitting with this finally got processed and my mail account got really busy all of a sudden!

By the way I loved the program you have written there, so I copied it and replaced mine with it.  It's a great improvement over the one I wrote.

---

