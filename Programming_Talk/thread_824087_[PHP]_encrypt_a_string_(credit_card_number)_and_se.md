---
title: "[PHP] encrypt a string (credit card number) and send through GET"
date: 2008-06-09
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-06-09
I've been searching and I can't seem to find what I need!

Would any of you PHP wizards know how to help me?

I think what I want is to be able to encrypt a credit card number using a function and then send that over GET. It's just an extra precaution... its going to be inside SSL.

So I was thinking something like:

$string = encrypt("my ccn", "my key");

and then send that over GET

Any ideas?

Thanks so much!

---

### Post by altonbr on 2008-06-09
> **oodlesOfmoodles said:**
> I've been searching and I can't seem to find what I need!

Would any of you PHP wizards know how to help me?

I think what I want is to be able to encrypt a credit card number using a function and then send that over GET. It's just an extra precaution... its going to be inside SSL.

So I was thinking something like:

$string = encrypt("my ccn", "my key");

and then send that over GET

Any ideas?

Thanks so much!

SSL or not, you should never send a credit card number over GET, ever. Even if it is encrypted one way, which is not what you are asking (you are asking for 2-way, meaning it can be unencrypted using a private key).

---

### Post by oodlesOfmoodles on 2008-06-09
Thanks for replying!

Ok then.
How about over POST?

---

### Post by altonbr on 2008-06-09
Well, there are some pretty good libraries out there. I wouldn't recommend programming your own ONLY based on the fact that you may not produce random numbers correctly and have an easily guessable key.

Here's an OOP library: [http://trac.kohanaphp.com/browser/trunk/system/libraries/Encrypt.php](http://trac.kohanaphp.com/browser/trunk/system/libraries/Encrypt.php) (it has encoding and decoding)

Here's the documentation for it: [http://docs.kohanaphp.com/libraries/encrypt](http://docs.kohanaphp.com/libraries/encrypt)

Just be careful in using that fully as it depends on a full PHP framework. I'm sure you could modify one or two lines to get it independent.

---

### Post by oodlesOfmoodles on 2008-06-09
> **altonbr said:**
> Well, there are some pretty good libraries out there. I wouldn't recommend programming your own ONLY based on the fact that you may not produce random numbers correctly and have an easily guessable key.

Here's an OOP library: [http://trac.kohanaphp.com/browser/trunk/system/libraries/Encrypt.php](http://trac.kohanaphp.com/browser/trunk/system/libraries/Encrypt.php) (it has encoding and decoding)

Here's the documentation for it: [http://docs.kohanaphp.com/libraries/encrypt](http://docs.kohanaphp.com/libraries/encrypt)

Just be careful in using that fully as it depends on a full PHP framework. I'm sure you could modify one or two lines to get it independent.
I appreciate you taking the time to help.

In your opinion, would it even be necessary to encrypt a ccn if it was sent through POST over SSL?

Thanks again!

---

### Post by NormR2 on 2008-06-09
The difference between a GET and a POST is that the data for a POST is sent following a newline after the request header. Otherwise if someone can see the traffic, they can see the data for either a GET or a POST.

---

### Post by oodlesOfmoodles on 2008-06-09
> **NormR2 said:**
> The difference between a GET and a POST is that the data for a POST is sent following a newline after the request header. Otherwise if someone can see the traffic, they can see the data for either a GET or a POST.
Thanks, didn't know that.

What should I do then?

---

### Post by altonbr on 2008-06-09
> **NormR2 said:**
> The difference between a GET and a POST is that the data for a POST is sent following a newline after the request header. Otherwise if someone can see the traffic, they can see the data for either a GET or a POST.

Which is exactly why you should use SSL.

> **oodlesOfmoodles said:**
> Thanks, didn't know that.

What should I do then?

Still encrypt it.

$_POST is at least invisible to the naked eye, unlike $_GET. With $_GET, someone could send spam e-mail from your site, asking users to send them the $_GET string, take screenshots, etc. Plus, SSL isn't fool-proof, so if someone could sniff the connection, there goes that user's credit card number. Encrypting via POST just adds that much more security.

