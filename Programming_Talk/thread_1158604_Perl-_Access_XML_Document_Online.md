---
title: "Perl- Access XML Document Online"
date: 2009-05-13
forum: Programming Talk
---

### Post by Holmes89 on 2009-05-13
I'm kind of new to Perl and had a question regarding accessing an online file. If I want to access an XML sheet how to I access it with Perl. I've tried downloading the file with wget but it won't save. So any ideas? Thanks in advance.

---

### Post by myrtle1908 on 2009-05-13
Have a look at the LWP modules.  A **very** basic example of how to grab something off of the web follows:-

```
use strict;
use warnings;
use LWP::Simple;

my $url = 'http://somewhere.com/somefile.xml';
my $xml = get($url);
die "Can't connect to $url" unless defined $xml;

print $xml;
```

If you need to parse the XML then there are a great many parsers available for Perl.  Search around.

---

### Post by KyleBrandt on 2009-05-14
I like XML::Simple, but you are not going to have an easy time with this until you are comfortable with references in Perl.  If you don't know references well look at : [http://perldoc.perl.org/perlref.html]("http://perldoc.perl.org/perlref.html") .  These can be a little tricky if you have never worked with something like pointers in c , so be patient and read slow.

---

