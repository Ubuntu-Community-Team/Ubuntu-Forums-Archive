---
title: "Perl: receiving the output of a command from a Net::Telnet connection"
date: 2013-01-08
forum: Programming Talk
---

### Post by marcelbo on 2013-01-08
Hi everybody,

I am writing a Perl script to automate the receiving of measured values from a scale. It is a Mettler Toledo IND 780 scale terminal which allows a telnet connection, that can be used to setup the scales and retrieve the measured values.

Using a telnet connection with a hyper terminal i can login and execute the command to get the values:

[IMG]https://dl.dropbox.com/u/24226413/perl/putty.PNG[/IMG]

[IMG]https://dl.dropbox.com/u/24226413/perl/putty2.PNG[/IMG]
(again copied to notepad++, showing all characters)

the first login didn't work but nevermind.

with the the command:

read wt0101 wt0201

I request the values of the scales.

00R001~ is just a formatted header with a counter, 20.14~ and 190.0~ are the values of the scales.
These two values are what I want to get with the perl script, best without the ~:

```
use strict;
use warnings;
use Net::Telnet ();
my $username="admin";
my $password="admin";
my $t;
my $s;
$t = new Net::Telnet(Host =>"192.168.0.1", Timeout => 5,Port => "1701", Prompt => '/>\$ $/');
 $t->waitfor('/Ready for user/i');
 $t->print("user admin");
 $t->waitfor('/Access OK/');
 $s=$t->print("read wt0101");
 print "result=", $s;
```With that i get result = 1
I'm looking for a way to get the text result, which should be 00Rxxx~ value1 value2, or even better just both values and save it in an array so that I can put all measured values in a file after the measuring cycle is finished.

I hope I could explain my problem in a proper way. I didn't do much programming yet, so I'am not quite experienced.

Thanks in advance!
Marcel

---

### Post by trent.josephsen on 2013-01-08
print() writes to a connection; it does not automatically capture any response. You'll need to use another method for that, like get() or getline().

---

### Post by marcelbo on 2013-01-09
I tried both get() and getline(). But those are for used for files, aren't they? 
With waitfor(..) I also get 1 as result ...

---

### Post by trent.josephsen on 2013-01-09
Learn to use documentation.

[http://search.cpan.org/~jrogers/Net-Telnet-3.03/lib/Net/Telnet.pm](http://search.cpan.org/~jrogers/Net-Telnet-3.03/lib/Net/Telnet.pm)

> print - write to object

        $ok = $obj->print(@list);

    This method writes @list followed by the output_record_separator to the open object and **returns 1 if all data was successfully written**. On time-out or other failures, the error mode action is performed. See errmode().

I'm not sure why you were expecting $t->print(...) to return anything other than a status code indicating whether or not it succeeded. waitfor() is the same thing; it returns a status code. The functions in Net::Telnet that return data read from the connection are get, getline, getlines and lastline.

---

