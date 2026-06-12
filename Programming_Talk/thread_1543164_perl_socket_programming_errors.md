---
title: "perl socket programming errors"
date: 2010-07-31
forum: Programming Talk
---

### Post by tjwilson1973 on 2010-07-31
I am new to perl and am experimenting with sockets. When I try to open a socket using sockaddr_in($port, $iaddr), I get this message: Bad arg length for Socket::pack_sockaddr_in, length is 0, should be 4 at /usr/lib/perl/5.10/Socket.pm line 214. I understand this may have something to do with perl failing to handle an IPv6 address. Is this true? If so, how do I fix this?

Here is the code I am trying to run. This is an adaptation of something similar I did using python to connect to the flight schedule server at Philadelphia International Airport and get all scheduled flights.

code:

#! /usr/bin/perl -w
# client1.pl - a simple client
#----------------

use strict;
use Socket;

# initialize host and port
my $host = shift || 'www.phl.org/cgi-bin/fidsarrival.pl';
my $port = shift || 80;

my $proto = getprotobyname('tcp');

# get the port address
my $iaddr = inet_aton($host);
my $paddr = sockaddr_in($port, $iaddr);
# create the socket, connect to the port
socket(SOCKET, PF_INET, SOCK_STREAM, $proto)
or die "socket: $!";
connect(SOCKET, $paddr) or die "connect: $!";

my $line;
while ($line = $paddr)
{
	print $line;
}
close SOCKET or die "close: $!"; 

Please help!

---

### Post by Some Penguin on 2010-07-31
First reflex:

'www.phl.org/cgi-bin/fidsarrival.pl';

is not a valid hostname.

---

### Post by tjwilson1973 on 2010-07-31
How about: 

my $host = shift || 'http://www.phl.org/cgi-bin/fidsarrival.pl';

---

### Post by tjwilson1973 on 2010-07-31
I get the same error with this initially.

---

### Post by Some Penguin on 2010-07-31
The host... should be a *hostname*, like 'www.phl.org' without any of the preceding protocol information or trailing protocol-specific foo.

---

