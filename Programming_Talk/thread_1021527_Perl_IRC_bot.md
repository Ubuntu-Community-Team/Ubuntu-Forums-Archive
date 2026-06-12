---
title: "Perl IRC bot"
date: 2008-12-25
forum: Programming Talk
---

### Post by jayk121121 on 2008-12-25
I am having trouble with an irc bot program that I got from the Linux Format Special: Code It! When I start it, it sits there and does nothing, with no output even though I put multiple print statements inside it. I did install the "libnet-irc-perl" package, so it shouldn't be a problem with not having Net::IRC. Also, the basic hello world program works, so it is not a problem with perl itself. Here is the program:

```
use Net::IRC;

print "Script started.";

$server = 'irc.freenode.net';
$channel = '-----';
$botnick = '-----';
$password = '-----';
$botadmin = '-----';

$irc = new Net::IRC;

$conn = $irc->newconn(Nick => $botnick,
	Server => $server, Port => 6667);

$conn->add_global_handler('376', \&on_connect);
$conn->add_global_handler('disconnect', \&on_disconnect);
$conn->add_global_handler('kick', \&on_kick);
$conn->add_global_handler('msg', \&on_msg);

$irc->start;

sub on_connect {
	$self = shift;
	$self->privmsg('nickserv', "identify $password");
	$self->join($channel);
	$self->privmsg($channel, "Lo! I'm just a silent bot.");
	print "Connected to channel.";
}

sub on_disconnect {
	$self = shift;
	$self->connect();
	print "Disconnected from channel.";
}

sub on_kick {
	$self = shift;
	$self->join($channel);
	$self->privmsg($channel, "Please don't kick me!");
	print "Kicked from channel.";
}

sub on_msg {
	$self = shift;
	$event = shift;

	if ($event->nick eq $botadmin) {
		foreach $arg ($event->args) {
			if ($arg =~ m/uptime/) {
				@output = `uptime`;
				foreach $line (@output) {
					$self->privmsg($botadmin, $line);
				}
			}
			if ($arg =~ m/df/) {
				@output = `df`;
				foreach $line (@output) {
					$self->privmsg($botadmin, $line);
				}
			}
		}
	}
	print "Received message.";
}
```

---

### Post by slavik on 2008-12-25
maybe it never connects to a channel for whatever reason

---

### Post by jayk121121 on 2008-12-25
The error occurs even before the channel stage. On the third line, I put a print statement, but for some reason it does not even reach that part. The only logical conclusion that I can draw is that there is a problem when loading Net::IRC, but I have installed that package.

Is there any to check whether or not a perl module is working, and if not, what exactly the problem is?

---

### Post by slavik on 2008-12-25
try the following:

$irc = new Net::IRC or die $!;

---

### Post by jayk121121 on 2008-12-25
That worked (meaning that it did not sit there doing nothing; it returned me to the command line after it was done). So that means that it can load Net::IRC. But why was it not able to get to the third line of my script?

Edit: It works when I put it in a separate file. It does make any difference when I replace that line in the script.

---

### Post by iansyngin on 2009-03-04
for what it's worth, I have got this bot running. I have it connecting to an ftp site, pulling down a file and running a program on the computer.
i'd like to get a better grasp on perl but don't really know where to start.
I could share code with anyone if they are interested.

One feature i'd like to implement is this.
when i leave computer, i want to make the Bot an OP. I can simply do this.
However, at another location, io then want to instruct the bot to hand back op privelages to my normal account. Anyone got some suggestions how i'd go about doing this.

Ian

---

### Post by Aaron850679 on 2009-05-20
add

```
use strict;
```

and make all variables global using

```
my $var = "blah";
or for mass
my ($nick,$server,$blah);
```

---

