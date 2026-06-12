---
title: "Using perl scrip to email"
date: 2008-12-22
forum: Programming Talk
---

### Post by kd5gje on 2008-12-22
I am trying to use a peal script to send an email.  I am using the program motion which will execute something when motion is picked up.  I know motion is working correctly because when I type:

```
./email.pl
```

into the terminal from the directory that this file is from, I get the same result as I do when motion is running:

```
Content-type: text/html
```

and no email.  I am using my same email account in the to and from fields, would that be a problem?  Also, it's an external account, I don't have an email server set up.

I also tried using mutt but had no luck there.  This was the closest thing I could find that seemed like it should work.

Is there something I am missing or will this not work?

```
#!/usr/bin/perl
print "Content-type: text/html\n\n";

$title='A Test';
$to='myemail@domain.com';
$from= 'myemail@domain.com';
$subject='Test';

open(MAIL, "|/usr/sbin/sendmail -t");

## Mail Header
print MAIL "To: $to\n";
print MAIL "From: $from\n";
print MAIL "Subject: $subject\n\n";
## Mail Body
print MAIL "This is a test\n";

close(MAIL);
```

---

### Post by cmnorton on 2008-12-22
Is there a reason you cannot use Perl's built-in mail modules?

Here are two of many available links I found in Google, searching for perl mail api.

[http://www.perl.com/pub/a/2004/06/10/email.html](http://www.perl.com/pub/a/2004/06/10/email.html)
[http://docs.proscriptum.com/pure_perl_mail.html](http://docs.proscriptum.com/pure_perl_mail.html)

---

### Post by monkeyking on 2008-12-23
I tried to use command line posting of emails.
Using some homemade script.
But I never got the attachment part working.
So I ended up installing mutt and ssmtp.

now I can send emails like

[PHP]echo "emailtext"| mutt -a attached.file -s "email subject" person.to@email.com[/PHP]

---

### Post by kd5gje on 2008-12-23
I give up.  I have spent three straight 8 hour evenings trying to get it all working.  I tried mailing with mail, mutt, sendmail, and alpine.  I tried writing about three perl scripts. I tried three different php scripts and opened them from the web browser (they said they worked, didn't echo the error) but no email.  I tried two different ways to upload to flicker.  And, I tried three different ways to send messages to twitter.

I got one to update twitter but it doesn't send messages to my phone.  I don't know what it's deal is, something with twitter, I have two accounts and they both follow each other, but no text, oh well.

Everything comes up with some type of error one way or another.  Thanks for trying to help though.

---

### Post by cmnorton on 2008-12-23
Have you installed the mail utilities package?

sudo apt-get update
sudo aptitude install -y mailutils

---

### Post by kd5gje on 2008-12-23
Ok, I did that and all it did was remove some linux headers.  I have run a few of the email scripts and have gotten nothing but:

```
Content-type: text/html
```

and a blank line.

Or, I just get a blank line and it cancels after a while.

I will try ftp now.

---

### Post by monkeyking on 2008-12-23
ok,
you really need to elaborate on how you want your email set up.

Have you installed a working local mailserver?
Do you use a normal remoter server?
or do you use something like gmail?

---

### Post by kd5gje on 2008-12-23
No, I don't have a local mail server set up, I am trying to send it to my yahoo account.  I remember being able to do that with php from my website when I had some stuff up on that thing, but then again, it was an actual hosted site and even though I didn't have an email address, it had an email server on it.

I now have made a perl script to ftp a file to my remote web site and it almost works correctly, but I am still having an issue.  I am saving the shockwave flash files as the same name on the linux box and then uploading them with the name_time so that I can upload them again and again to the remote server without overwriting any of them.  All of this works great but my problem is that somewhere along the way my files are corrupted.

I can play the file on the linux box so I know it works fine, but when I download the one from the remote server, it won't play.  I have put a delay in so that the computer may have time to complete the swf file before having to upload it (just guessing here) but still no help.  Here is what I got.

```
#!/usr/bin/perl
use Net::FTP;

# Create Variables
my $host="domain.com";
my $directory="./";
my $motion="/home/user/motion/";
my $cam1="/home/user/motion/cam1/camshot.swf";
my $cam2="/home/user/motion/cam2/camshot.swf";
my $cam1r="/cam1/";
my $cam2r="/cam2/";
my $time= time;

# Connect to the server
$ftp=Net::FTP->new($host,Timeout=>240) or $newerr=1;
  push @ERRORS, "Can't ftp to $host: $!\n" if $newerr;
  myerr() if $newerr;
print "Connected\n"; 

# Log in to the server
$ftp->login("user\@domain.com","password") or $newerr=1;
print "Getting file list";
  push @ERRORS, "Can't login to $host: $!\n" if $newerr;
  $ftp->quit if $newerr;
  myerr() if $newerr; 
print "Logged in at $time\n";


# Move to the remote cam1 directory
$ftp->cwd($cam1r) or $newerr=1; 
  push @ERRORS, "Can't cd  $!\n" if $newerr;
   myerr() if $newerr;
  $ftp->quit if $newerr;

# Delay before upload
my $delaytime= time;
my $newdelaytime= $delaytime + 5;
print "$delaytime\n";
while ($delaytime <= $newdelaytime){
  $delaytime= time;
}
$delaytime = time;
print "$delaytime\n";

# copy a single file to the remote server 
$ftp->put($cam1, "camshot_$time.swf");

# Show files that are in server in cam1 directory
@files=$ftp->dir or $newerr=1;
  push @ERRORS, "Can't get file list $!\n" if $newerr;
  myerr() if $newerr;
print "Got  file list\n";   
foreach(@files) {
  print "$_\n";
  }

# Move to the remote cam2 directory
$ftp->cwd($cam2r) or $newerr=1; 
  push @ERRORS, "Can't cd  $!\n" if $newerr;
   myerr() if $newerr;
  $ftp->quit if $newerr;

# Delay before upload
my $delaytime= time;
my $newdelaytime= $delaytime + 5;
print "$delaytime\n";
while ($delaytime <= $newdelaytime){
  $delaytime= time;
}
$delaytime = time;
print "$delaytime\n";

# copy a single file to the remote server 
$ftp->put($cam2, "camshot_$time.swf");

# Show files that are in server in cam2 directory
@files=$ftp->dir or $newerr=1;
  push @ERRORS, "Can't get file list $!\n" if $newerr;
  myerr() if $newerr;
print "Got  file list\n";   
foreach(@files) {
  print "$_\n";
  }

# Quit FTP
$ftp->quit; 

sub myerr {
  print "Error: \n";
  print @ERRORS;
  exit 0;
} 
```

The program motion is calling this after the motion is no longer detected on camera 2, there is a small delay there too.  Everything in terminal goes great with no errors.

---

### Post by monkeyking on 2008-12-24
hmm, looks rather complicated.
I couldn't really see anything mail related.

However, I think this is how I set up my ssmtp with my gmail. [http://www.delodder.be/howto/gmail-with-ssmtp-on-deb-based-system/](http://www.delodder.be/howto/gmail-with-ssmtp-on-deb-based-system/)

good luck

---

### Post by kd5gje on 2008-12-24
Ok, thanks.  I will take a look.  I just logged vert term 1 and noticed I have mail, 45 messages.  They are all the failed messages that sendmail couldn't get out to my yahoo account.  I guess sendmail is working afterall.  Anyway, I will take a look at your link.

---

### Post by cmnorton on 2008-12-24
These messages sound like you are having routing problems from sendmail. 

Definitely look at your logs to see more clearly what the errors are. You might need a smarthost setting in your sendmail configuration.

---

