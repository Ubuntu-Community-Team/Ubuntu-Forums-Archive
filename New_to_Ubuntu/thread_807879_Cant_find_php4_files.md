---
title: "Cant find php4 files"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Abadi176 on 2008-05-26
Hello,

I am a starter with linux and I did want to install php4 and php5 at the same time. I did want to use php4 as cgi. I searched on the net and found this article:

[http://www.howtoforge.com/apache2_with_php5_and_php4_p2](http://www.howtoforge.com/apache2_with_php5_and_php4_p2)

I tried to install it but when the install comes to php4 it says it cant find it. I also have edited the sources.list file. 

What am I doing wrong ? 

Already tyvm. Sorry for my english.

Greetz,

Abadi176

---

### Post by Sarah L on 2008-05-26
Hi,

The how-to that you mentioned is horribly out of date - it was written for Ubuntu 5.10, while we're currently on version 8.04! It's best to use a newer tutorial if you want to install something as large and dynamic as a webserver.

Also, is turning your computer into a server what you really wanted? Those packages will do that for you. If you want to test PHP scripts in a safe, enclosed environment (no hackers!), then I suggest that you install lampp from [http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html").

All you need to do is extract and run the webserver that directory - no installation needed! This is the method of choice for web site testing on a personal computer.

Best regards,
Sarah

---

