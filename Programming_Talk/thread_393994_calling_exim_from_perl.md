---
title: "calling exim from perl"
date: 2007-03-26
forum: Programming Talk
---

### Post by jmc1024 on 2007-03-26
Is there anything special to calling exim from perl?  I'm working on a cgi-bin script
to go with squidGaurd to email an admin when a site was blocked:

#!/usr/bin/perl -w
# blocked.cgi --

use CGI;
my $sendmail = "/usr/sbin/exim -bm";

print "Content-type: text/html\n\n";
print <<"BOF";
<HTML>
<HEAD>
<TITLE>BLOCKED!</TITLE>
</HEAD>
<BODY>
<H1>BLOCKED!</H1>
BOF

$query = new CGI;
$site = $query->param('url');
$user = $query->param('clientaddr');
$message = "\nThis message was sent through a www-email gateway\n\nAccess to the site $site was blocked for $user\n\n";

# Open a pipe to the sendmail program
open(SENDMAIL, "|$sendmail") or die "Cannot open $sendmail: $!";
# Use the highly convenient <<EOM notation to include the message
# in this script more or less as it will actually appear
print SENDMAIL "To: admin\@homesite.com\n";
print SENDMAIL "Cc: admin2\@homesite.com\n";
print SENDMAIL "Subject: Blocked site access attempt\n";
print SENDMAIL "Reply-To: admin\@homesite.com\n";
print SENDMAIL "Supposedly-From: admin\@homesite.com\n";
print SENDMAIL $message;
close(SENDMAIL);

print "\nAccess to the site ", $query->param('url')," was blocked for ", $query->param('clientaddr'), ".<br>";
print <<"EOF";
</BODY>
</HTML>
EOF

---

