---
title: "[PERL][SERVER] A bit of HTML problems.."
date: 2008-04-05
forum: Programming Talk
---

### Post by Petrock6 on 2008-04-05
```
#! /usr/bin/perl -w
# server0.pl
#--------------------

use strict;
use Socket;

print "Starting Saustin server..\n";
my $port = shift || 80;
my $proto = getprotobyname('tcp');

socket(SERVER, PF_INET, SOCK_STREAM, $proto) or die "socket: $!";
setsockopt(SERVER, SOL_SOCKET, SO_REUSEADDR, 1) or die "setsock: $!";

my $paddr = sockaddr_in($port, INADDR_ANY);

bind(SERVER, $paddr) or die "bind: $!";
listen(SERVER, SOMAXCONN) or die "listen: $!";
print "SERVER started on port $port\n";

my $client_addr;
while ($client_addr = accept(CLIENT, SERVER))
{
my ($client_port, $client_ip) = sockaddr_in($client_addr);
my $client_ipnum = inet_ntoa($client_ip);
my $client_host = gethostbyaddr($client_ip, AF_INET);
print "Connection from: $client_host","[$client_ipnum] \n";
print CLIENT "<html>";
print CLIENT "<head>";
print CLIENT "<title>Welcome to whatismyip.sytes.net</title>";
print CLIENT "</head>";
print CLIENT "<body bgcolor="#000000">";
print CLIENT "<FONT COLOR="WHITE">";
print CLIENT "<p>Hello, welcome to my IP finder service.</p>";
print CLIENT "<p>Starting Perl script..</p>";
print CLIENT "<p>Getting your IP information..</p>";
print CLIENT "<p>Your host/dns: <b>$client_host</b></p>";
print CLIENT "<p>Your IP: <b>$client_ipnum</b></p>";
print CLIENT "<p> Over time, you will see this get larger!</p>";
print CLIENT "</body>";
print CLIENT "</html>";
close CLIENT;
}
```

As you can see, at "<body bgcolor="#000000">
<FONT COLOR="WHITE">" if you try to compile it, it won't work, since you can't have more than 2 ""'s in one line.
Help?

---

### Post by tamoneya on 2008-04-05
use an escape character
 \"

---

### Post by Petrock6 on 2008-04-05
> **tamoneya said:**
> use an escape character
 \"

I'm kinda new to PERL..
Thanks a bunch.

---

### Post by tamoneya on 2008-04-05
glad to help.  Hope you have fun with perl and ubuntu

---

### Post by pmasiar on 2008-04-06
When generating such big text in Perl, heredoc is much more readable, but even better solution is using templating system. HtmlTmlp - HTMLTemplate is very simple (simplest templating system I've seen). You want to read up on Model-View-Controller design pattern, to separate presentation layer from your logic. CGI::Application is simple but powerful framework, will save you lot of time.

Even better will be of course to swicth to more modern and future-proof language, like Python, and use Django or TurboGears framework. :-)

---

