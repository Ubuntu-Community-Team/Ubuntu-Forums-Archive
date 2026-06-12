---
title: "Perl script"
date: 2010-10-30
forum: Programming Talk
---

### Post by wasanzy on 2010-10-30
Hi,

There is this project I am about to work on. The whole picture of the project is that, we have a mail server (qmail) and a ticketing system(kayako) and an mssql database that contains clintes and other information.

Now what I want to do is, write  a perl script that will querry the mssql database to check if the email coming is from a client or not. procmail I will configure to make this script run base on the email header. If the email is going to [email]support@ourdomain.com[/email], the the script is going to run. When the user exist in the database, the script wil have to rewrite the subject hearder of the email and add the account manager of the client's code in the database to it and report to procmail where procmail will take it over from there.

Please who have an idea on how I can start this? I have already connected from the qmal to the mssql database uging DBI and odbc.

Thank you.

---

### Post by wasanzy on 2010-11-03
May be I have to come up again. How do I do email parsing in perl. And also, I know how to make the procmail run the script, but how do I process procmail's parameters in perl?

---

### Post by slavik on 2010-11-03
have you read the promail documentation?

---

### Post by wasanzy on 2010-11-12
[COLOR=black][COLOR=black]I  have started some thng. My procmail looks like this. I intentionally  commented out those lines because I don't know how to implement them  yet, specially the Mail::Internet. Please I need a help with this. 
 
:0H 
* ^To.*postmaster@dot.com.gh 
| /usr/bin/mailfilter 
 
This is able to run the mailfter alright. 
 
How to get the sender of the mail to postmater in the perl script for futher processing is my problem. Below is the code: 
#!/usr/bin/perl 
 
use strict; 
use DBI; 
use Mail::Message; 
use Mail::Internet; 
use Mail::Procmail; 
use Mail::Sendmail; 
use Mail::Header; 
########################################################################## 
 
#$message = new Mail::Internet \*STDIN; 
 
my $m_obj       = pm_init( loglevel => 3); 
my $m_from      = pm_gethdr("from"); 
my $m_to        = pm_gethdr("to"); 
my $sm_sub      = pm_gethdr("subject"); 
 
my $data_source = q/dbi:ODBC:MSSQLServer/; 
my $user = q/test/; 
my $password = q/test/; 
 
#establishing the database connection 
 
#my $dbh = DBI->connect($data_source, $user, $password) 
 #   or die "Can't connect to $data_source: $DBI::errstr"; 
#my ($sql, $sth, $data, @rows); 
 
#$sql = "select coalesce(acm,0)acm from accounts where id in (select accid from category "; 
#$sql .= "where email like '%" . $m_from . "%') and coalesce(acm,0)>0"; 
#$sth = $dbh->prepare($sql) or die "Can't prepare statement: $DBI::errstr"; 
#$sth->execute(); 
 
 
 
#while( ( @rows ) = $sth->fetchrow()) 
#{ 
#       foreach $data (@rows) 
#       { 
 
my $myemail = "emma.wasanzy\@gmail.com"; 
                if ( $m_from eq $myemail ) 
                { 
                        sendEmail("wasanzy\@yahoo.com", "perscript\@dot.com.gh", "Simple email.", "the sender $m_from exist."); 
 
                } 
                else 
                { 
                        sendEmail("wasanzy\@yahoo.com",  "perscript\@dot.com.gh", "Simple email.", "the sender $m_from does not  exist."); 
                } 
 #       } 
#} 
#exit(); 
################################################# 
sub sendEmail 
 { 
        my ($to, $from, $subject, $message) = @_; 
        my $sendmail = '/usr/lib/sendmail'; 
        open(MAIL, "|$sendmail -oi -t"); 
                print MAIL "From: $from\n"; 
                print MAIL "To: $to\n"; 
                print MAIL "Subject: $subject\n\n"; 
                print MAIL "$message\n"; 
        close(MAIL); 
 } [/COLOR][/COLOR]

---

