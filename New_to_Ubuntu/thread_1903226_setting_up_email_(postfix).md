---
title: "setting up email (postfix)"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by anon0 on 2012-01-02
I'm trying to set up Ubuntu Server so that it can send emails, which I think is done by postfix. I ran "sudo dpkg-reconfigure postfix". It asks me for the system mail name. What do I put here, if I just want to use say my Hotmail or Gmail account?

---

### Post by lisati on 2012-01-02
The system mail name is what your server will use to identify itself to other mail servers. If you have (or will have) a domain name that other people can use to send mail directly to your server, use that.

---

### Post by anon0 on 2012-01-02
Thanks. I'm not sure if I'm on the right path. I don't have my own domain name and am just trying to test if I can get my Ubuntu machine to send out emails to myself with an HTML/PHP script. So all I have in theory could be an IP address. Will I be able to use postfix in this case, for testing? 

I'm following this tutorial:
[http://jonsview.com/how-to-setup-email-services-on-ubuntu-using-postfix-tlssasl-and-dovecot](http://jonsview.com/how-to-setup-email-services-on-ubuntu-using-postfix-tlssasl-and-dovecot)

---

