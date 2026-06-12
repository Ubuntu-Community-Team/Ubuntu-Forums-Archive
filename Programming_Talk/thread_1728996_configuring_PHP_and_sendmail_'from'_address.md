---
title: "configuring PHP and sendmail 'from' address"
date: 2011-04-14
forum: Programming Talk
---

### Post by equinox_ on 2011-04-14
I have specified the following in my PHP code:

```
$to      = 'blah@email.state.edu';
    $subject = 'test';
    $message = 'test';
    $headers = 'From: mail@smartrek.blah.me' . "\r\n" .
               'Reply-To: mail@smartrek.blah.me' . "\r\n" .
                'X-Mailer: PHP/' . phpversion();
mail($to, $subject, $message, $headers);
```

when I do this sendmail is sending this email via  my current running process followed by "@" and the hostname of the machine. In my case this is root@equinox. How do I go about changing this in my sendmail configuration or probably PHP?

---

### Post by SeijiSensei on 2011-04-14
That's tricky, and it depends on which MTA you're using.  If you really are using sendmail, take a look at /etc/mail/sendmail.mc and see if you can use the [MASQUERADE()]("http://www.sendmail.org/m4/masquerading.html") directive to create a new sendmail.cf that sets the outbound domain.  

You probably also want to add the user name that Apache runs as to /etc/mail/trusted-users.  Otherwise PHP won't be able to force a different From: address in the SMTP envelope. 

I'm troubled by the fact that you say the outbound address is "root@" though.  Are you running Apache as the root user?  That's a *very* bad idea from a security perspective.  Most modern implementations run Apache as a unprivileged user, typically the "apache2" user in Ubuntu or the "httpd" user in RHEL/CentOS.

Another option is to send the message with sendmail itself rather than using the PHP mail() function.  Suppose $msg contains the entire message including From/To/Date/Subject, etc.  Then you can run 
```
exec("/usr/bin/sendmail -t -fbounce@example.com < $msg")
```
to push the message through sendmail.  The address after the -f will be used as the SMTP envelope sender if the Apache user appears in /etc/mail/trusted-users; the "-t" switch tells sendmail to use the address in the To: field of the message as the destination.

Oh, and on Linux, you only need "\n" not "\r\n" to terminate lines.  The latter is a DOS/Windows thing.

---

### Post by equinox_ on 2011-04-14
> **SeijiSensei said:**
> That's tricky, and it depends on which MTA you're using.  If you really are using sendmail, take a look at /etc/mail/sendmail.mc and see if you can use the [MASQUERADE()]("http://www.sendmail.org/m4/masquerading.html") directive to create a new sendmail.cf that sets the outbound domain.  

You probably also want to add the user name that Apache runs as to /etc/mail/trusted-users.  Otherwise PHP won't be able to force a different From: address in the SMTP envelope. 

I'm troubled by the fact that you say the outbound address is "root@" though.  Are you running Apache as the root user?  That's a *very* bad idea from a security perspective.  Most modern implementations run Apache as a unprivileged user, typically the "apache2" user in Ubuntu or the "httpd" user in RHEL/CentOS.

Another option is to send the message with sendmail itself rather than using the PHP mail() function.  Suppose $msg contains the entire message including From/To/Date/Subject, etc.  Then you can run 
```
exec("/usr/bin/sendmail -t -fbounce@example.com < $msg")
```
to push the message through sendmail.  The address after the -f will be used as the SMTP envelope sender if the Apache user appears in /etc/mail/trusted-users; the "-t" switch tells sendmail to use the address in the To: field of the message as the destination.

Oh, and on Linux, you only need "\n" not "\r\n" to terminate lines.  The latter is a DOS/Windows thing.

Yes I am running it from root, I know how bad it is. Never used to log in via root, just for this case. If it's just for sending email do I have to set anything in the MX record? I have an A record already now, not sure if this affects anything.

I am also running nginx instead of apache. One other thing that's bothering me is that I always get a warning, unable to resolve host Blah when I restart sendmail

---

### Post by SeijiSensei on 2011-04-14
> **equinox_ said:**
> Yes I am running it from root, I know how bad it is. Never used to log in via root, just for this case. If it's just for sending email do I have to set anything in the MX record? I have an A record already now, not sure if this affects anything.

MX records tell remote SMTP servers where to send mail for a domain.  They don't have anything to do with outbound mail.

As for running as root, I'm not sure what logging in as root has to do with it.  I'm talking about the server daemon itself.  If you run "ps aux" what user is listed as owning the HTTP daemon processes?  I've not used nginx at all, so maybe that's the way it's supposed to be configured?  Seems pretty dicey to me, though.

> One other thing that's bothering me is that I always get a warning, unable to resolve host Blah when I restart sendmail

Do you run a nameserver?  Do you have a reverse domain for your IP address block like 10.10.10.in-addr.arpa?  If not, do you have an entry in /etc/hosts for your IP address and server name?  That alone might fix the problem.

---

### Post by equinox_ on 2011-04-14
I think the issue might be in the var_hosts it self. The mail server seems to be confused with which domain should it use. Is there a setting to this?
Here's what my etc/hosts looked like:

127.0.0.1 localhost.localdomain localhost
50.56.81.42 smartrek.test.me smartrek
50.56.81.42 admin.api.me adminfrapi

When I tried sending an email, I always got:

450 4.1.8 <www-data@localhost.localdomain>                                                             : Sender address rejected: Domain not found


clearly localhost.localdomain is not a valid domain. I want the mail server to use smartrek.test.me as the domain. How do I set that?

---

### Post by SeijiSensei on 2011-04-15
> **equinox_ said:**
> I want the mail server to use smartrek.test.me as the domain. How do I set that?

Reread my original post and the linked sendmail document.

Are you sure you're using sendmail and not Postfix?

As I said, this isn't simple to configure properly.

---

### Post by equinox_ on 2011-04-15
> **SeijiSensei said:**
> Reread my original post and the linked sendmail document.

Are you sure you're using sendmail and not Postfix?

As I said, this isn't simple to configure properly.

As of now I have set my /var/hosts as the following:

```
127.0.0.1 smartrek.test.me localhost
50.56.81.42 admin.api.me adminfrapi
```

It does what I want, except it's sending from [email]www-data@smartrek.test.me[/email], instead what I want is [email]admin@smartrek.test.me[/email]. Question now is how do I change it so that it doesn't use www-data and something else

---

