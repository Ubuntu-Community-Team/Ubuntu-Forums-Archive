---
title: "cgi email form"
date: 2011-04-13
forum: Programming Talk
---

### Post by rabbitfarmer on 2011-04-13
Hey i'm working on putting an email form into my webpage, but for some reason it doesn't seem to verify the email from the HTML form. The site is [http://www.thoughtfreeze.com/contact.html](http://www.thoughtfreeze.com/contact.html). here is the html code

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Contact</title>
<h1 style="font-size:44px" align="center">Mail FTW!</h1>
<style>
div#lancaster {
    width:60%;
    background-color:#699;
    padding-top:60px;
    padding-right:60px;
    padding-left:60px;
    padding-bottom:160px;
    font-size:20px;
    margin:auto;
}
</style>
<style>
ul#list-nav {
    margin-top:-10px;
    list-style:none;
    padding:0px 0px;
    width:99%;
    position:absolute;
    text-align:center;
    height:auto;

} 
ul#list-nav li{
    display:inline;
    vertical-align:middle;
    width:100px;
    padding:10px;
    background-color:#689;
    
}
ul#list-nav li a {
    text-align:center;
    text-decoration:none;
    color:#000;
    padding:10px;
    
    
    
    
    font-size:20px;
}
ul#list-nav li:hover {
    background:#699;
    font-weight:normal;
    color:#000;
    font-size:22px;
    border-left:10px solid #333;
    border-right:10px solid #999;
    border-bottom:10px solid #666;
    border-top:10px solid #000;
    padding:10px;
    width:auto;
    margin:auto;
    bottom:0px;
}
ul#list-nav li a:active {
    color:#FFF;
    font-size:30px;
}
</style>
<script src="form.js" type="text/javascript" language="javascript"></script>
</head>

<body background="backgrounds/mailbg.png">




<div style="width:100%;margin:auto;text-align:center">
<div id="lancaster">

<p align="center" id="lancaster">
Hey! You wanna say something?!? Fill in the boxes below! If you want to send me a file to put up on my site, you can also email webmaster@thoughtfreeze.com.
</p>
<br/>
<br/>
<div style="width:60%;margin-right:50%;text-align:right">
<form onsubmit="return ValidateForm()" name="mailz" action="cgi-bin/email.cgi" enctype="text/plain" method="post">
<input type="hidden" name="recipient" value="webmaster@thoughtfreeze.com">

Your return email address: <input type="email" name="address" /><br/>
(if you want a responce) <br/>
<br/>
Subject: <input type="text" name="subject" /><br/>
<br/>
<br/>
<p style="margin-left:35%;" align="left">Message:</p>
<textarea name="message" cols="50" rows="6" style="margin-left:50%;margin-top:-42px;">
</textarea><br/>
<input type="submit" name="submit" value="Send it!" style="margin-right:30px;"/>

</form>
</div>
</div>
</div>

<br/>
<div id="content" align="center" style="width:100%;margin-top:-65px;">
<ul id="list-nav" align="center">
<li><a href="index.html">Home</a></li>
<li><a href="Design.html">Design</a></li>
<li><a href="blocks.html">Blocks</a></li>
<li><a href="philosophy.html">Philosophy</a></li>
<li><a href="links.html">Links</a></li>

<li><a href="About.html">About</a></li>
</ul>
</div>

</body>
</html>

```

and here is the email.cgi file

```

#!/usr/bin/perl

# A simple Perl-based CGI email handler. 
#
# Copyright 2004 Boutell.Com, Inc. Compatible with our earlier C program.
#
# Released under the same license terms as Perl 5 itself.
#
# We ask, but do not require, that you link to 
# http://www.boutell.com/email/ when using this script or a 
# variation of it.

use CGI;

my $sendmail = "/usr/sbin/sendmail";

# A text file containing a list of valid email recipients and the web pages to 
# which the user should be redirected after email is sent to each, on 
# alternating lines.  This allows one copy of the script to serve multiple 
# purposes without the risk that the script will be abused to send spam.
# YOU MUST CREATE SUCH A TEXT FILE AND CHANGE THE NEXT LINE TO ITS
# LOCATION ON THE SERVER.

my $emailConfPath = "email.conf";

# Parse any submitted form fields and return an object we can use
# to retrieve them
my $query = new CGI;

my $name = &veryclean($query->param('name'));
my $email = &veryclean($query->param('email'));
my $recipient = &veryclean($query->param('recipient'));
my $subject = &veryclean($query->param('subject'));


my $content = &clean($query->param('content'));

#Note: subject is not mandatory, but you can easily change that


if (!open(IN, "$emailConfPath")) {
    &error("Configuration Error",
        "The file $emailConfPath does not exist or cannot be " .
        "opened. Please read the documentation before installing " .
        "email.cgi.");
}
my $returnpage;

my $ok = 0;
while (1) {
    my $recipientc = <IN>;
    $recipientc =~ s/\s+$//;
    if ($recipientc eq "") {
        last;
    }
    my $returnpagec = <IN>;
    $returnpagec =~ s/\s+$//;
    if ($returnpagec eq "") {
        last;
    }
    if ($recipientc eq $recipient) {
        $ok = 1;
        $returnpage = $returnpagec;
        last;
    }
    
}
if (!$ok) {
    &error("Email Rejected",
        "The requested destination address is not one of " .
        "the permitted email recipients. Please read the " .
        "documentation before installing email.cgi.");

}
close(IN);

# Open a pipe to the sendmail program
open(OUT, "|$sendmail -t");
# Use the highly convenient <<EOM notation to include the message
# in this script more or less as it will actually appear
print OUT <<EOM
To: $recipient
Subject: $subject
Reply-To: $email
Supposedly-From: $name
[This message was sent through a www-email gateway.]

$content
EOM
;
close(OUT);
# Now redirect to the appropriate "landing" page for this recipient.
print $query->redirect($returnpage);

exit 0;

sub clean
{
    # Clean up any leading and trailing whitespace
    # using regular expressions.
    my $s = shift @_;
    $s =~ s/^\s+//;
    $s =~ s/\s+$//;
    return $s;
}

sub veryclean
{
    # Also forbid newlines by folding all internal whitespace to
    # single spaces. This prevents faking extra headers to cc 
    # extra people.
    my $s = shift @_;
    $s = &clean($s);
    $s =~ s/\s+$/ /g;
    return $s;
}

sub error
{
    # Output a valid HTML page as an error message
    my($title, $content) = @_;
    print $query->header;
    print <<EOM
<html>
<head>
<title>$title</title>
</head>
<body>
<h1 align="center">$title</h1>
<p>
$content
</p>
EOM
;
    exit 0;
}

```

and here's the email.conf file
```

webmaster@thoughtfreeze.com
../index.html

```

any help would be appreciated, thanks!

---

### Post by rabbitfarmer on 2011-04-18
Anybody got anything? or something stupid i did wrong?

---

### Post by deathadder on 2011-04-18
Based on the couple of examples from the [mailers site]("http://www.boutell.com/email/") it looks like you need to point to the destination folder relative to the root of the site. So you'd probably want to change that to:
```
webmaster@thoughtfreeze.com
/

```
Just a thought though because my perl isn't that great =)

---

### Post by rabbitfarmer on 2011-04-18
still didn't work. thanks for the try though

---

### Post by rabbitfarmer on 2011-04-19
i firgured out that there was some kind of syntax error in my actual html page, which caused the cgi script to not find a recipient email address on the page. all solved now!

---

