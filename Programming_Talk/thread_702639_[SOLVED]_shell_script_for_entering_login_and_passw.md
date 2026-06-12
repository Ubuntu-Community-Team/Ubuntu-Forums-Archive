---
title: "[SOLVED] shell script for entering login and password"
date: 2008-02-20
forum: Programming Talk
---

### Post by adityakavoor on 2008-02-20
I need to write a shell script for renewing the IP address on my modem.

These are the steps : 

1 . telnet 192.168.1.1

2. login : foo (say)
3. password: foo (say)

4. pppoe set transport 1 disabled

5. pppoe set transport 1 enabled

How to write a script which automatically enters the login and 

password and executes the 2 commands ??

I dont want to enter the login and password every time .. 


Please help ...

---

### Post by WW on 2008-02-20
I haven't used it, but this sounds like a job for **[expect](http://en.wikipedia.org/wiki/Expect)**. Check out the first example on the wikipedia page.  (See also the **[expect home page](http://expect.nist.gov/)**.)

---

### Post by adityakavoor on 2008-02-20
Thanks , Will give a try

---

### Post by scruff on 2008-02-20
Expect is really simple. I write a lot of automated login-do-something scripts at work though and I prefer Perl with [Net::Telnet]("http://search.cpan.org/~jrogers/Net-Telnet-3.03/lib/Net/Telnet.pm").

---

### Post by supirman on 2008-02-20
Here ya go.  See if this works for you.

[PHP]

#!/usr/bin/env expect

set username yourUserNameHere
set pass yourPasswordHere
set host theIpAddressToConnectTo

spawn telnet ${host}

expect -re "login:"
send "${username}\r"

expect "Password:"
send "${pass}\r"

expect -re "$"

send "pppoe set transport 1 disabled\r"
expect -re "$"
send "pppoe set transport 1 enabled\r"

expect -re "$"
send "exit\r"
expect eof

[/PHP]


Put that into a file, say renew_ip.  Give it execute permissions: chmod +x renew_ip .   Then run it:  ./renew_ip

Also, if you don't have expect, just: sudo apt-get install expect

---

### Post by adityakavoor on 2008-02-21
supirman :popcorn:

Thanks a lot. Works like a charm. :) :)

But I get an error message at the end, but I dont think it has any relevence . 


```
Syntax error - use '?' to see valid completions
```

This error doesnt matter to me as I get the job done.

Thanks again . :guitar:

---

### Post by mzakaria on 2012-10-27
Works with SSH as well. Just replace it instead of talnet. Brilliant!:KS

---

