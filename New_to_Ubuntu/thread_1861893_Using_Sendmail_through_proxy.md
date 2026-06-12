---
title: "Using Sendmail through proxy"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by revanthb3000 on 2011-10-16
I'm at a university right now and I have to use a proxy(squid) to access the internet. How do I configure sendmail so as to be able to send emails ?

Thanks in advance

---

### Post by sadaruwan12 on 2011-10-16
Thats a little tedious if your proxy has been configure to let data out to the ports of 25 and 110 then you have to configure the proxy as your mail server but it's better if you ask your admin to that part for you.

'Cos it's a two way process.

---

### Post by smtp on 2011-10-20
Perhaps the best approach would be using internal university relay as a SMART host for sendmail (this is for outbound mails). Inernal relay could be provided by your system administrator.

---

