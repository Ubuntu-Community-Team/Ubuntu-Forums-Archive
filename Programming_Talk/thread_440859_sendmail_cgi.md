---
title: "sendmail cgi"
date: 2007-05-12
forum: Programming Talk
---

### Post by evaristegalois on 2007-05-12
I am trying to teach myself to make html forms, post them online and have the results emailed to me. I write my cgi files using perl. All is well except that I don't know enough about sendmail to have the results emailed to me. I know that the command is /usr/sbin/sendmail but then I couldn't find an answer to the simple question of how to write an email from a server. 

I defined $sendmail=/usr/sbin/sendmail and the other variables as you would expect but it didn't do the trick. What's wrong? What's the easiest way to send an email via sendmail from a server?

open(SENDMAIL, "|$sendmail")
print SENDMAIL $reply_to; 
print SENDMAIL $subject; 
print SENDMAIL $to; 
print SENDMAIL "Content-type: text/plain\n\n"; 
print SENDMAIL $content; 
close(SENDMAIL);

--evaristegalois

---

### Post by tr333 on 2007-05-13
try installing the "Mail::Sendmail" package from CPAN, or any other CPAN package for sendmail.

here's a sample of code that i use for sendmail:
(note that i also use the CGI package)

```
#!/usr/bin/perl -T

use strict;
use warnings;

use CGI qw(:all -debug);
use CGI::Carp qw(fatalsToBrowser warningsToBrowser);
use Mail::Sendmail;

$rxval = $Mail::Sendmail::address_rx;

my $from_name = param("from_name");
my $from_email = param("from_email");
my $subject = param("subject");
my $message = param("message");
my $address = 'Me <myaddress@example.com>';

if ($from_email !~ /$rxval/) {

    print redirect('email_error.html');

} else {

    // escape any html code that might be in the message
    $message = escapeHTML($message);

    %mail = ( To      => $address,
              From    => $from_name.' <'.$from_email.'>',
              Subject => $subject,
              Message => $message
        );

    sendmail(%mail);

    print redirect('email_success.html');

}
```

---

### Post by evaristegalois on 2007-05-13
Thanks. I was hoping for something simpler but I'll try this.

--evaristegalois

---

### Post by evaristegalois on 2007-05-15
I am not doing this from my own server so I can't install perl modules (or at least I don't know how to). There is a program called sendEmail which works like this

sendEmail -f "from@email.com" -t "to@email.com" -u "Subject" -m "this is the message body"

It works well from my computer but the program is not on my server. How could you do this in sendmail? Shouldn't there be a simple way to tell a perl cgi program to send an email to somebody without much ado, just using STDIN?

---

### Post by tr333 on 2007-06-19
if you want to send email directly from the "sendmail" program, writing directly to sendmail using stdin, read the "perlfaq9" page on "How do I send mail?".

```
perldoc perlfaq9
```

---

