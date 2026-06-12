---
title: "I need Encrypted internet connection"
date: 2006-04-17
forum: Repositories &amp; Backports
---

### Post by medya on 2006-04-17
not sure if I have posted it in the right place, please feel free to move it, if it is in a wrong place.

I have a dedicated server HOSTING and a ububuntu pc at home.
I want to have encrypted connection to internet using my dedicated server hosting ... is there any program to do that ?

---

### Post by encompass on 2006-04-17
not sure on the whole process of it... but you could look up ssh tunneling.  I use it for vnc connections.  So that is probably the same process but with port 80(http). Hope that helps.

---

### Post by medya on 2006-04-17
I know nothing of SSH tunneling... 
I know some other scripts like PHProxy or CGI proxy that let you surf internet using a hosting...

but for that you have to enter each site's adress manualy , and it wont work for Messengers and others..


if we can make a linux to surf internet using a "dedicated server hosting's internet" we can do the encrypt part...

my dedicated hosting has SSL certificate, so it would be encrypted...

---

### Post by stuporglue on 2006-04-17
I'm not entirely sure what you're asking for. You want everything on the network to be encrypted? Or you just want ssl to work for your server?

If you want EVERYTHING encrypted, check out Tor: [http://tor.eff.org/](http://tor.eff.org/) 
Tor encrypts everything TCP. Encryption is hard work for a computer, so expect your browsing etc to be quite a bit slower. 

If you just want your SSL and https connection to your server to be encrypted, that's a different question, and one I don't know how to answer.

---

### Post by fdoving on 2006-04-18
I would suggest VPN.
I use a Encrypted PPTP connection to my server.

- Frode

---

### Post by medya on 2006-04-18
studporogue thanks for [http://tor.eff.org/](http://tor.eff.org/) ,  I hope I can install it and use it ,
can I make Tor to enable encryption when I need it and normal connection when I dont need it?

and  fdoving, what is VPN ?

---

### Post by fdoving on 2006-04-18
[http://www.howstuffworks.com/vpn.htm](http://www.howstuffworks.com/vpn.htm)

---

