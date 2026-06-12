---
title: "conditionally removing newlines in text files"
date: 2009-02-22
forum: Programming Talk
---

### Post by MetroPietro on 2009-02-22
Hi, I am decidedly not a programmer, but I have the same need: to strip newlines from Project Gutenberg .txt files. I have read this series of exchanges and have no idea how I would execute the Perl script described here. This is my guess:
1. copy the script into Gedit. For simplicity, save it in the same directory as the Gutenberg .txt file. I named it: rm_newline.pl
2. Make it executable:
sudo chmod 755 rm_newline.pl
3? Execute on the file 600.txt (the Dostoevsky text)?
perl -p rm_newline.pl 600.txt

Clearly that does not work. So it seems that Perl scripts cannot be run like shell scripts from the command line (I have no way of verifying or denying this; manpages, Google, Wikipedia do not answer such a fundamental question). Do I have to compile the script? Do I have to invoke it from something other than the command line? A step-by-step usage example would be most helpful.

---

### Post by snova on 2009-02-22
> **MetroPietro said:**
> Do I have to compile the script?

Scripts are not compiled.

> Do I have to invoke it from something other than the command line?

Anything can be executed from the command line, some things can *only* be run that way.

I'm not a Perl expert, but I believe these programs are expecting the text file on stdin:

```
perl -p rm_newline.pl < 600.txt
```

The -p argument may also be incorrect, try it with/without.

---

### Post by slavik on 2009-02-22
made a new thread for you.

original discussion in: [http://ubuntuforums.org/showthread.php?t=593075](http://ubuntuforums.org/showthread.php?t=593075)

try not to resurrect all threads as people might not read your problem.

---

### Post by MetroPietro on 2009-02-23
Thanks for the guidance thus far. I have tried both:
```
perl -p rm_newline.pl < 600.txt

```
and```
perl rm_newline.pl < 600.txt

```
with the same return:
```
Use of uninitialized value $1 in concatenation (.) or string at rm_newline.pl line 9, <> line 2.
...
Use of uninitialized value $1 in concatenation (.) or string at rm_newline.pl line 9, <> line 4720.

```
So, again, the perl script from the previous thread is:
```
#!/usr/bin/perl
use warnings;
use strict;

while (<>) {
$_ =~ s/
$//g;
if ($_ =~ /^$/) { print "\n\n"; }
else { $_ =~ /(.*)\n/; print "$1 "; }
}
```
From what I have read, there are certain situations in which perl initializes values of $1, $2, etc, and instances where you need to explicitly use the 'my' to initialize a variable. That is as far as I can understand this issue; I am basically flying blind.

---

### Post by unutbu on 2009-02-23
```
#!/usr/bin/perl 
use strict;
use warnings;
while (<>) {
    $_ =~ s/\r$//g;
    if ($_ =~ /^$/) { print "\n\n"; }
    else { $_ =~ /(.*)\n/; print "$1 "; }
}

```

Use it like this:```

rm_newline.pl < 13437.txt > 13437_0.txt
```

---

