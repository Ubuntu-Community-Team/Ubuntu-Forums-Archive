---
title: "[SOLVED] How to tell if server is sending mail"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by WorldTripping on 2008-05-16
Ok, so I have Apache set up and running OK (also using vhosts).

When I set up my LAMP server I installed a mail server too.

On the server I have a html page, that processes a php page to send mail (a simple feedback form).

The html and php pages process properly, ie error trapping, detecting invalid e-mail, looking for empty fields etc.

So as far as I can tell the server should be sending mail OK.

Where would I look, to check that a new mail is pending to be sent ?

Cheers.

(The machine is un-networked with no internet access.)

---

### Post by dca on 2008-05-16
Isn't it /var/mail?  If a message is pending and not sent depending on MTA app I thought it sits there.

---

### Post by Monicker on 2008-05-16
Depends.  Is your script using the local MTA ( such as postfix, or sendmail), is is it trying to directly speak to an outside mail server?

If you were using postfix, you could do "sudo postqueue -p" to view a list of all pending email messages.

---

### Post by WorldTripping on 2008-05-16
> Isn't it /var/mail? If a message is pending and not sent depending on MTA app I thought it sits there.

That folder is empty, except for a file called 'www-data' that I can't seem to access.

> If you were using postfix, you could do "sudo postqueue -p" to view a list of all pending email messages. 

Tells me "Mail que is empty"

I installed the mail server by using Synaptic | Edit | Mark Packages By Task | Mail Server

How can I determine what mail process is being used ?

I'm sending mail, using a php form that executes the function mail().

Here's the final two lines of php that send the mail (hopefully).

```
		mail($mailto, $subject, $messageproper,
		"From: \"$strSenderName\" <$strSenderEMail>" . $headersep . "Reply-To: \"$strSenderName\" <$strSenderEMail>" . $headersep . "X-Mailer: chfeedback.php 2.10.0" );
```

The code actually executes past this point, so I'm assuming that it has executed properly.

Any ideas ?

Cheers.

---

### Post by Monicker on 2008-05-16
It looks like a function which relies on the local mta for delivery.  You should have postfix installed, from your description of the installation.


From a terminal:

```
sudo grep "status=sent" /var/log/mail*
```


And check the following log files in particular:

```
/var/log/mail.log
/var/log/mail.info
```

---

### Post by WorldTripping on 2008-05-16
Cool,

Those logs are exactly what I was looking for.

It looks like I'm running 'postfix', with Dovecot v1.0.10

It also looks as if the server is sending mail OK.

It's picking up the correct <to> and <from> fields from the php processing script.

Is there any way that I can send the mails to myself, and collect them with Thunderbird?

Would this be as simple as replacing the php string:
$mailto = 'someone@domain';
with
$mailto = 'someone@localhost';

Could I then set up a local Thunderbird mail account to collect these ?

Cheers.

---

### Post by WorldTripping on 2008-05-16
I answered my own question !

In the php processing file, if I put:
$mailto = 'someone@localhost';

I can then collect these using Thunderbird, with account settings;
Server Name=localhost
User Name = someone

This then happily collects the mail sent by the php code.

Cool.

---

