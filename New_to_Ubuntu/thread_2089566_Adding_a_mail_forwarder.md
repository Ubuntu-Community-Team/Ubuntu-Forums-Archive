---
title: "Adding a mail forwarder"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by Maveeeee on 2012-11-29
Hello, I've got a linux VPS.

I want to add a mail forwarder (for example [EMAIL="admin@mysite.com"]admin@mysite.com[/EMAIL] to [EMAIL="mymail@gmail.com"]mymail@gmail.com[/EMAIL])

I have googled around and I found nothing useful :/
Can somebody please explain to me how I create an email alias/forwarder? 

Thank you so much.

---

### Post by lisati on 2012-11-29
If your VPS uses Postfix, you have a number of options. One is the [.forward]("http://www2.slac.stanford.edu/comp/messaging/Using/forw_unix.html") file. IIRC this approach works with other MTAs as well.

---

