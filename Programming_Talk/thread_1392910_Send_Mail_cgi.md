---
title: "Send Mail cgi"
date: 2010-01-28
forum: Programming Talk
---

### Post by Rich78 on 2010-01-28
What do I need to install on an Ubuntu server running 8.04 x64 to use Mail::Sendmail? for a sendmail cgi perl script?

I've just moved a site from my freebie space on my ISP to my own VPS server and it's failing on the sendmail cgi script.  Since I've not installed any mail system I'm guessing it's that but just not sure where to start.

Thanks.

---

### Post by myrtle1908 on 2010-01-28
Failing how?  You can use the cpan shell to install Mail::Sendmail.

```

cpan install Mail::Sendmail

```

---

### Post by Rich78 on 2010-01-29
I'm asuming I will also need to setup some sort of simple mail server on the server though?

---

### Post by Rich78 on 2010-01-29
> **myrtle1908 said:**
> Failing how?  

General 500 error.  Since nothing has been setup for sendmail it's not surprising just wanted to know what I will need.

I don't want to have the hassle of maintaining a full mail server, so just want something that can send out.

---

### Post by Rich78 on 2010-01-29
Should have done a search, Doh!!

Looks like I need to install exim4 [http://www.exim.org/](http://www.exim.org/)

---

