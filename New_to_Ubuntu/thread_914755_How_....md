---
title: "How ...????"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by hemlet on 2008-09-09
Hello, 
....every body i've question 


-) How to install XAMPP server / LAMPP on linux ?

-) How to using proxy on linux ubuntu 8.04 ?




thanx, regards
tutorial-hemlet.blogspot.com

---

### Post by jemate18 on 2008-09-09
> **hemlet said:**
> Hello, 
....every body i've question 


-) How to install XAMPP server / LAMPP on linux ?

-) How to using proxy on linux ubuntu 8.04 ?




thanx, regards
tutorial-hemlet.blogspot.com

Try this
> [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by jemate18 on 2008-09-09
Do you want to install proxy server?

check this out

> [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/squid.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/squid.html)

or 

> [http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/](http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/)

---

### Post by Blutack on 2008-09-09
Ok, to set up a LAMP stack there are two ways.
If you are using it for developing and it probably won't be going on the internet, use this
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
it will not automatically update, but it does have an easier initial configuration so you shouldn't need to change much.
If you want to install a LAMPP stack through ubuntu's package management system (if this is going to be a production server connected to the internet) follow this guide:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
you will need to do a bit more work but it will be more secure, and will automatically update.
For a proxy server you want to use a program called Squid.
This guide should do the trick:
[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

---

### Post by jemate18 on 2008-09-09
Do you mind changing the TITLE of your thread so that those who will answer or look for solution will have easy time looking for what they are searching for.

Thanks.....

---

