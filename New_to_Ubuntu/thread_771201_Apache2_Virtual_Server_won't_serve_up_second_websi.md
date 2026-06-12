---
title: "Apache2 Virtual Server won't serve up second website ..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by cwmoser on 2008-04-27
I must have something goofed up -- my Apache2 server will not serve up my second website.  

I have two domains:  Cerant.com and EasternHouseSoftware.com.

[www.Cerant.com](www.Cerant.com) works fine

[www.EasternHouseSoftware.com](www.EasternHouseSoftware.com) serves up the page at /var/www instead of the one I want in the /var/www/easternhousesoftware.com folder.

I can get the EasternHouseSoftware page to display  if I enter [www.Cerant.com/easternhousesoftware.com](www.Cerant.com/easternhousesoftware.com)


Any ideas how to make this work properly?

Thanks

Carl

PS BTW, I am posting here because for some reason I do not have rights to post in the Server forums.  Must be because of the upgraded forum.

---

### Post by RealPSL on 2008-04-27
You might want to take a look at the link

[http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html")

It gives a pretty good example of how to setup virtual hosts on apache 2. If not we will have to see exactly what you have configured in order to help.

---

