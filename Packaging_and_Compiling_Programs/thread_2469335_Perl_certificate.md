---
title: "Perl certificate"
date: 2021-11-26
forum: Packaging and Compiling Programs
---

### Post by rovell742 on 2021-11-26
Hi
I'm using ubuntu 18.04. I want to send email with Perl Script SendEmail but i get the error

  TLS setup failed: SSL connect attempt failed error:1416F086:SSL routines:tls_process_server_certificate:certificate verify failed

In what folder or repository i've to put certificate to validate?

Thanks

---

### Post by TheFu on 2021-11-27
Are you using an MTA as Unix expects or not?

Typically, the MTA would have a cert, so your script doesn't need it.

Is this server in a residential network or on a business network?  

With a business, you have more options and setting up an email gateway (MTA) to address this stuff isn't THAT hard.  

On a residential network, you'll either need to use client-to-server connection (465/tcp or 587/tcp), which I'm guessing perl can do or use the ISPs email relay, which is really easy to setup with an MTA for outbound email. There's a relayhost setting just for it in postfix's main.cf file and just add 1 line to the 'transport' file for all email to be send through the ISP's relay.

If client-to-remote-server using 465/587 authentication is needed, I'd use the perl module Net::SMTP::TLS or Net::SMTP or Mail::Sendmail.  I've not done this, since I run email servers, but I whack on perl all the time the last 25 yrs.

If you post a 20 line version of your script, I'll take a look. Can't promise anything. The perlmonks might be good to look at it as well.

---

