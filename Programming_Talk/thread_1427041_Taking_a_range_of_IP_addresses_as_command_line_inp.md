---
title: "Taking a range of IP addresses as command line input."
date: 2010-03-11
forum: Programming Talk
---

### Post by Stev0 on 2010-03-11
Working on a new project in python, and I decided I wanted to add some complexity too it. The idea was sound, but when I actually went to code it, I realized I had no idea what I was doing :) 

So I have a pretty solid understanding of things like sys.argv and using the optparser and getopt modules. However I'm not how to go about accepting a range of numbers as a command line argument that can be used later in the program. Essentially I'd like to allow for a range of IP addresses to be passed, something like 192.168.1.1-99. I understand how to store that argument, but would it be a string, an int, or a long? In addition, how does one store that argument in some sort of variable that I can later use in a function, but then increment the numbers, starting with the first one, and ending with the last? IE I'd like to open up http connections to every IP address in the range. I've got the jist of making the http connections, just never worked with a range of numbers in python before, nor have I worked with command line arguments.

I'm kind of torn between python 3.1 and 2.6 for this, as I was looking at the ipaddr module in 3.1, but I'm not sure if that module has what I'm looking for. Can I do this in 2.6?

---

### Post by myrtle1908 on 2010-03-11
I haven't dabbled much in Python but the principle is the same in most any language.  Here's a starter in Perl.

```
use strict;
use warnings;

my $mask = $ARGV[0]; # store the argument, normally you would do some input checking here
my @ip = split(/\./, $mask); # split on full-stop/period
my @range = split(/\-/, $ip[3]); # grab the range
for ($range[0] .. $range[1]) { # loop through the range
  print "$ip[0].$ip[1].$ip[2].$_\n";
}

```

I'm sure a Python person can help you better than I can.

Obviously my script will only work with ranges provided in the fourth quadrant.

Good luck.

---

### Post by ssam on 2010-03-11
generally commandline arguments arrive as strings, and its up to you to convert them to other datatypes if you want.

if you program is very simple you can just use sys.argv, but if there are more than a few options use optparser or getopt.

once you have the string eg, "192.168.1.1-5", you split()
```

s = "192.168.1.1-5"
ip_parts = []
for part in s.split("."):
  if "-" in part:
    min, max = part.split("-")
    ip_parts.append(xrange(int(min), int(max)+1)) # need to add one as range(1,5) -> 1,2,3,4
  else:
    ip_parts.append([int(part)])

```
then use itertools' product to generate all the ip list.
```

import itertools
ip_addresses = itertools.product(*ip_parts)
for ip_address in ip_addresses:
  print "%d.%d.%d.%d" % ip_address

```

this will work with for case where more than one part has a range. using the itertools and for loop means that the address are only generated as needed, not all at once. so 1-255.1-255.1-255.1-255 will not use up all you ram.

---

### Post by Stev0 on 2010-03-11
Thanks. Exactly what I was looking for. You are a gentleman and a scholar.

---

