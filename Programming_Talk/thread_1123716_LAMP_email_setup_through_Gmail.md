---
title: "LAMP email setup through Gmail"
date: 2009-04-12
forum: Programming Talk
---

### Post by Beezleray on 2009-04-12
Hello, I've looked all over for tutorials and I can't seem to find one that doesn't just confuse me, I'm looking for a way to set-up my lamp server to send email to and from a gmail account. If anyone can direct me to a simple guide or walk me through it here that would be great!

Thanks.

(Running Ubunutu 8.10 btw)

---

### Post by Reiger on 2009-04-12
That is because it is not [neccesarily] the job of a LAMP stack to handle mail traffic (instead it does HTTP traffic); however there are plenty of mail-server packages out there which will get you up and running in no time. IMAP is the most feature rich `common' mail protocol, SMTP is a lot more basic (called Simple for a reason).

Then, set your server to forward all outgoing mail to smtp.gmail.com (just like your current e-mail client would), and set your Gmail account to forward all incoming e-mail to your mail server.

---

### Post by odyniec on 2009-04-12
> **Reiger said:**
> IMAP is the most feature rich `common' mail protocol, SMTP is a lot more basic (called Simple for a reason).

Note that IMAP and SMTP serve two different purposes, so saying that one is more feature-rich than the other is like comparing apples and oranges.

OP, could you provide some more details on what you're trying to accomplish? Do you want to setup your e-mail server to relay messages through Gmail?

This is off-topic here in the programming section, by the way.

---

### Post by Beezleray on 2009-04-12
> **odyniec said:**
> 
OP, could you provide some more details on what you're trying to accomplish? Do you want to setup your e-mail server to relay messages through Gmail?


I just need to relay the email from my LAMP server through gmail to its destination. I guess I need to set up a SMTP server to do this? I need to send emails for a PHP class I'm taking but my professor doesn't know squat about Linux. The only thing i've been able to find so far is changing the sendmail_path in php.ini beyond that I have no idea.

Sorry if this is in the wrong place.

---

### Post by odyniec on 2009-04-12
Ok, just to make sure we're clear -- at this moment, is your server set up to send any mail? For example, are you able to send messages from the command line?

If it is, are you sure you need to use Gmail SMTP server to relay mail? This is only necessary if you know the destination won't accept messages coming directly from your server (eg. if your IP address is blacklisted).

If you do need to relay mail through an external host, then you have to properly set up your SMTP server. When relaying through Gmail, you need a Gmail account, and your server must be configured to use the account for authentication. Here's one decent tutorial on setting it up in Ubuntu:
[http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps](http://behindmyscreen.newsvine.com/_news/2006/12/31/501615-configuringubuntu-postfix-and-gmail-in-101-easy-steps)

---

### Post by Reiger on 2009-04-12
> **odyniec said:**
> Note that IMAP and SMTP serve two different purposes, so saying that one is more feature-rich than the other is like comparing apples and oranges.

OP, could you provide some more details on what you're trying to accomplish? Do you want to setup your e-mail server to relay messages through Gmail?

This is off-topic here in the programming section, by the way.

Doh! I should quite writing multiple posts at the same time, it plays weird copy/cut/paste tricks on you...

@OP: SMTP is Simple Mail Transfer Protocol which is only for `forwarding' mail between servers. So you'd be looking to set up an SMTP stack on your own server.

Well if you are not going to use `massive' volumes of e-mail traffic (i.e. only occasional status updates or critical log messages); you could alternative set up & configure a command line e-mail client and feed it input from PHP, parse its output and use that within your app as well.

For purely sending e-mail it is possible to simply use the mail() function:
[http://nl2.php.net/manual/en/function.mail.php](http://nl2.php.net/manual/en/function.mail.php).

---

### Post by aaronp on 2009-04-13
> For purely sending e-mail it is possible to simply use the mail() function:
[http://nl2.php.net/manual/en/function.mail.php](http://nl2.php.net/manual/en/function.mail.php). 

Does the php mail function allow you to use gmail as the smtp server? I believe gmail requires authenication to send mail so you would not be able to use mail() to achieve this as it doesn't support authentication with the smtp server.

Maybe take a look at the PEAR package in php - I believe you can use it to specfy and authenticate with any smtp server (i.e. gmail)

Take a look here for a nice explanation:

[http://www.developer.com/open/article.php/10930_3782831_1](http://www.developer.com/open/article.php/10930_3782831_1)

or here for the details of that PEAR mail package:

[http://pear.php.net/package/Mail/](http://pear.php.net/package/Mail/)

hth
Aaron

---

### Post by Beezleray on 2009-04-13
Thanks everyone for you help, I set up Pear and that does exactly want I want.

---

### Post by aaronp on 2009-04-13
no problems ;-)

---

### Post by tturrisi on 2009-04-14
If needed & wanted for a home server, you can also install exim & set it up as a smarthost and use gmail as the smtp relay if your isp filters port 25.

---

