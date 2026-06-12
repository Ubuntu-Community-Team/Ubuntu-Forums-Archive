---
title: "help with a perl script to send a simple email"
date: 2008-10-25
forum: Programming Talk
---

### Post by fredscripts on 2008-10-25
Hi!

I found this module in order to send a simple email using a gmail account in Perl
[http://search.cpan.org/~lbrocard/Email-Send-Gmail-0.33/lib/Email/Send/Gmail.pm](http://search.cpan.org/~lbrocard/Email-Send-Gmail-0.33/lib/Email/Send/Gmail.pm)

Running the synopsis-like code to test it:

```
#!/usr/bin/perl


use strict;
use warnings;
use Email::Send;
use Email::Send::Gmail;
use Email::Simple::Creator;
use Carp;

my $email = Email::Simple->create(
header => [
	From    => 'myaccount@gmail.com',
	To      => 'myaccount@hotmail.com',
	Subject => 'hello email::send::gmail',
],
body => 'will Email::Send::Gmail fail? y/n',
);

my $sender = Email::Send->new(
{   mailer      => 'Gmail',
	mailer_args => [
	username => 'myaccount@gmail.com',
	password => 'mypassword',
	]
}
);
eval { $sender->send($email) };
confess "Error sending email: $@" if $@;

print "success\n";
```

All modules installed successfully, but when I run it:

```
Error sending email: Email::Send::Gmail: error authenticating username
+ myaccount at /usr/local/share/perl/5.8.8/Email/Send.pm line 243
 at ./sendemail.pl line 29
```

Acces to gmail is fine:

```
telnet smtp.gmail.com 995 -> Trying 216.239.59.109... Connected to gmail-smtp-msa.l.google.com

```

Besides,that this code runs perfectly in a Leopard plataform (Mac OS X). And even more surprising, it runs perfectly on the Ubuntu 8.04 that I have installed in the macbook (in a different partition). So it really freezes me because the problem is specific of my PC.


Anyone have any idea why it fails? (I've also started a thread in perlmonks,[http://www.perlmonks.org/?node_id=719444](http://www.perlmonks.org/?node_id=719444))

It would be interesting to test some network commands here on the PC and on the mac ubuntu partition to really see the differences between plataforms and realize why this script works on a macbook and not on a normal PC.

Thank you very much in advance!!!

---

### Post by loell on 2008-10-25
how did you install **Email-Send-2.192**? is it through regular cpan way?

---

### Post by fredscripts on 2008-10-25
Yep sure using the cpan module.

---

### Post by drubin on 2008-10-25
[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/) This is what I do althought I mostly use it as an application instead of with perl modual but it might help you.

---

### Post by fredscripts on 2008-10-26
> **drubin said:**
> [http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/) This is what I do althought I mostly use it as an application instead of with perl modual but it might help you.

Hi! thanks for the info.

I'm having problems sending a simple email from my gmail account with that program.I'm running:

```

./sendEmail -f myaccount@gmail.com -m "foo" -cc myaccount@gmail.com -xu myaccount -xp mypassword

```

And (even using sudo) this error appears:

```
Oct 26 10:49:01 fredlab sendEmail[6026]: ERROR => Connection attempt to localhost:25 failed: IO::Socket::INET: connect: Connection refused
```

I'm not running the program with correct arguments?

Thanks!

---

### Post by fredscripts on 2008-10-26
any ideas?

---

### Post by drubin on 2008-10-26
> **fredscripts said:**
> Hi! thanks for the info.

I'm having problems sending a simple email from my gmail account with that program.I'm running:

```

./sendEmail -f myaccount@gmail.com -m "foo" -cc myaccount@gmail.com -xu myaccount -xp mypassword

```

You would never need sudo in this situation as the send is not trying to access your files on your computer but a remote server.

The biggest issue is that you are not telling the script what smtp server to connect to.  the -s param. in this case  smtp.gmail.com

also -ux if your FULL gmail address ie  -ux [email]myaccount@gmail.com[/email]

[this]("http://lifehacker.com/software/email-apps/how-to-use-gmail-as-your-smtp-server-111166.php") might help you

---

### Post by fredscripts on 2008-10-26
Thanks for answering.

```
./sendEmail -s smtp.gmail.com -f myaccount@gmail.com -m "foo" -cc myaccount@gmail.com -xu myaccount@gmail.com -xp mypassword

```

```
Oct 26 21:12:58 fredlab sendEmail[5955]: ERROR => Connection attempt to smtp.gmail.com:25 failed: IO::Socket::INET: Bad hostname 'smtp.gmail.com'

```
What am I doing wrong?

```

telnet smtp.gmail.com 25
Trying 216.239.59.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP m5sm6471201gve.3
```

---

### Post by drubin on 2008-10-26
> **fredscripts said:**
> Thanks for answering.

```
./sendEmail -s smtp.gmail.com -f myaccount@gmail.com -m "foo" -cc myaccount@gmail.com -xu myaccount@gmail.com -xp mypassword

```

```
Oct 26 21:12:58 fredlab sendEmail[5955]: ERROR => Connection attempt to smtp.gmail.com:25 failed: IO::Socket::INET: Bad hostname 'smtp.gmail.com'

```
What am I doing wrong?

```

telnet smtp.gmail.com 25
Trying 216.239.59.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP m5sm6471201gve.3
```

Try adding a -vvvv  (for more verbose output generated) 

But > Outgoing Mail Server - use the SMTP mail server address provided by your local ISP or smtp.gmail.com (SSL enabled, port 465)

so it would not be using 25 port.

> TLS Support
Starting with sendEmail v1.54, TLS support is included! To enable TLS support simply install the Net::SSLeay and IO::Socket::SSL perl modules. The following new command line parameters are now available:
    -o tls=auto This is the default, TLS will be used if possible.
    -o tls=yes Use this to require TLS for message delivery.
    -o tls=no Use this to disable TLS support.
If TLS is giving strange errors, try upgrading the Net::SSLeay and IO::Socket::SSL perl modules. Please do NOT report TLS bugs unless you have already done this! If you're running up-to-date versions of these modules and you are getting TLS errors, your detailed bug report will be appreciated. Yes, you can finally use SendEmail to send messages to your GMail account :) 

try 

```
./sendEmail -vvv -s smtp.gmail.com -f myaccount@gmail.com -m "foo" -cc myaccount@gmail.com -xu myaccount@gmail.com -xp mypassword -o tls=auto

```

---

### Post by fredscripts on 2008-10-26
now it worked!!!!

Thanks you very much!!! (Even though I'm curious about why my script worked on Mac OS, and on an ubuntu partition in the same macbook, and not on my normal PC which has the same ubuntu version and packages of the one of macbook)

---

### Post by drubin on 2008-10-26
> **fredscripts said:**
> now it worked!!!!

Thanks you very much!!! (Even though I'm curious about why my script worked on Mac OS, and on an ubuntu partition in the same macbook, and not on my normal PC which has the same ubuntu version and packages of the one of macbook)
Glad. 

Don't forget to mark it as solved so others that are searching for a similar solution can see this as a solved solution.

I am not sure about why it did/didn't work I know very little perl code so I was just going by what the manual said.

---

