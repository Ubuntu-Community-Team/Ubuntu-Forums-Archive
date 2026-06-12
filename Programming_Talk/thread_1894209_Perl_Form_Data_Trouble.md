---
title: "Perl Form Data Trouble"
date: 2011-12-12
forum: Programming Talk
---

### Post by fairplay89 on 2011-12-12
I am not very good with Perl so I was hoping that someone could help me. I need to read from an HTML form to a file with Perl. 

So far I have form. pl:
```

#!/usr/bin/perl -w

my $file = "log.txt";
my $name = param('name');
my $username = param('username');
my $password = param('password');
my $confirm = param('confirm');
my $DOB = param('DOB');

print "Content-Type: text/html\n\n";
print "<p>Why hello, $name.";
print "<p>Username: $username, Password: $password";
print "<p>DOB - $DOB";

open (LOG, ">$file") || die "D";
flock (LOG, 2) || die "D";
print LOG "$name, $username, $password, $DOB";
close (LOG);

```

And I have form.html as the source:
```


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Perl Final</title>
</head>
<form action="final.pl" method="post">
<p>Name:<input type="text" name="name" value="">
<p>Username:<input type="text" name="username" value="">
<p>Password:<input type="text" name="password" value="">
<p>Confirm Password:<input type="text" name="confirm_password" value="">
<p>Date Of Birth:<input type="text" name="DOB" value="">
<input type="submit" name="submit" value="Submit">
<form>
<body>
</body>
</html>

However I get an error on line 4. Can anyone help? Please! :(

```

---

### Post by Lars Noodén on 2011-12-12
You seem to be not using the package [libcgi-pm-perl](http://packages.ubuntu.com/oneiric/libcgi-pm-perl).  If you haven't already, install it.  That will give you the module [CGI](http://manpages.ubuntu.com/manpages/oneiric/en/man3/CGI.3perl.html) which will make it easier to read form data.

---

### Post by fairplay89 on 2011-12-12
> **Lars Noodén said:**
> You seem to be not using the package [libcgi-pm-perl](http://packages.ubuntu.com/oneiric/libcgi-pm-perl).  If you haven't already, install it.  That will give you the module [CGI](http://manpages.ubuntu.com/manpages/oneiric/en/man3/CGI.3perl.html) which will make it easier to read form data.

Will I need to make any code edits if using that?

I had it setup before using CGI, but I'm not sure that's how I have to do this one. (It's a project.)

---

### Post by Lars Noodén on 2011-12-12
> **fairplay89 said:**
> Will I need to make any code edits if using that?




A little bit.  Look at the manual page under the section, "Fetching the Value or Values of Single Named Parameter"

---

