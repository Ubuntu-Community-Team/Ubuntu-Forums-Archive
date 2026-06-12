---
title: "How to send mail by commandline"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by dvks on 2013-03-19
I have Ubuntu 12.10 with mailutils and postfix packages installed. I tried the following command line ==>    mail -s "subject .... "    [EMAIL="name@domain.com"]name@domain.com[/EMAIL]       but it fail to send out the mail where [EMAIL="name@domain.com"]name@domain.com[/EMAIL] is my email address carried by google.  Can anyone help with the complete installation & setup required for the mail command line to work on Ubuntu 12.10?

---

### Post by SeijiSensei on 2013-03-19
Use "sudo more /var/log/mail.log" to see what errors might have occurred.  You can also use "mail -v" to have the program display what it is doing as it tries to send the message.

---

### Post by dvks on 2013-03-19
Thanks for your feedback, I checked /var/log/mail.log and there is no such file on my system, and the -v suggest me to check help for valid options. Any idea what is going on here?

---

### Post by rich4421972 on 2013-03-19
It might be that your main.cf  file has not been adjusted to send the log files

How is your postfix server configured and what is the content of you main.cf file?  You need to adjust your main.cf file to tell the program where to send error messages and returned email messages. In ubuntu 12.10, this file is in /usr/share/postfix. Once you adjust your config file,  You can see your recorded log files with the verbose option. 


code:
> postfix  -vc  /usr/share/postfix/main.cf [command] 

---

### Post by dvks on 2013-03-19
rich thanks for your help, in fact I didn't do any configuration for postfix and never used postfix, what I really need is to be able to send mail messages from command line so: 1. do I need postfix configured or mailutils can do it without postfix? 2. If I need to configure postfix beyond the 2-3 questions that were asked during the setup can you give me some directions or if it is simple the complete minimum set of details for such configuration. again, at this point I need to be able to send mail from command line as soon as possible and prefer a more robust setting later on.

---

### Post by rich4421972 on 2013-03-19
Have you thought about a more user-friendly system like Alpine? Unlike postfix, Alpine was made for those of us with less experience and does not require the hand-editing of configuration files (You configure the account settings from within the program). you can get alpine through the ubuntu ("universe")  apt repositories, and, if you're online, there are easy to understand instructions at 

