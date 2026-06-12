---
title: "Can't see my index.php stored in /var/www"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by zerofxC on 2008-10-21
I am running ubunutu 8.04 with LAMP server installed along with Webmin and SQUID.

This has all been working nice and tidly untill now! 

When i try to connect to the hosted site via the internet i can't see the index page that i placed in the /var/www directory. It just shows a blank page. This worked fine last week.

The weird thing is that i can access sub directories, for example [http://myIp/images](http://myIp/images).

I have also got an SSH server running and connect to my machine from work using a Tunnel. When i try and access [http://localhost](http://localhost) from my work machine it also shows a blank page insted of the index but works with sub directories. e.g. [http://localhost/images](http://localhost/images).

Has anyone had this problem before?

:popcorn:

---

### Post by alphacrucis2 on 2008-10-21
> **zerofxC said:**
> I am running ubunutu 8.04 with LAMP server installed along with Webmin and SQUID.

This has all been working nice and tidly untill now! 

When i try to connect to the hosted site via the internet i can't see the index page that i placed in the /var/www directory. It just shows a blank page. This worked fine last week.

The weird thing is that i can access sub directories, for example [http://myIp/images](http://myIp/images).

I have also got an SSH server running and connect to my machine from work using a Tunnel. When i try and access [http://localhost](http://localhost) from my work machine it also shows a blank page insted of the index but works with sub directories. e.g. [http://localhost/images](http://localhost/images).

Has anyone had this problem before?

:popcorn:

Not especially but has the index.php page or associated css file changed? In your browser view the page source and see if it looks ok. Firefox View / Page Source. i.e is the page really blank or just being rendered that way. I recall a case a few years back where some one has accidentally changed their text colour to white on a white background, :)

---

### Post by zerofxC on 2008-10-21
Unfortunatly not. The page is as basic as it gets, it also has images that are not showing which rules out that solution.

Thanks for your reply though!

I have also noticed that it will show in Firefox but not in Internet Explorer 7.

In IE7 you can see the source but there is still nothing displayed.

Thanks again! :guitar:

---

### Post by alphacrucis2 on 2008-10-21
> **zerofxC said:**
> Unfortunatly not. The page is as basic as it gets, it also has images that are not showing which rules out that solution.

Thanks for your reply though!

I have also noticed that it will show in Firefox but not in Internet Explorer 7.

In IE7 you can see the source but there is still nothing displayed.

Thanks again! :guitar:

There are differences between the way different browsers render html, css etc but there isn't normally the difference of displaying versus not displaying at all on a simple page. Try some other browsers and see if the problem only pertains to IE7? You could try running your page through a html validator. Maybe Firefox is being forgiving about something that IE 7 doesn't like. Could be due to a service pack updating IE 7 rather than anything on your web server. As you page ends in .php. I presume you are running some sort of php script in which case you would need to pass the page as delivered to the browser to the validator rather than the index.php file off the server as the php script can alter the html that apache is outputting to the browser.

---

### Post by zerofxC on 2008-10-29
I finaly got round to looking at my problem here.. and don't i feel like a gimp!

Turns out I had my HTML wrong..

Instead of **<title>Title here</title>** I had **<title>Title here<title/>**

As soon as i changed this it was fine!

Thankyou for the replys though!  :lolflag:

---

