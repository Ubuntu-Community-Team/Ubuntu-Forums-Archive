---
title: "[SOLVED] Perl Telnet login script"
date: 2007-08-01
forum: Programming Talk
---

### Post by PastorTaz on 2007-08-01
I'm new to programming in Perl and I'm trying to get a script to automate a login to a FTP server using Telnet.  I've searched the net and everything I see does not work for me for some reason.   Here is my code

```
#!/usr/bin/perl -w
use strict;
use Net::Telnet;
my ($host, $port, $user, $pass, $command);

##### get host info
print 'Enter host: ';
chop($host = <STDIN>);
##### get port info
print 'Enter port: ';
chop($port = <STDIN>);
##### get user info
print 'Enter user: ';
chop($user = <STDIN>);
##### get user info & hide input
print 'Enter password: ';
system 'stty -echo';
chop($pass = <STDIN>);
system 'stty echo';
print "\n";


my $tn = new Net::Telnet(Host => $host, Port => $port, Timeout => 20)
     or die "connect failed: $!";
$tn->open ($host);
$tn->login($user, $pass)
     or die "login failed: $!";

print 'Hostname: ';
print $tn->cmd('/bin/hostname'), "\n";
my @who =  $tn->cmd('/usr/bin/who');
print "Here's who:\n", @who, "\n";
print "\nWhat is your command: ";
chop($command = <STDIN>);
print $tn->cmd($command), "\n";
$tn->close or die "close fail: $!";
```

This is where it dies
```
$tn->login($user, $pass)
```

And here is the error:
```
timed-out waiting for login prompt at ./test2.pl line 26

```

The FTP server I'm trying to get into is FileCOPA.

Thanks for any help you can give a noobie.

---

### Post by Mr. C. on 2007-08-01
The **login** method in Net::Telnet will timeout when the prompts do not match what is expected.  The **login** method expects the remote server to prompt with a login prompt that matches either:
```
/login[: ]*$/i
/username[: ]*$/i
```

and the password prompt must match:

```
/password[: ]*$/i
```

Use print() and watifor() to connect instead of login() if the remote FTP server does not prompt with those patterns.

Be sure the command prompt is also set.

See:

```
perldoc Net::Telnet
```

If your goal is to automate an FTP login and transfer, you can use wget or curl.

MrC

---

### Post by PastorTaz on 2007-08-03
Thanks Mr. C... I'm getting closer, this FTP server just wants to be a pain to automate.  Here is what I have for code...

```
#!/usr/bin/perl -w
use strict;
use Net::Telnet;
my ($host, $port, $user, $pass, $command);

##### get host info
print 'Enter host: ';
chop($host = <STDIN>);
##### get port info
print 'Enter port: ';
chop($port = <STDIN>);
##### get user info
print 'Enter user: ';
chop($user = <STDIN>);
##### get user info & hide input
print 'Enter password: ';
system 'stty -echo';
chop($pass = <STDIN>);
system 'stty echo';
print "\n";

print "user ", + $user, + "\r\n";
print "pass ", + $pass, + "\r\n";

my $tn = new Net::Telnet(Host => $host, Port => $port, Timeout => 20)
     or die "connect failed: $!";
$tn->open ($host);
#$tn->login($user, $pass)
#     or die "login failed: $!";
$tn->waitfor('/remaining/i');
#$tn->waitfor('/remaining: $/i');
print 'user ', + $user;
$tn->waitfor('/./i');
print 'pass ', + $pass;
$tn->waitfor ('/logged in./i');
print 'Hostname: ';
print $tn->cmd('/bin/hostname'), "\n";
my @who =  $tn->cmd('/usr/bin/who');
print "Here's who:\n", @who, "\n";
print "\nWhat is your command: ";
chop($command = <STDIN>);
print $tn->cmd($command), "\n";
$tn->close or die "close fail: $!";
```

Here is what my log in to the FTP server looks like

> 220-InterVations FileCOPA FTP Server Version 1.01 21st November 2005
220 Trial Version. 19 days remaining
user test
331 Password required for test.
pass test
230 User test logged in.


And here is my error...
> pattern match timed-out at ./test2.pl line 33
user testroot@vm-ubuntu:/lpt/scripts/perl# 

Line 33 is $tn->waitfor('/./i'); what's wierd is that the script is reading and executing line 34 before it times out.  Any suggestions as to why the waitfor() is not working for me?

Thanks,

---

### Post by Mr. C. on 2007-08-03
The /./ pattern matches any single character.  Is this what you want ?

MrC

---

### Post by PastorTaz on 2007-08-04
Not really sure to be honest.  What I'm trying to do is automate a login to a FTP server with a Perl script.  Here is what the server answers with when I do a manual login...

> [Trying 192.168.1.235...
Connected to 192.168.1.235.
Escape character is '^]'.
220-InterVations FileCOPA FTP Server Version 1.01 21st November 2005
220 Trial Version. 19 days remaining
user test
331 Password required for test.
pass test
230 User test logged in.
/QUOTE]

This is the code that I have so far for the login...

```
$tn->open ($host);
$tn->waitfor('/remaining/i');
print 'user ', + $user;
$tn->waitfor('/required for test/i');
print 'pass ', + $pass;
$tn->waitfor ('/logged in./i');
```

The "waitfor('/remaining/i'); seems to be working fine as the "print 'user' line runs.  The hang up is with the "waitfor('/required for test/i')" line (which was the "waitfor('/./i')" line in the previous post).

Here is the error being returned

[QUOTE]pattern match timed-out at ./test2.pl line 33


My ultimate goal is to be prompted for the host, port, user, and password and then have the script run and complete the login.

Thanks for the help. I haven't programmed since college 8 years ago.

---

### Post by Mr. C. on 2007-08-04
Since you are trying to match:

> 331 Password required for test.

try:

```
$tn->waitfor('/required for test\.$/i');
```

A dot (.) means any single character, so you have to escape it to match a literal dot.

MrC

---

### Post by PastorTaz on 2007-08-04
Someone else helped me do this with a socket instead of Telnet... However, my curiosity has been sparked and I want to get to the bottom of this.  I'm still getting the same error on the same line even with the adjusted code.

---

