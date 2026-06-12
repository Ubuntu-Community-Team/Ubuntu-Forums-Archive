---
title: "PHP mail function"
date: 2010-01-21
forum: Programming Talk
---

### Post by jtrulen on 2010-01-21
Greetings,

I am trying to use the mail() function using PHP. The page says it succeeds, however no mail comes through. Any suggestions?

I have lampp installed and running, but other than that I do not know.

Thank you,

Jordan Trulen

---

### Post by korvirlol on 2010-01-21
Do you have a MTA (mail transfer agent) like postfix installed and configured correctly?

---

### Post by jtrulen on 2010-01-21
I have sendmail.

I've never done any of this before and am fairly new to ubuntu, so i don't exactly know what/how to configure things yet.

---

### Post by korvirlol on 2010-01-21
if you use the mailx command on the terminal can it send mail to external mail addresses?

man mailx

If you can do this, then you likely havent setup the sendmail path in /etc/php5/apache2/php.ini

also, you can check /var/log/mail for any more hints as to why php does not send your mail.

---

### Post by s.fox on 2010-01-21
Hi,

Just to confirm nothing is wrong with the script you are using can you please post it?

Just to rule that problem out :)

-Silver Fox

---

### Post by jtrulen on 2010-01-21
I followed some other guides that help me set up the path, and my logfile contains:

Jan 21 11:46:20 pdcdc-lnxsvr1 sendmail[20297]: o0LHkKot020297: from=nobody, size=98, class=0, nrcpts=1, msgid=<201001211746.o0LHkKot020297@pdcdc-lnxsvr1.cabelas.corp>, relay=nobody@localhost

Jan 21 11:46:20 pdcdc-lnxsvr1 sm-mta[20298]: o0LHkKR9020298: from=<nobody@pdcdc-lnxsvr1.cabelas.corp>, size=345, class=0, nrcpts=1, msgid=<201001211746.o0LHkKot020297@pdcdc-lnxsvr1.cabelas.corp>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]

Jan 21 11:46:20 pdcdc-lnxsvr1 sendmail[20297]: o0LHkKot020297: to=jtrulen@cabelas.com, ctladdr=nobody (65534/65534), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30098, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (o0LHkKR9020298 Message accepted for delivery)

Jan 21 11:46:21 pdcdc-lnxsvr1 sm-mta[20300]: STARTTLS=client, relay=mail2.cabelas.com., version=TLSv1/SSLv3, verify=FAIL, cipher=AES128-SHA, bits=128/128

Jan 21 11:46:21 pdcdc-lnxsvr1 sm-mta[20300]: o0LHkKR9020298: to=<jtrulen@cabelas.com>, ctladdr=<nobody@pdcdc-lnxsvr1.cabelas.corp> (65534/65534), delay=00:00:01, xdelay=00:00:01, mailer=esmtp, pri=120345, relay=mail2.cabelas.com. [64.47.54.93], dsn=2.0.0, stat=Sent (<201001211746.o0LHkKot020297@pdcdc-lnxsvr1.cabelas.corp> Queued mail for delivery)

---

### Post by jtrulen on 2010-01-21
```
mail( $recipient, $subject, $message, "From: $sender" );
```

I just get some input from an HTML document to populate the variables in the above code.

---

### Post by Hellkeepa on 2010-01-21
HELLo!

The "mail ()" function works, but it seems like you have some issues with delivering the mail to the external MTA. I suspect the lack of headers being the main reason.
Also, the one line you posted doesn't give us any of the information we need, you have to post the entire code that recieves, and manages the input from the form. That way we can point out if there's something lacking, or anything wrong with it.

Happy codin'!

---

### Post by jtrulen on 2010-01-21
```
<?php
    $recipiant = $_POST['target_email'];
    $subject = $_POST['subject'];
    $message = $_POST['message'];
    $sender = $_POST['sender_email'];

    mail( $recipiant, $subject, $message, "From: $sender" );
?>
```

---

### Post by Hellkeepa on 2010-01-21
HELLo!

You have a complete lack of security there, I see... You have to validate the input before using it, otherwise it's a prime target for spammers to highjack your script. Especially since you let them set the sender manually, this is an open invitation to having people set the headers to whatever they want. And I mean *whatever*.
I recommend you to either have a look at my [validation functions](http://norskwebforum.no/pastebin/7609), or use the built-in filters.

Also, you might want to add some headers in there, to make the mail a bit more legit. Most likely it'll hit the spam filters quite hard, as it is now.

Happy codin'!

---

### Post by korvirlol on 2010-01-21
> I recommend you to either have a look at my [validation functions]("http://norskwebforum.no/pastebin/7609"), or use the built-in filters.


that there is a pretty neat link!

---

### Post by jtrulen on 2010-01-22
Understood. Currently, I am merely working on getting it to function correctly at the moment. As I am in a testing environment where I am the only user, I am not worried about security at this point.

But thank you, once I am done testing, I will definitely be looking at the link seriously.

---

### Post by Hellkeepa on 2010-01-22
HELLo!

Actually, security isn't something that lends itself to be tacked on at the end, but is a process that must be applied from the start. It'll not only make your apps safer, but it'll also save you a lot of work rewriting stuff.

**korvirlol**: Thank you. :-)