Here is a little snippet from an e-mail I found online, related to this matter: [http://lists.evolt.org/archive/Week-of-Mon-20020304/105704.html](http://lists.evolt.org/archive/Week-of-Mon-20020304/105704.html)
> You can encrypt the card numbers on the server side (as they go
into the db) after accepting the form post over an SSL connection, then
decrypt them on retrieval and send them back to the client (if your
application provides for this) over the SSL connection as well.  While it's
not completely fool-proof (your method of encryption will most likely be the
"weakest link" here) it is relatively secure as long as the web server/db
server is secure as well.


It links to an ONLamp.com article about PHP Encryption: [http://www.onlamp.com/pub/a/php/2001/07/26/encrypt.html](http://www.onlamp.com/pub/a/php/2001/07/26/encrypt.html)

I also found an article on PHP encryption by IBM: [http://www.ibm.com/developerworks/library/os-php-encrypt/index.html](http://www.ibm.com/developerworks/library/os-php-encrypt/index.html)

Good luck!

---

### Post by tamoneya on 2008-06-09
i think the standard method is to use cUrl: [http://curl.haxx.se/](http://curl.haxx.se/) and then use ssl and https for the transfer.

---

### Post by id1337x on 2008-06-09
I'd probably use SQL and I'd use like SHA for encryption. Sending over $_GET is definitely not advisable anybody could read it besides sending over $_POST isn't a great idea either.

---

### Post by babooka on 2008-06-09
I think you should start with a XOR encryption.


Basic binary mathematics, google for XOR

[http://www.go4expert.com/forums/showthread.php?t=5555]("http://www.go4expert.com/forums/showthread.php?t=5555")

---

### Post by tamoneya on 2008-06-09
> **babooka said:**
> I think you should start with a XOR encryption.


Basic binary mathematics, google for XOR

[http://www.go4expert.com/forums/showthread.php?t=5555]("http://www.go4expert.com/forums/showthread.php?t=5555")

that is easily crackable.  By watching just a handful of credit cards I could figure out what string you are xoring the card number with just based upon the fact that I know you are transmitting ascii numbers and they could only have a restricted value range.

---

### Post by altonbr on 2008-06-09
> **id1337x said:**
> I'd probably use SQL and I'd use like SHA for encryption. Sending over $_GET is definitely not advisable anybody could read it besides sending over $_POST isn't a great idea either.

How would you send the credit card number from the user to the server then? You need to send the variable somehow...

---

### Post by tamoneya on 2008-06-09
> **id1337x said:**
> I'd probably use SQL and I'd use like SHA for encryption. Sending over $_GET is definitely not advisable anybody could read it besides sending over $_POST isn't a great idea either.

one of the basic rules when working with credit cards is that you never store it anywhere on your servers.  You should just send directly to the authorization gateway through an encrypted connection.

---

### Post by altonbr on 2008-06-09
> **tamoneya said:**
> one of the basic rules when working with credit cards is that you never store it anywhere on your servers.  You should just send directly to the authorization gateway through an encrypted connection.

This is true however. Listen to him.

---

### Post by oodlesOfmoodles on 2008-06-10
Thanks for all your help guys. I'm learning a lot.

I've researched hashing (SHA1) and I'm pretty sure that there's no way to unhash something... isn't that the point? One way encrypting?

Anyway, I think that the credit card info is going to be sent directly to the processing company's website.

Are you suggesting that it should be sent directly to processing (through POST and SSL of course)?

Is it possible to send a binary string through POST anyway? I've seen the output and it looks like it would not play nice with POST or GET

I hope I've understood what you are all trying to say.

Thanks again for all your replies and help.

---

### Post by altonbr on 2008-06-10
> **oodlesOfmoodles said:**
> Thanks for all your help guys. I'm learning a lot.

I've researched hashing (SHA1) and I'm pretty sure that there's no way to unhash something... isn't that the point? One way encrypting?

Anyway, (btw I'm interning for a web company) I think that the credit card info is going to be sent directly to the processing company's website (it's for donations to a non-profit).

Are you suggesting that it should be sent directly to processing (through POST and SSL of course)?

Is it possible to send a binary string through POST anyway? I've seen the output and it looks like it would not play nice with POST or GET

I hope I've understood what you are all trying to say.

Thanks again for all your replies and help.

md5, sha1, etc. is all for one-way encrypting, yes. Do you understand its use though? Think saving a user's password with sha1. If the database is stolen, it'll be hard to reverse the hash, but it is still useful to the website  as they can test sha1($password) with that hash already in the DB.

POST, through SSL, directly to the payment gateway (ie: PayPal). Do not store credit card information on your computer, ever. Even if it is hash and salted and God himself made you encrypt it.

To send binary, read [http://ca.php.net/base64_encode](http://ca.php.net/base64_encode)
>  string base64_encode  ( string $data  )

Encodes the given data with base64.

This encoding is designed to make binary data survive transport through transport layers that are not 8-bit clean, such as mail bodies.

Base64-encoded data takes about 33% more space than the original data. 

---

### Post by tamoneya on 2008-06-10
> **oodlesOfmoodles said:**
> Thanks for all your help guys. I'm learning a lot.

I've researched hashing (SHA1) and I'm pretty sure that there's no way to unhash something... isn't that the point? One way encrypting?

Anyway, (btw I'm interning for a web company) I think that the credit card info is going to be sent directly to the processing company's website (it's for donations to a non-profit).

Are you suggesting that it should be sent directly to processing (through POST and SSL of course)?

Is it possible to send a binary string through POST anyway? I've seen the output and it looks like it would not play nice with POST or GET

I hope I've understood what you are all trying to say.

Thanks again for all your replies and help.


Yes that is what SHA1 does.  Because of that it is not the best idea to hash the credit card number because then when you send the hash the authentication gateway wont be able to figure out if it is a legit card number because they dont know the card number.  SHA1 hasing is what you would do with user passwords.  You would have a database of usernames and password hashes.  They would log in and you hash their password and make sure the hashes match.  THis way you dont store password in plaintext on your database.  You should get in contact with your authorization gateway.  I once did this is authorize.net and they provided nice sample code.  Here is their page.
[http://developer.authorize.net/samplecode/](http://developer.authorize.net/samplecode/)

I used the AIM-PHP code.

---

