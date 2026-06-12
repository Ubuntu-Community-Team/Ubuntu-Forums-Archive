---
title: "How to verify TLS support in postfix"
date: 2007-07-05
forum: Outdated Tutorials &amp; Tips
---

### Post by vrillusions on 2007-07-05
I wanted to confirm that email sent using postfix as the smtp server was really being transmitted over a TLS/SSL connection.  In a default postfix install with TLS enabled there will be no indication that a message was transmitted over TLS in the mail log or in the email itself.  After some searching I was able to finally find the right parameters that need to be set.

Some notes
[LIST]
[*]Tested on Ubuntu Server v6.06 LTS with Postfix v2.2.10
[*]This only covers the options to view TLS information.  There are other tutorials on how to enable TLS support
[*]Standard disclaimer:  I make every effort possible to ensure this is still secure, if this blows up your computer or causes armegeddon, don't blame me
[*]I tend to use TLS and SSL interchangeably.  In a nutshell, SSL is a secure connection that occurs on a specific port (465 is the default for sending email).  TLS is a secure connection that can be used on any port.  Usually this is done over the standard smtp port 25.  There are many more differences, search google if you're curious.  Just remember that both TLS and SSL are secure connections, meaning content transmitted over TLS or SSL is encrypted and prevents the casual person from being able to read your email while in transit.
[/LIST]

To check if you already have this enabled.  Ensure your mail client is setup to send email either through SSL (port 465 by default) or TLS through SMTP (port 25 by default).  Send yourself an email message.  When you receive the email view the raw email.  This can be called several things in your email client.  It will usually be under the view menu and may say "raw message" or "full message" or "message source".  At the top you will see some received by headers, probably just one.  In a default postfix setup with default options the header will look something like the following:

```
Received: from [192.168.1.2] (your-isp.com [11.22.33.44])
	by mail.example.com (Postfix) with ESMTP id 162AEEE9E9
	for <you@example.com>; Thu,  5 Jul 2007 11:36:26 -0400 (EDT)
```

To enable that you were using TLS, you would add the following two options to your /etc/postfix/main.cf

```
smtpd_tls_received_header = yes
smtpd_tls_loglevel = 1
```

*smtpd_tls_received_header*, which defaults to no, will insert the extra information into the received header.  The reason this isn't enable by default is it can possibly be spoofed by a malicious user who creates their own bogus receive headers and adds bogus TLS information.  So this can't be used to be 100% certain a message was transmitted through an encrypted connection, but you can be pretty certain as malicious users usually don't bother with inserting false headers and if they do they would just insert a header like the one above that doesn't have a TLS line.  Although it is a valid point, I'd rather know if I'm sending over TLS and the risk of falsely believing a message was transmitted securely is minimal.

*smtpd_tls_loglevel*, which defaults to 0, indicates how much information you want logged to the mail log, typically /var/log/mail.log.  A value of 0 means don't log anything about the TLS subsystem.  A value of 1 will log the startup and certificate information.  You can set the value up to 4 with 3 being the recommended value for debugging (see references for a full description).  Setting the log level to 1 will only add two extra lines to the mail log and is also useful for debugging to know what clients are using TLS/SSL and which are not.

Once you have those enabled and restart postfix, send another email to yourself and your header should now look like this:

```
Received: from [192.168.1.2] (your-isp.com [11.22.33.44])
	(using TLSv1 with cipher AES128-SHA (128/128 bits))
	(No client certificate requested)
	by mail.example.com (Postfix) with ESMTP id 77233EF294
	for <you@example.com>; Thu,  5 Jul 2007 12:31:17 -0400 (EDT)
```

You will also see new lines like the following in your mail log during the smtp conversation:

```
Jul  5 12:31:17 hostname postfix/smtpd[28882]: setting up TLS connection from your-isp.com [11.22.33.44]
Jul  5 12:31:17 hostname postfix/smtpd[28882]: TLS connection established from your-isp.com [11.22.33.44]: TLSv1 with cipher AES128-SHA (128/128 bits)
```

This tells you that the connection was encrypted with TLSv1 using the cipher AES128-SHA with 128 bit key.  "No client certificate received" means the sender's mail client (yours in this case) did not send a client certificate.  A client certificate is beyond the scope of this tutorial, but it is a certificate that you install into your mail client that adds an extra layer to certify *you* are really you.  While some other MTDs (mail transport daemons) don't include that line, postfix does.

OK, so you may be asking yourself why would this information would be beneficial after initial testing?  If TLS is setup properly, not only can you verify that the end user is sending to the mail server over a secured connection, you can also verify that server to server communication is over a secured connection.  Take the following excerpt as an example:

```
Received: from mail.workdomain.com (mail.workdomain.com [44.33.22.11])
	(using TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits))
	(No client certificate requested)
	by mail.example.com (Postfix) with ESMTP id ADD52EF294
	for <you@example.com>; Thu,  5 Jul 2007 13:16:07 -0400 (EDT)
Received: from [10.0.0.2] ([11.22.33.44])
	(authenticated user jdoe@workdomain.com)
	by mail.workdomain.com (Kerio MailServer 6.4.0)
	(using TLSv1/SSLv3 with cipher AES128-SHA (128 bits))
	for you@example.com;
	Thu, 5 Jul 2007 13:17:23 -0400
```

This shows that the user [email]jdoe@workdomain.com[/email] sent [email]you@example.com[/email] an email.  It was first received by the work mail server (Kerio Mail Server in this case) over a tls/ssl connection.  So [email]jdoe@workdomain.com[/email] used a secure method to transmit the message to the work server.  Then work's mail server, mail.workdomain.com sent the message to mail.example.com over a secure TLS connection.  And you should be using a secure method to download your mail to your client.  You can then be pretty certain that this email was always transmitted in an encrypted form over the internet.

**Reference**
[Postfix/TLS - Configuring main.cf and master.cf](http://www.aet.tu-cottbus.de/personen/jaenicke/postfix_tls/doc/conf.html) - lists all the various configuration parameters that are TLS specific.

---

