---
title: "Perl + sendmail. need help"
date: 2012-02-09
forum: Programming Talk
---

### Post by balagosa on 2012-02-09
So I am trying to send a test email to some users listed in a directory relative to my home. Thus you will see below a subroutine that will get those users and acquire a string of emails. 

Example the directory contains two users (.user1@domain_com AND .user2@domain_com). The subroutine gets those users and returns a string of (user1\@domain.com,user2\@domain.com,). I have no problem here and it is working because I have tried printing the output of the subroutine; the string is a concatenation of all emails separated by a comma for later use in email recipient.

The problem is on the variable $address. When incorporating it into sendmail, it is blank and thus the email fails. (problem area is shown in bold letters below). 

```

#!/usr/bin/perl
use strict;
use warnings;
use MIME::Parser;
use MIME::Entity;
use MIME::Body;

sub create_list;

**my $address = create_list();**

my $sendmail = '/usr/sbin/sendmail -t -i';
open MAIL, ("|$sendmail") || die "Unable to send mail: $!";
**print MAIL "To: $address\n";**
print MAIL "From: $address\n";
print MAIL "Subject: Antivirus Automailer";
print MAIL "\ \n$body";
close MAIL;


sub create_list
{
   my @files = <../mail/.*_com>;
   my @EmailList;
   foreach my $file (@files)
   {
        my @fields = split(/\./, $file);
        my $manipulate = $fields[3];
        $manipulate =~ s/_/./g;
        $manipulate =~ s/@/\\@/g;
        push(@EmailList, $manipulate);
   }


   my $buffer = '';
   foreach my $email (@EmailList)
   {
        $buffer = $buffer . $email . ",";
   }
   return $buffer;

}

```

I have tried doing a local assignemnt of the variable as follows below. It worked and no problems existed there.

```

my $address = 'user1@domain.com,user2@domain.com,';

ALSO

my $address = "user1\@domain.com,user2\@domain.com,";

```

I have included the bouncing email because of no recipient. As you can see the To: field is blank.

```

A message that you sent contained no recipient addresses, and therefore no
delivery could be attempted.

------ This is a copy of your message, including all the headers. ------

To: 
From: 
Subject: Antivirus Automailer 
Message-Id: <E1RvNl9-0001Dy-Dk@gatorXXXX.hostgator.com>
Date: Thu, 09 Feb 2012 00:45:35 -0600

TEST

```

---

### Post by balagosa on 2012-02-09
I have an update.

I decided to start small instead, doing the debugging step by step. The first line you will see is also the first line of my subroutine create_list(). Please take note of the items in bold. 

```

my @files = <../mail/.*_com>;

my $sendmail = '/usr/sbin/sendmail -t -i';
open MAIL, ("|$sendmail") || die "Unable to send mail: $!";
print MAIL "To: MYEMAIL@DOMAIN.COM\n";
print MAIL "From: MYEMAIL@DOMAIN.COM\n";
print MAIL "Subject: Antivirus Automailer";
print MAIL "\ \n**@files**";
close MAIL;

```

I am expecting an output on my email: [email]MYEMAIL@DOMAIN.COM[/email] with a message body of **@files** OR a VERY LONG LIST OF USERNAMES. The email was sent successfully but it was **BLANK**.

---

### Post by balagosa on 2012-02-09
no hope? :lolflag:

---

### Post by myrtle1908 on 2012-02-09
Does the following send a blank email also?

```
...
print MAIL "To: $address\n";
print MAIL "From: $address\n";
print MAIL "Subject: Antivirus Automailer\n";
print MAIN "Content-type: text/plain\n\n";
print MAIL "Hello";
...
```

---

### Post by balagosa on 2012-02-09
> **myrtle1908 said:**
> Does the following send a blank email also?

```
...

print MAIN "Content-type: text/plain\n\n";

...
```


That did not work either. The problem is with the create_list subroutine. IT RETURNS NO VALUE.

I think I lack in explaining the situation. This perl script is executed from a pipe. In my domain I have an email forwarder. This is where it pipes to this script. This is where the create_list returns no value. I also noticed the code below has no effect when the script is piped. But seems ok when executed from perl commandline.

```
system("some perl script here");
```

---

### Post by balagosa on 2012-02-10
gave up hope on this one.

No more piping to perl. I just made a mailing list with the users of my domain. More simple but I have to update the list regularly.

The pipe script was supposed to automate everything.

---

