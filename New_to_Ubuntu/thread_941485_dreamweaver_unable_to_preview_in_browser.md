---
title: "dreamweaver unable to preview in browser"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by mkosinska@tiscali.co.uk on 2008-10-08
hi I am a total beginner in web design in fact I am still trialing dreamweaver CS3. However I can not preview my pages in he browser. I get an error message: HTTP Error 404.0 - Not Found The resource you are looking for has been removed, had its name changed, or is temporarily unavailable. I have vista and not sure if that has anything to do with it or perhaps I have set my site setting incorrectly. Is there anyone out there who would not mind giving me some advice (in plain english please!)???? Many thanks

---

### Post by tradet on 2008-10-08
Hello, not sure if you're in the right forum.

Sounds like you need apache or xampp.
[Try xampp]("http://www.apachefriends.org/en/xampp.html"), very easy to use.

Just put testing server and point it to c:/xampp/htdocs and it should work.

Probably a few more things for you to do but this should get you started.

---

### Post by Paqman on 2008-10-08
> **tradet said:**
> 
Sounds like you need apache or xampp.
[Try xampp]("http://www.apachefriends.org/en/xampp.html"), very easy to use.


No, Dreamweaver can send a static page to the browser to be checked without a server. You'll only need a testing server if you're creating a dynamic site.

Tradet, try adding a new browser to the list. Launch it with the command /usr/bin/firefox, which you should be able to browse to. Dreamweaver will probably interpret that as Z:\usr\bin\firefox, since it thinks of Ubuntu root as being Z drive.

---

### Post by mkosinska@tiscali.co.uk on 2008-10-08
thanks for your help
I tried addidng another browser unfortunatelly it did not work 
I have windows vista would that be causing any problems?

---

### Post by Paqman on 2008-10-09
> **mkosinska@tiscali.co.uk said:**
> 
I have windows vista would that be causing any problems?

Not if you're running Dreamweaver in Ubuntu, no.

---