Happy codin'!

---

### Post by jtrulen on 2010-01-22
You seem to misunderstand me. This is merely a test scenario. I am doing this ti find the flaws in our server so that when I do write the actual page, i will be able to know beyond a shadow of a doubt that the mail() function works, and if nothing is being sent, then it with my code.

That is what I need assistance with. Figuring out why I am unable to send a simple email using the mail() function in a simplistic test environment that will go no further than to verify that the component works.

---

### Post by Hellkeepa on 2010-01-23
HELLo!

Since the mails made it to your mail queue, the "mail ()" function works. The problem in this case seems to lie with your MTA, which doesn't seem to be able to relay your mail to the external MTA.
This may be mitigated by setting the correct headers for your mail, and here are the ons I recommend setting:
[php]"From: $Sender <$FromMail>\n".
	"Reply-To: $Sender <$FromMail>\n".
	"Return-Path: ".MAIL_ABUSE."\n".
	"Organization: ".ORG_NAME."\n".
	"Content-Type: text/plain; format=flowed; delsp=yes; charset=utf-8\n".
	"MIME-Version: 1.0\n".
	"Content-Transfer-Encoding: 7bit\n".
	"User-Agent: PHP-mailer v{$PHP_VERSION}\n";
[/php]
Last line can be changed to whatever you prefer.

Happy syncin'!

---

### Post by jtrulen on 2010-02-01
I have added in the headers you have suggested, however still no go. Although after about 4 hours, my log files show a timeout error.

Any ideas?

---

### Post by Hellkeepa on 2010-02-01
HELLo!

As I previously have stated: There is nothing wrong with your PHP code, it is your MTA which is malconfigured for sending external mails. The timeout in the mail logs confirm this.

Happy codin'!

---

### Post by jtrulen on 2010-02-01
Alright, any websites you can point me to to properly configure the MTA?

---

### Post by Hellkeepa on 2010-02-01
HELLo!

You should be able to find some guides in this search:
[http://www.google.no/search?client=opera&rls=en-GB&q=sendmail+external+mta&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.no/search?client=opera&rls=en-GB&q=sendmail+external+mta&sourceid=opera&ie=utf-8&oe=utf-8)
The second one, from StackOverflow, might be worth looking into. other than that I recommend asking in the server section here at the fora.

Happy codin'!

---

### Post by CyberJack on 2010-02-01
I can't help you with sendmail but I have written a small guide on how to setup postfix (relay) and let php send mail.
If you can't get sendmail to work, I'm happy to help with postfix.

---

### Post by jtrulen on 2010-02-02
I guess I'll give postfix a try considering everything I try with sendmail does not work.

---

### Post by CyberJack on 2010-02-04
Ok, here is how I got php to send mail using postfix. This guide was created using ubuntu 9.04.
In my case my isp required a username and password before i could send mail.
If your isp does not require a username and password I guess you can skip step 3 to 7.

[LIST=1]
[*]Install Postfix and sasl
```
sudo aptitude install postfix libsasl2 ca-certificate libsasl2-modules
```
[*]During the postfix installation you will be asked a few questions.
There where my answers:
```
Server configuration: Satellite system
Mail name           : [Your domain name for example: example.com]
relay host          : [Your isp relay host]
root and postmaster : [empty]
final destination   : [Remove you domainname but leave the rest]
Forced              : no
Network blocks      : [all default]
limit               : 0
local address       : *
IP                  : all
```
[*]After the postfiux installation add th following lines to the "/etc/postfix/main.cf" file above the "myhostname" part.
```
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
```
[*]Create the file "/etc/postfix/sasl_passwd" (as root) and add the following lines:
```
[Your isp relay host] [username]:[password]
```
[*]As the file contains your mail username and password make sure the file is only readable by the root user
```
sudo chown root:root /etc/postfix/sasl_passwd && sudo chmod 600 /etc/postfix/sasl_passwd
```
[*]Create the postfix hash db file
```
sudo postmap /etc/postfix/sasl_passwd
```
[*]Reload the postfix config
```
sudo /etc/init.d/postfix reload
```
[*]Modify you php.ini and change the ;sendmail part
```
sudo vim /etc/php5/apache2/php.ini
change: ;sendmail_path
to: sendmail_path = /usr/sbin/sendmail -i -t
```
[*] Restart apache, and try to mail
```
sudo /etc/init.d/apache2 restart
```
[/LIST]

If there are thing wrong about my list please let me know.

---

