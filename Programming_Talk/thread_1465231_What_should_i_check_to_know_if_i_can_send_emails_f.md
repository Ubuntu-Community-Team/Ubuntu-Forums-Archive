---
title: "What should i check to know if i can send emails from my web app?"
date: 2010-04-29
forum: Programming Talk
---

### Post by tirengarfio on 2010-04-29
Hi,

i would like to know how can i send emails from my web app that i have in a hosted in a shared server.

Well, first of all i would like to know if i can, so my question is: what should i check?

I heard some time i should have a mail server in my hosting, so i tried "telnet smtp.tirengarfio.com 465" but i get:

```

telnet: could not resolve smtp.tirengarfio.com/465: Name or service not known
```

tirengarfio.com is the domain where i have the web app.

As you can see im lost..

Javi

---

### Post by slavik on 2010-04-29
you want a mail server to act as a relay, unless you want to do that yourself (which you can). hosting sites would not normally provide that. if you have access to an imap mail host, you can use imap libraries to login to the server to send e-mail. or you need to set up a mail transfer agent.

---

