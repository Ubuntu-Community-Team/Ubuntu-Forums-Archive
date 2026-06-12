---
title: "php cookies.."
date: 2006-01-04
forum: Programming Talk
---

### Post by grim918 on 2006-01-04
does anyone know where i can read about using cookies with php. i have a book on php but the cookies examples that they show seem to simple. you could probably use simple javascript injection to gain access into accounts with the methods from the book. i want to learn how to make my php code secure.

---

### Post by signifer123 on 2006-01-04
Well if you use client side its not going to be very secure probably hashing(sha1,md5) it would be your best bet, on cookies/sessions, but overall don't store anything you need to be safe in cookies...what book did you get?

---

### Post by grim918 on 2006-01-04
a book from sams publishing. where can i read up on hashing and md5. that is the kind of stuff i would like to learn about but i cant find some php examples. i just want to make my php code secure. i dont want someone running around reading sensitive information

---

### Post by healychan on 2006-01-04
If you want something more secure. You should use session instead of cookie.

Although the session id itself is a cookie, it contain no important information about the user. PHP is good at handling session and interact with database, and that's why today people use the LAMP to develop web site.
I think this forum is using the LAMP as well:razz: 

Anyway, cookie itselt has too many limitation, such as file size. Programmer shouldn't store any information with cookie.

If you want a book, I would recommend this.
Programming PHP, O'Reilly
ISBN: 1-56592-610-2

---

### Post by Ahriman on 2006-01-04
Heres a decent tutorial on sessions and cookies from phpfreaks

[http://www.phpfreaks.com/tutorial_cat/23/Sessions-and-Cookies.php]("http://www.phpfreaks.com/tutorial_cat/23/Sessions-and-Cookies.php")

---

### Post by grim918 on 2006-01-06
thank you guys i finally figured out how to use cookies and sessions. now i have another question though. i read that cookies or sessions will not work if the users browser does not accept cookies. is there another way of authenticating a user besides passwords,usernames, and sessions/cookies.

---

### Post by Ahriman on 2006-01-06
Sessions will still work if the user's browser doesn't accept cookies. It just means that in all the URL's on that site will have the PHPSESSID tacked onto the end of them.
Like so:

index.php?PHPSESSID=s123a4e5f6g4a6e5f4g6e421a6e

If their browser accepts cookies, it won't have that at the end of the URLs, because it will be saved in it's own small cookie.

---

### Post by healychan on 2006-01-06
[QUOTE=grim918]thank you guys i finally figured out how to use cookies and sessions. now i have another question though. i read that cookies or sessions will not work if the users browser does not accept cookies. is there another way of authenticating a user besides passwords,usernames, and sessions/cookies.[/QUOTE]

Since SESSION_ID itself is a cookie, you cannot maintain the state once the user close the browser. However, you can make a form that allow user to login. Compare the user input with the database to verify the user. Notice that the cookie will disappear only when the browser close.

---

