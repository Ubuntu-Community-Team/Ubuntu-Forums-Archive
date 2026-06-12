---
title: "IRC Client in C/C++"
date: 2006-06-17
forum: Programming Talk
---

### Post by Christmas on 2006-06-17
I managed to try to make some simple C plugins for XChat and also a couple of Perl scripts, so I decided to try making a very basic C/C++ IRC client. Searched the net and found nothing, only a Perl example.
```
#!/usr/bin/perl -w
# irc.pl
# A simple IRC robot.
# Usage: perl irc.pl

use strict;

# We will use a raw socket to connect to the IRC server.
use IO::Socket;

# The server to connect to and our details.
my $server = "irc.freenode.net";
my $nick = "Homecoming";
my $login = "christmas";

# The channel which the bot will join.
my $channel = "#DSotM";

# Connect to the IRC server.
my $sock = new IO::Socket::INET(PeerAddr => $server,
                                PeerPort => 6667,
                                Proto => 'tcp') or
                                    die "Can't connect\n";

# Log on to the server.
print $sock "NICK $nick\r\n";
print $sock "USER $login 8 * :Viva Pink Floyd!\r\n";

# Read lines from the server until it tells us we have connected.
print "Connecting to irc.freenode.org...";
while (my $input = <$sock>) {
    # Check the numerical responses from the server.
    if ($input =~ /004/) {
        # We are now logged in.
	print "Connected.\n";
        last;
    }
    elsif ($input =~ /433/) {
        die "Nickname is already in use.";
    }
}

# Join the channel.
print $sock "JOIN $channel\r\n";

# Keep reading lines from the server.
while (my $input = <$sock>) {
    chop $input;
    if ($input =~ /^PING(.*)$/i) {
        # We must respond to PINGs to avoid being disconnected.
        print $sock "PONG $1\r\n";
    }
    else {
        # Print the raw line received by the bot.
        print "viva viva viva$input\n";
    }
}
```
I want to make something like this, but in C or C++, but I don't know what headers do I need and how to use them. I think I looked over more than 5 irc clients and bot sources (XChat, LostIRC, BitchX and even Eggdrop) but couldn't understand how should I start this. I'm looking for a tutorial or a small example.
Any help would be greatly appreciated, thanks!

---

### Post by nagilum on 2006-06-18
IRC is quite simple text-based protocol, so all you need are the socket functions to connect to the server (see 'man 2 socket', assuming you have the dev-manpages installed) and some string handling to parse the responses (e.g. strtok). That's basically it.
Which headers you need is stated in the manpages for each function (connect, select etc.). The Perl example you posted is probably as simple as it can get. You can try to write your C client along this example, although it will probably get way longer thanks to the manual string handling.

There's some good (although lengthy) documentation available from the GLIBC software. It explains the networking stuff as well as the string handling in detail, i.e. all you need for a basic IRC client.
[http://www.gnu.org/software/libc/manual/html_node/Sockets.html](http://www.gnu.org/software/libc/manual/html_node/Sockets.html)
[http://www.gnu.org/software/libc/manual/html_node/String-and-Array-Utilities.html](http://www.gnu.org/software/libc/manual/html_node/String-and-Array-Utilities.html)

---

### Post by ynef on 2006-06-19
In addition, you'll also need to study the IRC standard, outlined in RFC 1459: [http://www.irchelp.org/irchelp/rfc/rfc.html](http://www.irchelp.org/irchelp/rfc/rfc.html)

I'm writing a chat system myself this summer, at least that's the plan, and it seems really simple. I would, however, recommend that you use C++ and take advantage of its string handling and get hold of a reasonable socket library -- unless you want to write one yourself. System calls are just begging to be wrapped in a nice class...

---

### Post by Christmas on 2006-06-21
OK guys thanks, I'll try the web addresses you pointed me at.

---