[http://www.washington.edu/alpine/](http://www.washington.edu/alpine/)

[http://www.washington.edu/pine/tutorial.4/](http://www.washington.edu/pine/tutorial.4/)

Alpine is the current version of the old University of Washington program, PiNE (Pine is Not Elm). It stands for something else these days. There are other mail clients out there, but alpine is considered to be "beginner-friendly" and I have always liked it, myself. I guess it makes sense that a program used in colleges would be somewhat easy to understand

alpine is completely text-based but has menus and places where you can compose a message and send it. There is another easy to read   HOWTO for alpine at

[https://howto.ccs.neu.edu/howto/mail/configuring-alpine/](https://howto.ccs.neu.edu/howto/mail/configuring-alpine/)

There is also a mail client built into EMACS, but pine is much easier. I hope that some of this helps.

---

### Post by dvks on 2013-03-19
rich, thanks again for the information, I will check alpine later. However I hope you can help with my immediate problem which is specifically to get the "mail" command to work, and I am not sure I even need to setup postfix or only some settings for mailutils. I appreciate any help or information regarding: 1. which packages I need to setup so "mail" command will work. 2. If possible get instructions on such settings. 3. Does alpine implement the "mail" command line? Thanks for your help.

---

### Post by sanderj on 2013-03-20
If you just want "send mail by commandline" like your subject says, and you have a default smart host (=SMTP server, from your ISP or Gmail for example), consider the CLI tool 'mailsend' from [http://www.muquit.com/muquit/software/mailsend/mailsend.html](http://www.muquit.com/muquit/software/mailsend/mailsend.html)

Works for me.

HTH

---

### Post by dvks on 2013-03-20
Sanderj thanks for your feedback, I am specifically interested in making the MAIL command work any information regarding packages that are required or related settings will be helpful.

---

### Post by sanderj on 2013-03-20
> **dvks said:**
> Sanderj thanks for your feedback, I am specifically interested in making the MAIL command work any information regarding packages that are required or related settings will be helpful.

And what do you mean with "making the MAIL command work "? Send mail? Receive mail? Multiple users? Mail with outside world? Your own domain?

---

### Post by schragge on 2013-03-20
To send mails from command-line the *mail* command alone is not enough. You also need a properly configured mail transfer agent (MTA). It doesn't have to be a full-fledged MTA like sendmail, postfix, or exim4. If all you want is getting mails off your system then you can use a simple relay-only MTA like *ssmtp*, *esmtp*, *msmtp-mta*, or *nullmailer*.

Alternatively, use something like [sendEmail](http://manpages.ubuntu.com/manpages/precise/en/man1/sendEmail.1.html) or mentioned above *mailsend* instead of mail/mailx.

---

### Post by dvks on 2013-03-20
Sorry, you are correct, I need to have the following command line to work properly-         echo "mail body........" | mail -s "mail subject...."   [EMAIL="username@domain.com"]username@domain.com[/EMAIL]            if required by destination mail server we can add the   -aFrom:senderuser@localdomain   too.  the mail should go out of our local domain through ISP connection to any external mail address.

---

### Post by sanderj on 2013-03-20
> **dvks said:**
> Sorry, you are correct, I need to have the following command line to work properly-         echo "mail body........" | mail -s "mail subject...."   [EMAIL="username@domain.com"]username@domain.com[/EMAIL]            if required by destination mail server we can add the   -aFrom:senderuser@localdomain   too.  the mail should go out of our local domain through ISP connection to any external mail address.

And why don't you use mailsend for that?

No, let me rephrase that: what is your **functional **requirement? 

If your functional requirement is: "I want to send a mail from my system, with a certain from-address, with a certain (external) to-address, via a defined SMTP server, and possibly with an attachment" ... I would advice mailsend.

If your functional requirement is "I want to use the 'mail' command line fuction", my question would be: Why?

---

### Post by dvks on 2013-03-20
sanderj & schragge thanks for your time
1. I need the "mail" to work since I need to resolve the send mail problem on a system that I am not too much familiar with and I know that they are using the "mail" command in their scripts, I prefer to fix mail instead of searching and changing the scripts.
2. I understand from achragge that actually I will solve the problem by setting any MTA that can send mail, this is good.
    a. Can you recommend a "simple" MTA that can be used to send mail through ISP connection 
    b. which of - ssmtp, esmtp, msmtp-mta, or nullmailer, or other should I choose, better one with good setting instructions.
    c. Any detailed instructions on setting of the MTA for sending out mail through ISP connection?
Thanks

---

### Post by sanderj on 2013-03-20
> **dvks said:**
> sanderj & schragge thanks for your time
1. I need the "mail" to work since I need to resolve the send mail problem on a system that I am not too much familiar with and I know that they are using the "mail" command in their scripts, I prefer to fix mail instead of searching and changing the scripts.
2. I understand from achragge that actually I will solve the problem by setting any MTA that can send mail, this is good.
    a. Can you recommend a "simple" MTA that can be used to send mail through ISP connection 
    b. which of - ssmtp, esmtp, msmtp-mta, or nullmailer, or other should I choose, better one with good setting instructions.
    c. Any detailed instructions on setting of the MTA for sending out mail through ISP connection?
Thanks

I believe recommendations have already been given. Often there is wizard during the "sudo apt-get install". You should choose "smart host" and then select the local (or ISP) relay host.

It was in the 90's that I did setup sendmail configs ... I'm so glad that I don't do that anymore ... ;)

---

### Post by dvks on 2013-03-20
I will try to set MTA and hope everything will start working.
Appreciate you help
Thanks

---

### Post by schragge on 2013-03-20
Well, there are lots of online sources on how to configure mentioned MTAs. E.g.

[list]
[*][http://wiki.debian.org/sSMTP](http://wiki.debian.org/sSMTP)
[*][https://wiki.archlinux.org/index.php/SSMTP](https://wiki.archlinux.org/index.php/SSMTP)
[*][http://code.google.com/p/google-gadgets-for-linux/wiki/MSMPTQuickStart](http://code.google.com/p/google-gadgets-for-linux/wiki/MSMPTQuickStart)
[*][http://msmtp.sourceforge.net/documentation.html](http://msmtp.sourceforge.net/documentation.html)
[*][https://wiki.archlinux.org/index.php/Msmtp](https://wiki.archlinux.org/index.php/Msmtp)
[*][http://undesigned.org.za/2007/11/22/nullmailer-a-developers-best-friend](http://undesigned.org.za/2007/11/22/nullmailer-a-developers-best-friend)
[*][http://www.untroubled.org/nullmailer/HOWTO](http://www.untroubled.org/nullmailer/HOWTO)
[*][http://esmtp.sourceforge.net/doc.html](http://esmtp.sourceforge.net/doc.html)
[/list]

---

### Post by dvks on 2013-03-20
schragge,
Thanks for the information

---

### Post by sanderj on 2013-03-20
OK ... I didn't want to do this, but I did:

**Setup Postfix:**

```
sudo apt-get install postfix
```

Fill out the wizard:
- choose "Internet with smart host"
- fill out FQDN of your host
- fill out your (ISP's) smart host

Ready

**Set hostname with a FQDN name:**

```
sudo nano /etc/hostname
```

Fill out a resolvable FQDN of your host. I choose a name of remote system / domain I own.
Save and exit
Reboot your system


**Install and use 'mail':**

```
sudo apt-get install mailutils

echo Hello | mail -s "this is a test" yourmailaddress@gmail.com
```


... and ... bingo! It works for me

HTH

---

### Post by dvks on 2013-03-20
Sanderj,
Thanks for doing the extra steps and checking the setup
I will follow your instructions
Your feedback is very useful to me
Thanks again

---

### Post by dvks on 2013-03-20
It took me additional 2 hours and the following links to finally get postfix start sending mail through gmail.
It was mainly settings of the account authentication that prevented sending out the emails, You may check the following links for details:
[https://wiki.amahi.org/index.php/Gmail_As_Relay_On_Ubuntu](https://wiki.amahi.org/index.php/Gmail_As_Relay_On_Ubuntu)
[http://yaui.me/postfix-gmail-smtp-server-relay-ubuntu/](http://yaui.me/postfix-gmail-smtp-server-relay-ubuntu/)
[http://askubuntu.com/questions/228938/how-can-i-configure-postfix-to-send-all-email-through-my-gmail-account](http://askubuntu.com/questions/228938/how-can-i-configure-postfix-to-send-all-email-through-my-gmail-account)

The last link have a critical component that without it I couldn't get the authentication with gmail to work!

You need to enable TLS in Postfix's SMTP client, since Google requires it. This is indicated by them in the message "Must issue a STARTTLS command".
In /etc/postfix/main.cf you want something like this:
smtp_tls_policy_maps = hash:/etc/postfix/tls_policy

and then in /etc/postfix/tls_policy:
[smtp.gmail.com]:587 encrypt

where the  "[smtp.gmail.com]:587"   part must be identical to the "relayhost" entry in main.cf file

and you must run postmap on the policy file:
sudo postmap hash:/etc/postfix/tls_policy

now, finally after additional 2 hours of search and trial I have postfix and mailutils sending out emails, 
I hope this may help others too.

---

