---
title: "PHP cURL problem with Javascript redirect"
date: 2010-03-04
forum: Programming Talk
---

### Post by Mattza on 2010-03-04
Hi,
im working on a script that should via cURL go to a specific homepage, login and the parse some info based on a search. The basic login with SSL is solved and i get the cookie etc. BUT when cURL do a GET a Javascript is doing a redirect to the final page that the info is, but when i try to parse the info into text i only get the redirect script!? I know this is a common problem with PHP/cURL when a javascript redirect occur it cannot follow it correctly, I've followed the following guide to solve the problem with no luck: 

[http://php.net/manual/en/ref.curl.php](http://php.net/manual/en/ref.curl.php)

It describe how you should do the loop and set CURLOPT_FOLLOWLOCATION etc. etc. But i can't get it to work properly. Safe mode and open_basedir are off.

What happens is that the HTTP GET output results in when converting to text and do print() i get following: "Redirecting back to secondary domain to set cookies function postForm() { document.multiDomain.submit(); } Welcome to the domain *** Click the button to continue... "

BUT when i just print the result i correctly get redirected to the site im suppose to goto, that means the javascript is runned and follow the redirect. Anyone else had this problem? Please help!

Ver.
PHP 5.2.6-1
curl 7.18.2 (i486-pc-linux-gnu) libcurl/7.18.2 OpenSSL/0.9.8g zlib/1.2.3.3 libidn/1.8 libssh2/0.18

If anymore info is needed, let me know!

Cheers // Mattias

---

### Post by Hellkeepa on 2010-03-04
HELLo!

The reason cURL doesn't follow the JS redirect, is because it is sent as HTML content and your application does not evaluate the JS code. Which means that cURL doesn't even know that there is a redirect involved, since it can only follow HTTP header redirects.

To get this to work you'll have to parse the returned content, extract the URL "manually", and then use cURL to visit the correct location.

Happy codin'!

---

### Post by Mattza on 2010-03-05
Thanks for the quick reply! Problem is that im able to get the redirected URL, but when i do another HTTP GET to that URL there is a Javascript redirect once again?! So there is a eternity loop. But when i manually go the page im able to get a correct search with that URL string, but obviously there is some kind of default Javascript redirect on this homepage. Any ideas how to solve this?

---

### Post by Hellkeepa on 2010-03-05
HELLo!

Sounds like they're using a cookie check, and if the cookie is missing (or failing the check) it'll send the redirect again. So make sure you're updating the cookies you're sending, and that you have the right session ID.

Happy codin'!

---

### Post by Mattza on 2010-03-08
Good point, but i've created a cookiejar correctly and got it. But i don't think i send any cookie with the HTTP GET request. I'll look into this during the day, thanks for the quick reply!

---

