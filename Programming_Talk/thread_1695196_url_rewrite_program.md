---
title: "url rewrite program"
date: 2011-02-25
forum: Programming Talk
---

### Post by sartic on 2011-02-25
I wrote my own url rewrite program for squid. It works on standard input, but I can not understand why is not working when I put url_rewrite_program line in squid .conf. I see my program spawned in memory but squid is bypassing it. Any hints?

---

### Post by sartic on 2011-02-26
I tried even width this script and change my program to catch url from cmd line.

#!/usr/bin/perl
$|=1;
while (<>) {
    @X = split;
    $url = $X[0];
    system "/home/sartic/squid_redirect $url";
}

Same thing squid spawns redirectors and bypass it?!

---

### Post by gmargo on 2011-02-26
The url_rewrite_program reads from stdin and writes the (possibly modified) url to stdout.

So here's the world's simplest do-nothing url_rewrite_program:
```

#!/usr/bin/perl -w
use strict;
use warnings;

$| = 1;

while (<>)
{
    print;
}

```And here's a simple url_rewrite_program that logs the URLs to a file:
```

#!/usr/bin/perl -w
use strict;
use warnings;

open(my $log, ">>", "/tmp/url.log.txt") || die("Cannot open output file: $!");
select $log;   $| = 1;
select STDOUT; $| = 1;

while (<>)
{
    my @parts = split;
    my $url = $parts[0];
    my $now = localtime;
    print $log "$now: $url\n";
    print "$url\n";
}

```

---

### Post by sartic on 2011-02-27
Thx 4 working scripts :)
I am still stumbled why my program is not running as...

I recompiled for Win port of Squid and program works. Linux binary just waits in memory width "unix_stream_data_wait"

---

### Post by sartic on 2011-03-09
Program finally works but width 2 problems.

1. program is locked when is called from daemon squid. If I stop and start manually squid it works.
2. program can not write to file (my log). It works when is not called by squid.

Same app(code) works great under win. 

Is there way to kill and start squid from script? Sudo is owned by root (damn sudo :) (problem #1)
For problem #2 I checked compiled file permissions (all read and write for user)

---

### Post by gmargo on 2011-03-09
Can't help without seeing your code.

---

### Post by sartic on 2011-03-14
> **gmargo said:**
> Can't help without seeing your code.

Code is simple I need ideas outside of my code. It works perfect when is called from xterm ;)

Problem #1 I am handling width
sudo killall -HUP my_redirector
...for now.
Still stumble why is my program locked when is called from squid as service.
Problem #2 is unsolved still..

---

### Post by sartic on 2011-03-14
Finally solved problem #2.
I can write only to file in folder that is own by group "proxy".

Still stumbling on #1.

---

### Post by sartic on 2011-04-18
I think i solved number #1 I will test it 24h.

Even files that are only read by my redirector have to be in folder that is own by proxy/proxy.

---

### Post by sartic on 2011-06-25
Program works great. Finally i have something like adblock plus cache and more for LANs ;)

And now lnx & win (bad translated by google):

[http://translate.google.com/translate?js=n&prev=_t&hl=hr&ie=UTF-8&layout=2&eotf=1&sl=hr&tl=en&u=http%3A%2F%2Fendrigo.com%2Fforum%2Findex.php%3Ftopic%3D162.0](http://translate.google.com/translate?js=n&prev=_t&hl=hr&ie=UTF-8&layout=2&eotf=1&sl=hr&tl=en&u=http%3A%2F%2Fendrigo.com%2Fforum%2Findex.php%3Ftopic%3D162.0)

After first final I had only one problem; squid shuts down in 8am (logs ?) and forgets redirectors. I solved this problem width another watchdog ;)

---

