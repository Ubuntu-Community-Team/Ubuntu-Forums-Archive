---
title: "PHP socket chat"
date: 2009-09-02
forum: Programming Talk
---

### Post by hackaro on 2009-09-02
hi everyone!

i'm trying to execute a php file that acts like a sever to my socket chat.

But when i execute it(console mode), php crash on socket_select and socket_accept, and show me no error.

i think that is some socket bad configuration.

can anyone help me. i'm new with ubuntu. thanks

---

### Post by hackaro on 2009-09-02
> **hackaro said:**
> hi everyone!

i'm trying to execute a php file that acts like a sever to my socket chat.

But when i execute it(console mode), php crash on socket_select and socket_accept, and show me no error.

i think that is some socket bad configuration.

can anyone help me. i'm new with ubuntu. thanks

i solve the problem with socket_set_nonblock funtion, but now i get socket_accept:unable to accept incoming connection [11]:resource temporarily unavailable....

---

