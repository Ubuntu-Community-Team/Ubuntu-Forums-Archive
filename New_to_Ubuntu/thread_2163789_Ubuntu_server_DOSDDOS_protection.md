---
title: "Ubuntu server DOS/DDOS protection"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by qICEp on 2013-07-19
Hey everyone, im setting up server for private hosting (Just me and my friends)
And i need to protect it from dos attack's as far as i can.

The machine will have ssh/ssh2,apache,mysql,FTP and game servers.
How do i protect it from DOS and what do you suggest me?

Any references,suggestions or just info about these is welcome.

Thank you

---

### Post by HermanAB on 2013-07-19
Howdy, 

The best you can do is to use an iptables rate limit rule.

Something like this: [http://www.aeronetworks.ca/2013/05/ssh-brute-force-attacks.html](http://www.aeronetworks.ca/2013/05/ssh-brute-force-attacks.html)

---

