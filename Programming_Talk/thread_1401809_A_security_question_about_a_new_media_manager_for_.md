---
title: "A security question about a new media manager for Linux."
date: 2010-02-08
forum: Programming Talk
---

### Post by Yuzem on 2010-02-08
Hi, I just released yesterday the first version of Figuritas.
You can read more about it [here]("http://yuzem.blogspot.com/p/figuritas.html")

I'm not a programmer thats why I can't be sure if it is secure and I wanted to know if anyone has any advice about that.

Figuritas runs on a server using thttpd, it can be accessed from any other computer but it blocks any connection coming from an ip that is not specified in the config file.

The default ips that are allowed are "$HTTP_HOST" and "::1" the last one is the one given when localhost is used instead of the actual ip.

When a computer that is not allowed tries to access Figuritas, it responds with:
Not allowed ip: $REMOTE_ADDR

Does anyone know if there are other things that I may be missing?
Any advices on this are welcome.

Thanks in advance.

---

