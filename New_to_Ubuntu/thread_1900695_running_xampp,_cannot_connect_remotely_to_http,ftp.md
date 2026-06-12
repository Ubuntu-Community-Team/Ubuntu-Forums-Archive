---
title: "running xampp, cannot connect remotely to http,ftp"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-12-26
[SIZE=3]Hi Friends,
I installed xampp last night which went smoothly however, now I  can only access ftp/http on the local machine. I can connect only internal, 127.0.0.1, [http://localhost]("http://www.techsupportforum.com/forums/external-link/?link=http%3A%2F%2Flocalhost"), my LAN IP. I can connect in http, ftp, but as  soon as I try to login from a remote machine on a different ip,which is also in my LAN, I fail .

Kindly help me to solve....
[/SIZE]

---

### Post by Gone fishing on 2011-12-27
Sonds like your firewall is doing its job - how do you connect to the internet through a router? Have you opended the required ports in the firewall on the router?

---

### Post by pmohankumar on 2011-12-27
Ya router used.
Other systems are working fine. 
i can access other systems xampp through my browser, but they can't access my xampp through their browser and also FTP.

---

### Post by Gone fishing on 2011-12-27
Sounds like your router is dropping inward connections to the required ports, check the firewall settings of the router. 

You could port scan you machine using this site [http://www.grc.com](http://www.grc.com)

---

### Post by Lars Noodén on 2011-12-27
I would take a step back and re-consider the set up.  xampp is a crutch for people still on Windows and when added to a working Ubuntu system introduces non-standard locations for things and even some duplicates and conflicting versions of existing packages.  Further, updates and versions are not tracked the way xampp is set up so you lose a lot of security benefits that the package manager provides.  

To reset your system, nuke everything in the [font=Courier New]/opt/lampp[/font] directory.

Then, perl and a few other things are already on your system by default so you can add the pieces that are missing:

```

apt-get install openssh-server apache2 php5 mysql-server

```

---

### Post by pmohankumar on 2011-12-30
I just stopped system firewall.
CMD "$ ufw disable"
Its working.

Thanks friends.

---

### Post by Lars Noodén on 2011-12-30
When you re-enable the firewall be sure to leave open ports 80,443 and 22 for HTTP, HTTPS and SSH respectively.

---

### Post by pmohankumar on 2012-01-06
Still now i didn't re-enabled,
while enable i will leave that ports.
thanks friend.

---

