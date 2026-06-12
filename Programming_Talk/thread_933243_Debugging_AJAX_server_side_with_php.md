---
title: "Debugging AJAX server side with php"
date: 2008-09-29
forum: Programming Talk
---

### Post by matthewboh on 2008-09-29
I've got some code that I am using to alter for my own - and it uses AJAX and Json - however, when you use Json, you apparently can't use print or echo to do debugging on the server side in PHP.  I found a nifty package called FirePHP that's an extension of Firebug, but that requires PHP 5.2.5 which hasn't been backported.

Does anyone have a suggestion about server side AJAX using Json debugging tools?

Thanks

---

### Post by pmasiar on 2008-09-29
... because AJAX/Json runs not on server but in client's browser?

---

### Post by Mindzai on 2008-09-29
What sort of thing are you needing to debug? Surely any script you run via an ajax request either returns something back to the client or performs a function on the server like updating a database which you can check?

If you need to debug your php, just run the script directly in a browser passing in the data directly via post or get rather than using javascript. If you need to debug the javascript you can do that client side in a number of ways, easiest probably being alert().

Unless i'm misunderstanding the problem?

---

### Post by matthewboh on 2008-09-29
What I'm trying to do is find out where my code is bombing in the php script that runs on the server.

Basically, I send a request to the server to have it lookup a username / password combination - and it's just not working.  Basically, I borrowed code that has worked flawlessly.  The only change I've made is in the database name - which shouldn't harm it.

Anyway, you can't use echo or print to put out messages because it breaks the json headers, so I've been trying to use PHPEclipse and Xdebug - but just running into more problems with trying to set the parameters to run it.  I've been googling most of the day, but haven't found the secret to debugging PHP code that's called with AJAX.

---

### Post by supirman on 2008-09-29
One simple way: write your debug output to a file so you can then go and examine it.

---

### Post by matthewboh on 2008-09-30
Found a way!  Using Firebug 1.2.1 and PHPEclipse together.  There's also FirePHP, but that requires PHP 5.2.5 and I just don't feel like installing that from source.  Thanks everyone!

---

### Post by Mickeysofine1972 on 2008-09-30
I do this at work:

tail -f /var/www/name-of-your-site-folder/log/error_log

then I open fire bug and watch whats being sent and received via the xml request.

between those two you can usually see whats going on.

Mike

---

### Post by drubin on 2008-09-30
> **Mickeysofine1972 said:**
> I do this at work:

tail -f /var/www/name-of-your-site-folder/log/error_log

then I open fire bug and watch whats being sent and received via the xml request.

between those two you can usually see whats going on.

Mike
Ye at work I have a log tailer running on the one pc perminatly..  

Use this instead of echo/print to view debugging info.  [www.php.net/error_log](www.php.net/error_log)

---

### Post by Jefferythewind on 2011-07-01
Hi,
  I came to this thread because I have the same problem.  If you are using Ubuntu server with Apache, then you can use something like this in your php code to debug:
```
function() or error_log("error message here");
```
then you can find these error messages in the /var/log/apache2/error.log file.  access this file by using the command line code:
```
tail /var/log/apache2/error.log
```

---

