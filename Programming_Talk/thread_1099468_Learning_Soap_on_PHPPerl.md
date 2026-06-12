---
title: "Learning Soap on PHP/Perl"
date: 2009-03-18
forum: Programming Talk
---

### Post by Johnsie on 2009-03-18
Hi, I need to write a Soap client for work and I'm trying to try some basic stuff before I write it.

Is there anything special I need to do do get the following code working?

> 

  #!perl -w

  use SOAP::Lite;

  my $soap = SOAP::Lite
    -> uri('http://www.soaplite.com/Temperatures')
    -> proxy('http://services.soaplite.com/temper.cgi');

  print $soap
    -> c2f(37.5)
    -> result;





The function on the server is a simple function to convert celsius to fahrenheit.

A php client would also be useful. Thanks to anyone who can help,

Johnsie

---

### Post by Johnsie on 2009-03-18
I'm getting the following error messages:

> 
tester@postalhub:/var/www/training/soap$ ./soap.pl
Warning: unknown mime-type for "Content-type: text/html\r\n\r\n" -- using "application/octet-stream"
Error: no such file "Content-type: text/html\r\n\r\n"
: command not found
Warning: unknown mime-type for "Hello there!<br />\nJust testing some things.<br />\n" -- using "application/octet-stream"
Error: no such file "Hello there!<br />\nJust testing some things.<br />\n"
: command not found
./soap.pl: line 4: use: command not found
: command not found
: command not found
./soap.pl: line 6: my: command not found
./soap.pl: line 7: syntax error near unexpected token `('
'/soap.pl: line 7: `    -> uri('http://www.soaplite.com/Temperatures')


---

