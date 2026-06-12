---
title: "Perl and inet_ntoa issues"
date: 2007-09-01
forum: Programming Talk
---

### Post by raevin on 2007-09-01
Searched Google, here, and everywhere else I could think of, with no help...

I have Perl installed from the install of Kubuntu, and everything was running fine earlier this week, but ever since like...a few days ago, whenever "inet_ntoa" is called in a Perl script, it won't work.

Main focus of this is in the CGIProxy script, but even testing it with a very simple script yields no success.

Here's the error:

```

eric@eric-desktop:/var/www$ ./test.pl www.google.com
www.l.google.com => 64.233.167.99 64.233.167.104 64.233.167.147
Bad arg length for Socket::inet_ntoa, length is 16, should be 4 at ./test.pl line 14.

```

And here's the code:

```

#!/usr/bin/perl
# hostaddrs - canonize name and show addresses
use Socket;
use Net::hostent;
$name = shift;
if ($hent = gethostbyname($name)) {
    $name      = $hent->name;                # in case different
    $addr_ref  = $hent->addr_list;
    @addresses = map { inet_ntoa($_) } @$addr_ref;
}
print "$name => @addresses\n";

$i = inet_ntoa(inet_aton($name));
$i2 = inet_ntoa($name);

print "$name (using inet_ntoa) => $i\n";
print "$name (strict inet_ntoa) => $i2\n";

```

I installed the IO::Socket package, and it still did no good...and, I'm really just at a loss now as to why this is erroring out.

I've even went to recompile Perl on my own using the source tarball from Perl's website, and I can't do that (getting an error saying makedepend is already running...and I don't see how.)

If anyone can help me, this would be much appreciated.

---

### Post by slavik on 2007-09-01
[http://perldoc.perl.org/Socket.html](http://perldoc.perl.org/Socket.html)

should help

---

### Post by raevin on 2007-09-01
> **slavik said:**
> [http://perldoc.perl.org/Socket.html](http://perldoc.perl.org/Socket.html)

should help

That doesn't tell me anything I haven't already done, tried or read about though...

Everything was working fine earlier...so I guess I'm more just wondering how could I reinstall the Perl package to defaults (if possible.)

---

### Post by PaulFr on 2007-09-01
```
#!/usr/bin/perl -w
use strict;
use Socket;

my $ipdotted    = "209.209.220.3";
my $ipnetwork   = inet_aton($ipdotted);
my $revipdotted = inet_ntoa($ipnetwork);

print "$ipdotted converted and then back to $revipdotted \n";
exit 0;
``` works for me. You are of course aware that inet_aton only takes a dotted quad, i.e. xx.yy.zz.ww. If you want to use a name like *[www.google.com](www.google.com)*, you have to use gethostbyname or similar to resolve the name into a dotted quad before you use inet_aton.

Correction: gethostbyname will already give you the correct network order dotted quad, so you have to use inet_ntoa to make it a printable dotted quad string. The first part of your code does that using map of inet_ntoa on the addresses returned by gethostbyname.

---

