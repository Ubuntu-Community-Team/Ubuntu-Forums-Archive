---
title: "How can I pass a value from one file to another in PHP?"
date: 2008-02-22
forum: Programming Talk
---

### Post by thenetduck on 2008-02-22
Hi I just would like to pass one string from one file to another in PHP Does anyone know how I can do this?:

bit confused. Thanks 

The Net Duck

---

### Post by lnostdal on 2008-02-22
ah, yes .. http is stateless and you are stuck

the two most common ways to handle this is to either store the data on the client and pass it along to the server on each request (via your URLs / GET) .. or use sessions (HTTP cookie-id <---> session data on server)

about sessions you have this as a reference of course:
[http://www.php.net/manual/en/ref.session.php](http://www.php.net/manual/en/ref.session.php)

..and some google searches bring up some php session tutorials .. this for instance: [http://www.tizag.com/phpT/phpsessions.php](http://www.tizag.com/phpT/phpsessions.php) (i don't know if it is the best one out there)

---

### Post by frankos44 on 2008-02-22
One way is to use sessions, I prefer this because sensitive data does not need to be passed between pages but are available to all pages if needed.:

# FILE 1
session_start();
$_SESSION['firstname'] = "Fred";
$_SESSION['surname'] = "Smith";
$_SESSION['age'] = 45;

# FILE2
session_start();
$firstname = $_SESSION['firstname'];
$surname = $_SESSION['surname'];
$age = $_SESSION['age'];
..

Also you can pass objects in the same way, this is a better method because a complete collection of data is bound to one entity thus the variable age can be used in different objects or even multiple instances of the same object. 

# FILE 1
require_once('..cgi-bin/objects/class.client.php')
session_start();
$oClient = new client;
$oClient->firstname = 'Fred';
$oClient->surname = 'Smith';
$oClient->age = 45;
$_SESSION['client'] = serialize($oClient);
..

# FILE 2
require_once('../cgi-bin/objects/class.client.php')
session_start();
$oClient = new client;
$oClient  = unserialize($_SESSION['client']);
..

Hope this helps

---

