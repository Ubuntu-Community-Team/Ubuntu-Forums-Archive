---
title: "unable to send mail"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by jtcdesigns on 2008-05-07
Well this is my first post here and just starting out in linux. I am starting to learn Drupal so I setup a virtual machine with xubuntu as a LAMP server. I managed to get everything setup and working fine except setting up a new user sends out an email to them with their username and password. So my dilema is it's not sending out email. A friend of mine suggested I setup postfix but doing so I dont exactly know all of what to fill out. I have googled to no evail. Currently I run my own mail server at work with lotus notes domino. I setup an email address on our mail server and was hoping for a way to route all mail from the xubuntu computer over to the mail server. I'm not sure if this is just a big pain to do or something easy that I dont know. So I figured I'll join an ubuntu forum and ask. Is this something simple and if so is there a link on how to set it up that I haven't found yet?

---

### Post by Monicker on 2008-05-07
Postfix is pretty nice, and the default config works well.  During the postfix installation, there will be a prompt for several options:

```
No configuration
Internet Site
Internet with smarthost
Satellite system
Local only
```

If you choose Satellite system, it will send all mail to another mail server for delivery.  You could specify you Lotus server there.  Just be sure the Lotus side will accept mail from your linux machine, and relay for it.

---

### Post by jtcdesigns on 2008-05-07
Well I just tried that adding in my server address but forgot my mail server doesn't allow relay. I could possibly make an exception to the rule and just allow that computer in. I think I will see if I can setup a mail server on xubuntu and then see if I can forward my mail from that account over to my mail server.

---

