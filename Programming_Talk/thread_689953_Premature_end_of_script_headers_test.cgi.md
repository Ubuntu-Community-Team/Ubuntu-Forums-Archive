---
title: "Premature end of script headers: test.cgi"
date: 2008-02-06
forum: Programming Talk
---

### Post by anbumanij on 2008-02-06
This was the log message of apache, So wht i have to do. There was 

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>500 Internal Server Error</title>
</head><body>
<h1>Internal Server Error</h1>
<p>The server encountered an internal error or
misconfiguration and was unable to complete
your request.</p>
<p>Please contact the server administrator,
 webmaster@localhost and inform them of the time the error occurred,
and anything you might have done that may have
caused the error.</p>
<p>More information about this error may be available
in the server error log.</p>
<hr>
<address>Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c mod_perl/2.0.2 Perl/v5.8.8 Server at localhost Port 80</address>
</body></html>

**Wht configuration i have to do.** I changed to 0775 to my CGI-BIN and also to test.pl. And also i want to know the difference between cgi and pl extension. Pls help me. :mad:

---

### Post by anbumanij on 2008-02-07
Problem solved. Want to give proper header info of perl

such as #!/usr/bin/perl -w
and also want to use..

print "Content-type:text/html\n\n";

Example program...


#!/usr/bin/perl -w
use DBI;


print "Content-type:text/html\n\n";

$dbh = DBI->connect("dbi:mysql:anbu","root","") or die("Unable to connect with database");

	$sSQL = "SELECT * FROM users";
	$st = $dbh->prepare($sSQL) or die "Preparing MySQL query failed";
	$st->execute() or die "The execution of the MySQL query failed:";
	while ($row = $st->fetchrow_hashref())
	{
    		print " $row->{user_id} Password $row->{password} <br>";
	}

$dbh ->disconnect();

---

### Post by pmasiar on 2008-02-07
You should not post your passwords in a public forum - and you should change default MySQL passwords too :-)

Consider using more modern language with good web app framework, like Python (with Django or Turbogears, my favorite) or Ruby on Rails. Framework will solve many problems for you, and in a "best practices" way.

If you are stuck to Perl (and I feel sorry for you: been there, done that), learn about best coding practices. Trust me, Perl code could become so messy you will not believe what moron wrote it - and you know that moron is same person. And use Perl web app framework. Thera are many (too many), CGI::Application is possibly the most popular simple one, but i do not follow Perl development anymore, check for yourself.

---

