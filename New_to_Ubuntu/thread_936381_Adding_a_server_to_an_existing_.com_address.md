---
title: "Adding a server to an existing .com address?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Madman6510 on 2008-10-02
I have a website on a hosting server that I want to add some things to. Problem is, the server isn't ours, but rather a friends. The web app I want to run requires some programs to be installed and up to date, and also requires access to the MySQL database. Instead of asking him to update and install his software, and giving me the root password to the database, I would like to add my server to the domain, kind of like as a secondary server.

EX:
Main server: [www.example.com](www.example.com)
Secondary: wiki.example.com

How would one do this?

---

### Post by Bachstelze on 2008-10-02
Just change your DNS A record for wiki.example.com to point to the IP of the new server, instead of the old one.

---

### Post by Madman6510 on 2008-10-02
Thank you, except I have no idea what the DNS A record is/how to change it, and my ISP gives me a dynamic external IP address.

---

