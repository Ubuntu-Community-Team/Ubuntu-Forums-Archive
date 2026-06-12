---
title: "pahelp namn pls.."
date: 2009-08-31
forum: Philippine Team
---

### Post by frustphil on 2009-08-31
sa mga marunong sa mail server pahelp naman..=)

kakatapos ko lang mag install ng postfix at gusto kong magcreate ng transport.db.
So inexecute ko ang:

>    	 	 	 	 	 	  #/usr/local/sbin/postmap /usr/local/etc/postfix/transport
 

pero nag-error xa at ito sabi ng system:

> 
postmap: warning: /usr/local/etc/postfix/transport, line 0: expected format: key whitespace value

sa pagkakaalam ko kelangan kong magcreate ng 'transport' na directory at iupdate ang master.cf at main.cf. Ang tanong ko, pano? Specifically anong parameter ang iupdate ko sa master.cf at main.cf? Alam ko merong mga server experts dito, share your knowledge naman.. =) 

salamat...

---

### Post by jmazaredo on 2009-09-01
Hi! actually im noob at servers. I have setuped servers using postfix + mysql and using guide on the internet and kung ginaya mo sila wala ka magiging problem regarding sa transport.

eto yung file directory nang transport
/etc/postfix/transport

kugn wala i think you should create one $nano /etc/postfix/transport

Check this [link]("http://www.postfix.org/transport.5.html")
Also this [one]("http://linuxnet.ca/postfix/dedicated_transport.html")
This [one]("http://www.ithowto.ro/2008/10/howto-add-custom-transport-routes-maps-in-postfix/") also

---

