---
title: "[SOLVED] website problem with accents and other spanish characters..."
date: 2007-09-26
forum: Programming Talk
---

### Post by orlox on 2007-09-26
Hi!

Just recently, I ended up a website I was making for a client of mine. Everything worked fine until just recently, when suddenly all accentuated characters started to be displayed wrong. I believe they did something strange on the host, but I don't know much about this...

Does anyone know what could cause this???

---

### Post by LaRoza on 2007-09-26
Did you use entities or ascii codes?

---

### Post by mssever on 2007-09-26
It's almost certainly a character set issue. Make sure that you always explicitly specify the charset (and prefer utf-8)

---

### Post by orlox on 2007-09-27
The thing is, everything worked fine until just recently, The charset is specified as utf8, I didn't used entities everywhere but, I just can't figure out what change on the server could cause this...

---

### Post by PaulFr on 2007-09-28
I would suggest that you check the **Content-Type** header value being output by your server using an Firefox extension like Firebug or Web Developer Toolbar or Live HTTP Headers.

---

### Post by orlox on 2007-09-28
I've got this on my head:

<meta content="text/html; charset=utf-8" http-equiv="Content-Type"/>

---

### Post by LaRoza on 2007-09-28
Does it work if you use ascii codes, not entities?

---

### Post by orlox on 2007-09-28
Where I use simple ascii it fails to display correctly, entities display well. However just a week ago it worked fine!!

I know the problem could be fixed by using entities everywhere, but since a lot of the info is stored in a database, correction of all the information before display would be too much work...So what i'm truly looking for is the reason that caused this.:(:(:(

---

### Post by aks44 on 2007-09-28
> **PaulFr said:**
> I would suggest that you check the **Content-Type** header value being output by your server using an Firefox extension like Firebug or Web Developer Toolbar or Live HTTP Headers.

+1

Looks like your server is now sending a wrong Content-Type header (probably because of some upgrade or change in the server's configuration). If you're using PHP, just make sure to add to your pages before any other output:
[php]header('Content-Type: text/html; charset=UTF-8');[/php]

---

### Post by mssever on 2007-09-28
The meta tag should override the headers. In other words, the server's content type header shouldn't matter.

You might want to check that your database is using the correct character set; if you use phpmyadmin or similar to view your database, are the characters correct?

---

### Post by orlox on 2007-09-29
phpMyAdmin correctly displays the accents. Also, it doesnt use entities to do that...

---

### Post by mssever on 2007-09-29
> **orlox said:**
> phpMyAdmin correctly displays the accents. Also, it doesnt use entities to do that...

Hmm.. I'm nearly out of ideas. One last suggestion: ```
telnet yourhostname.com 80
```Once you're connected, type ```
HEAD /url/to/bad/page HTTP/1.1
Host: yourhostname.com
```Be sure to type an extra blank line. Also, backspace/delete won't work properly.

When you get the reply, look for the content-type header and check the character set there. As I said earlier, this character set shouldn't matter since you're setting the appropriate meta tag. But this is worth a shot, anyway.

---

### Post by orlox on 2007-09-30
Here is the output:

```

pablo@PCPABLO:~$ telnet aprendizajeservicio.cl 80
Trying 200.73.13.9...
Connected to aprendizajeservicio.cl.
Escape character is '^]'.
HEAD http://www.aprendizajeservicio.cl/index.php HTTP/1.1
Host: aprendizajeservicio.cl

HTTP/1.1 200 OK
Date: Sun, 30 Sep 2007 19:30:19 GMT
Server: Apache/1.3.37 (Unix) mod_auth_passthrough/1.8 mod_log_bytes/1.2 mod_bwli                                 mited/1.4 FrontPage/5.0.2.2635.SR1.2 mod_ssl/2.8.28 OpenSSL/0.9.7a PHP-CGI/0.1b
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Pragma: no-cache
X-Powered-By: PHP/5.2.0
Set-Cookie: 91cb6c891e19ff90f553f314825f9285=9cc13b71ff7367a561628508de6f6407; p                                 ath=/
Content-Type: text/html; charset=iso-8859-1


```

I seem to get iso-8859-1 as the charset :confused:

---

### Post by mssever on 2007-09-30
In that case, see aks44's post (post 9) It will make your server send the correct content type.

Off topic: I don't recall seeing any .cl domains before. What country is that?

EDIT: I visited your site, and looked in Firefox's view menu to see what character set it was using. As expected, it was using ISO 8859-1. When I manually changed it to UTF-8, the page displayed properly. I did find it odd, though, that the headers were correct, but the dropdown menus were wrong.

---

### Post by orlox on 2007-10-01
.cl domains are from Chile.

I'll try manually modyfing the headers and see what happens...

---

### Post by orlox on 2007-10-01
It worked :):):):):)
Specifying the header with php did the job

Thanks to all!!!!

---

