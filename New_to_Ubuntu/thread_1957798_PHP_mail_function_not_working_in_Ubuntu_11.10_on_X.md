---
title: "PHP mail function not working in Ubuntu 11.10 on XAMPP"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2012-04-13
So I'm making a website with PHP and MySQL so before I directly buy a host. I thought of developing the site first on my computer using XAMPP then buying the host and uploading it. But for a email confirmation page I need the mail function (or anything else which can send emails). But it dosent seem to work(I heard when I buy a host it wont be a problem) I tried google but most of them are outdated or not working for me. So please tell me how to fix it or provide an alternative mailing system.

---

### Post by GWBouge on 2012-04-13
Which part of it isn't working?  Is PHP throwing an error?  Is the delivery agent complaining?  Or is it just not getting to the destination?

I'm not sure if it comes with a XAMPP setup, but you'll need a delivery agent, such as Postfix, to handle the sending of the mail called by PHP's mail() function.  If that's there, check the logs (something like /var/log/mail.err and /var/log/mail.log) to see if or what it's complaining about.  If the sending is timing out, your ISP might not be letting you outbound on port 25.

---

### Post by cyb3r_sn4k3 on 2012-04-13
> **GWBouge said:**
> Which part of it isn't working?  Is PHP throwing an error?  Is the delivery agent complaining?  Or is it just not getting to the destination?

I'm not sure if it comes with a XAMPP setup, but you'll need a delivery agent, such as Postfix, to handle the sending of the mail called by PHP's mail() function.  If that's there, check the logs (something like /var/log/mail.err and /var/log/mail.log) to see if or what it's complaining about.  If the sending is timing out, your ISP might not be letting you outbound on port 25.


The ISP is not blocking I called and checked :) PHP does not throw an error. But no mail is recieved. Also, I was not aware of a delivery agent. I'll check it out and let u guys know..

---

