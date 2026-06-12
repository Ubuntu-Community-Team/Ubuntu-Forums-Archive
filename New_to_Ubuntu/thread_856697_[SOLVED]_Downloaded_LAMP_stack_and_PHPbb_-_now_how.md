---
title: "[SOLVED] Downloaded LAMP stack and PHPbb - now how do I use it?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Old_Grey_Wolf on 2008-07-11
I downloaded the LAMP stack from the repository, PHPbb2, and PHPbb2-conf-mysql. PHPbb2-conf-mysql asked for the MySQL password so I assume it automatically configured the MySQL database. 

Now I want to try out the message board. Where do I begin? Is there a URL hosted on my computer?

---

### Post by LookTJ on 2008-07-11
[http://localhost/](http://localhost/) work for you?

---

### Post by fatality_uk on 2008-07-11
Open a web browser and type:
> [http://localhost/phpbb](http://localhost/phpbb)

Then when that page opens, at the top of that page, click log in.
Enter the following:
> username = admin
password = admin


Then click the:
> GotoAdministrationPanellink and start from there.

---

### Post by Old_Grey_Wolf on 2008-07-11
Taylor;

When I do that, all I get is a web page with this information on it.

Index of /
Name	Last modified	Size	Description
apache2-default/	20-Nov-2004 14:16 	-
Apache/2.2.4 (Ubuntu) Server at localhost Port 80

---

### Post by Old_Grey_Wolf on 2008-07-11
fatality_uk,

That gives me:

Not Found
The requested URL /phpbb was not found on this server.
Apache/2.2.4 (Ubuntu) Server at localhost Port 80

---

### Post by fatality_uk on 2008-07-11
Did you follow all the guidelines posted here?
[https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)

---

### Post by Old_Grey_Wolf on 2008-07-11
> **fatality_uk said:**
> Did you follow all the guidelines posted here?
[https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)

I searched but didn't find that help link you provided (You are now thanked 59 times). I guess I'm not very good at searching the Ubuntu Wiki. I followed the instructions. My Message Board is working now. :mrgreen:

Thanks, fatality_uk



To the moderator that moved this thread, I'm not convinced that a thread on LAMP servers is an "Absolute Beginner Talk" topic. :lolflag:

---

### Post by fatality_uk on 2008-07-11
60 but who's counting ;)
No worries. Glad to have helped.

---

