---
title: "perl-script"
date: 2010-11-29
forum: Programming Talk
---

### Post by wasanzy on 2010-11-29
Hi all,

I wrote a script to extract the body of an incoming mail but it is not working as expected.

Script:
#!/usr/bin/perl
use Mail::Internet;

my $mail = Mail::Internet->new( \*STDIN );
my $headers = $mail->head->header_hashref;
my $sender = $mail->get('From');
my @sender = @{${$headers}{'From'}};
my $from = $headers->{From}->[0];
my $body = [ @{$mail->body} ];
print $body . "\n";

This is outputing:
ARRAY(0x8cf407c)

Instead of the real text messages in the body.

Some one to help?

Thanks!

---

### Post by spjackson on 2010-11-29
There are many ways to make it work. The most appropriate depends on what you are going to do later. Here's one way.
```
my $body = join("", @{$mail->body});
print $body . "\n";
```

---

### Post by trent.josephsen on 2010-11-29
What did you expect?  You asked it to print an arrayref, so it did.

If you want to see what the reference actually points to, use Data::Dumper.  If you want to view the result of $mail->body, which unless my perl-fu is failing is a subroutine call, just print that.

Apart from that, your use of @{...} is ... interesting.  It's legit as far as I can tell, but surely there's a clearer way to write whatever you are trying to do?

---

### Post by shawnhcorey on 2010-11-29
> **trent.josephsen said:**
> Apart from that, your use of @{...} is ... interesting.  It's legit as far as I can tell, but surely there's a clearer way to write whatever you are trying to do?

It is also correct.  But there are others ways to use references:
```
my @sender = @{ $headers->{'From'} };
```

---

### Post by Arndt on 2010-11-29
> **trent.josephsen said:**
> What did you expect?  You asked it to print an arrayref, so it did.

If you want to see what the reference actually points to, use Data::Dumper.  If you want to view the result of $mail->body, which unless my perl-fu is failing is a subroutine call, just print that.

Apart from that, your use of @{...} is ... interesting.  It's legit as far as I can tell, but surely there's a clearer way to write whatever you are trying to do?

I think smileys should be off by default. The Data colon colon Dumper thing got corrupted here, which probably was not your intention.

---

### Post by wasanzy on 2010-11-30
Thank you for the reply. I have got that part fixed.

Now my problem is, when procmail send the mail to the script, and  secript to sends it to another email address, I am geting it in this  format:


--001636c5a9efd3783a049644488f
Content-Type: text/plain; charset=ISO-8859-1

Hi,

Kindly send me back this ticket to my queue.


Regards

Emmanuel

--001636c5a9efd3783a049644488f
Content-Type: text/html; charset=ISO-8859-1

Hi,<br><br>Kindly send me back this ticket to my queue.
<br><br><br>Regards<br><br>Emmanuel<br>

--001636c5a9efd3783a049644488f--




The script doing this is here: Although I know the problem is from how I  am extracting the body but how to control this is a problem.

#!/usr/bin/perl
use strict;
use DBI;
use Mail::Internet;
use Mail::Sendmail;
use Mail::Header;
use Mail::Address;
use Net::POP3;
##################################################################
sendlog();
my ($ref, $mid, $mail, $sql, $sth, $data, $sender, $message_sent, $message);


# Read mail from STDIN
my $mail = Mail::Internet->new( \*STDIN );

# Creating an empty mail object
my $reply = Mail::Internet->new();

# Locate address of sender. The get() method returns a header line from the
# message, or undef if it doesn't exist. 
my $headers = $mail->head->header_hashref;
 # $sender = $mail->get('Reply-To') or 
  $sender = $mail->get('From');

my @sender = @{${$headers}{'From'}};
my $from = $headers->{From}->[0];

#split and use only the email address part
my @hfrom = split(/[<>]/, $from);
my $emailfrom = $hfrom[1];

$sender = (Mail::Address->parse($sender))[0];

my $mailto = "mbryqf\@dot.com.gh";

my $subject = $headers->{Subject}->[0];

my $email = $emailfrom;

my $body = join '', @{ $mail->body };
my @newbody = split(//, $body);

my $support = "support\@dot.com.gh";
my $support = "support\@dot.com.gh";

my @newmessage = ( "You are not  authorized to send email message to $support from $email.\n",
                   "For any clarification, please  call Teledata ICT customer service deparment");
                

my $subauto = "AUTO RESPONDER - Not autorized to send to $support";

#database connection
my $data_source = q/dbi:ODBC:MSSQLServer/;
my $user = q/test/;
my $password = q/test/;
my $dbh = DBI->connect($data_source, $user, $password);

my $logfile = "/tmp/mailfilter.log";
my $date = localtime();
my $logmesg = $date;
open LOGFILE, ">>$logfile" or die "can't open logfile $logfile for writting $!";


if (!$dbh)
{
        $subject = "AM-100" . "" . $subject;
        sendEmail("$mailto", "$email", "$subject", "$body");
        print LOGFILE $logmesg, "\tError connceting to the  $data_source:$DBI::errstr\n \t\tMail sent with subject: $subject,  succesfuly to $mailto \n";
}

my $error =  "Can't prepare statement: $DBI::errstr";
$sql = "select coalesce(acm,0)acm from accounts where id in (select accid from category ";
$sql .= "where email like '%" . $email . "%') and coalesce(acm,0)>0";
$sth = $dbh->prepare($sql) or die "$error";


$sth->execute();
my $exist = $sth->fetchrow_array();

        if ($exist)
        {
                #$subject = "AM-$exist  $subject";
                $subject = "AM-4 $subject";
                sendEmail("$mailto", "$email", "$subject", "$body");
                print LOGFILE $date, "\t$email Found in database. Mail sent succesfuly to $mailto with the subject $subject \n";

 }
        else
        {
                sendEmail("$email", "$support","$subauto", "@newmessage");
                print LOGFILE $logmesg, "\t$emailfrom was not found in database, message rejected from $emailfrom\n";

        }

close(MAIL);
close(LOGFILE);
deletemail();

And the sendEmail():
sub sendEmail
 {
        my ($mailto, $emailfrom, $subject, $body) = @_;
        my $sendmail = '/usr/lib/sendmail';
        open(MAIL, "|$sendmail -oi -t");
                print MAIL "From: $emailfrom\n";
                print MAIL "To: $mailto\n";
                print MAIL "Subject: $subject\n\n";
                print MAIL "$body \n";
        close(MAIL);
 }

---

