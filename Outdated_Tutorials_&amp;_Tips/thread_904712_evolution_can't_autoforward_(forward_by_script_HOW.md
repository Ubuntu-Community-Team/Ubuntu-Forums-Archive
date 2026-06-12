---
title: "evolution can't autoforward (forward by script HOWTO)"
date: 2008-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by mikey11 on 2008-08-29
Greetings, 

       After much frustration I have found a solution which worked for me where no others would.

Evolution will not autoforward mail for me, and I am on a network where the ports for smtp and other popular mail protocols are disabled. This left me with no way to autoforward outside of my network using the typical solution like piping the output to a shell script, and using tools like 

formail 
sendmail
mutt


I had a PERL script created for by a colleague using Mail::Send which also had the same problems, but worked internally... 

I'll include the script for people whom the ports are not blocked

```

#!/usr/bin/perl -w
use strict;
use Mail::Send;
my @body = <>;
my $msg = Mail::Send->new;

$msg-> to('redirectaddy@host.com');

$msg-> subject('forwarded from other acct');

my $FH = $msg->open('sendmail');

print $FH @body;

$FH->close;

```

In the end, the solution for me was either to pipe the output to a file and use a cron job to ftp (ftp isn't blocked) it to my home ftp server (not ideal, server is not always up), or to access a function within the MS exchange mail server software itself. 

I accessed my exchange account through Outlook on a colleagues windows machine, and created a Rule (I believe it's a choice under the options tab). The rule redirects mail which is sent only to me (committee and group emails are of less importance to me) to my gmail account.

This was much easier than any of the other solutions, and anyone who does not like shell scripting would be best off using this method. 

Beware though, your IT dept can turn off which rules are allowed and break it for you. 

Cheers, Mike

---

