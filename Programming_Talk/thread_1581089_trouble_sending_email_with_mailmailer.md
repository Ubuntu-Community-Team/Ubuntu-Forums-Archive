---
title: "trouble sending email with mail::mailer"
date: 2010-09-24
forum: Programming Talk
---

### Post by badperson on 2010-09-24
Hi,
I'm trying to write a script that will send an email, but I'm getting an error:

```
use strict;
use Mail::Mailer;

my $mail = Mail::Mailer->new("sendmail");
$mail->open({
    From => 'my@address.com',
    To => 'my@address.com',
    Subject => 'test email',
    }) or die "can't open $!\n";
```


returns this:
> No mailer type specified (and no default available), thus can not find executable program. at test-email.pl line 4


by altering the code like so:
```
my $mail = Mail::Mailer->new qw(mail);
```

I get 
> Can't locate Mail/Mailer/mail.pm in @INC (@INC contains: /bunch/of/paths/for/@INC

what is the correct way to configure this for ubuntu?
bp

---

### Post by gmargo on 2010-09-25
You must not have a [Message Transfer Agent]("http://en.wikipedia.org/wiki/Message_transfer_agent") installed.  Your "sendmail" example generates that error if it cannot find a **sendmail** executable.  Install one of the available MTAs, like the **postfix** package. [http://packages.ubuntu.com/lucid/postfix](http://packages.ubuntu.com/lucid/postfix)

---

### Post by badperson on 2010-09-27
thanks for the reply. 
I installed sendmail, and my script now sends email, although the script runs very slowly. I think this is because sendmail doesn't like sending email to/from the localhost? 

my mail.log file has entries such as:

> Sep 27 10:15:48 machine-name sendmail[4532]: My unqualified host name (machine-name) unknown; sleeping for retry
Sep 27 10:16:48 machine-name sendmail[4532]: unable to qualify my own domain name (jason-desktop) -- using short name
Sep 27 10:16:48 machine-name sendmail[4532]: o8REGmUe004532: from=jason, size=176, class=0, nrcpts=1, msgid=<201009271416.o8REGmUe004532@machine-name>, relay=jason@localhost
Sep 27 10:16:48 machine-name sm-mta[4543]: o8REGmnL004543: from=<jason@machine-name>, size=397, class=0, nrcpts=1, msgid=<201009271416.o8REGmUe004532@jason-desktop>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Sep 27 10:16:48 machine-name sendmail[4532]: o8REGmUe004532: to=jw@jasonwardenburg.com, ctladdr=jason (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30176, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (o8REGmnL004543 Message accepted for delivery)
Sep 27 10:16:49 machine-name sm-mta[4545]: o8REGmnL004543: to=<me@me.com>, ctladdr=<jason@machine-name> (1000/1000), delay=00:00:01, xdelay=00:00:01, mailer=esmtp, pri=120397, relay=email-server. [74.6.140.31], dsn=2.0.0, stat=Sent (ok dirdel)

do you know how to configure sendmail to work faster, or is postfix a better solution?
bp

---

### Post by gmargo on 2010-09-27
Do you have a fully qualified domain name for your system?  I think it's trying to figure that out for the minute's delay.  Try adding "jason-desktop.example.com" as an additional name to the "jason-desktop" entry in /etc/hosts.  Or try postfix.

---

### Post by badperson on 2010-09-27
how do you connect postfix to mail::mailer?
I'm getting this when trying to use the default MTA:

```
No real MTA found, using 'testfile' at /usr/share/perl5/Mail/Mailer.pm line 107.
```

tried restarting postfix...no dice.
bp

---

