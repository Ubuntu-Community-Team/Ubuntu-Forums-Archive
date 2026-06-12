---
title: "how to setup an smtp server pls i need a guide"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by nnamdi on 2008-05-12
please i got a job to setup and smtp server pls i want to use ubuntu gusty how do i go about it
thanks on any quick reply

---

### Post by Monicker on 2008-05-12
Personally I like Postfix for an smtp server.

This guide will get you started:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto#head-4788a460d7f9013d52b7b43fd7f36afe28c0bd6c]("https://help.ubuntu.com/community/PostfixBasicSetupHowto#head-4788a460d7f9013d52b7b43fd7f36afe28c0bd6c")

---

### Post by hyper_ch on 2008-05-12
[http://www.howtoforge.com](http://www.howtoforge.com) --> they have perfect server tutorials that show how to setup mailservers... BUT do you have a static IP address?

---

### Post by nnamdi on 2008-05-12
yes the company should provide a static ip

or

i think it is an intranet

---

### Post by hyper_ch on 2008-05-12
well, if you plan to send through the mailserver accross the internet then you'll need a static IP... most mailservers will not accept email from non-static iped servers.

---

### Post by brian_p on 2008-05-12
> **nnamdi said:**
> please i got a job to setup and smtp server pls i want to use ubuntu gusty how do i go about it
thanks on any quick reply

```
sudo apt-get install exim4
```

```
sudo dpkg-reconfigure exim4-config
```

to alter the configuration. That might do exactly what you want. If not there is loads of documentation to read. Have fun.

---

