---
title: "How to upgrade from php 5.2.4 to 5.3"
date: 2010-07-02
forum: Programming Talk
---

### Post by megamonk on 2010-07-02
Hi,

just installed a LAMP server and i want to upgrade my php version because im having problem with this version not being able to support "request_order" which i want to set to "GP" only excluding the cookie from being loaded to the $_request variable in php

pls help

thanks

---

### Post by Bachstelze on 2010-07-02
Just upgrade to Lucid.

---

### Post by megamonk on 2010-07-02
i cant... its a remote production server....

---

### Post by Bachstelze on 2010-07-02
Then you can either find php 5.3 packages built for your sersion of Ubuntu, or install the Lucid packages if you're feeling lucky, or compile PHPH 5.3 from source.

Personally, I'd just compile from source. It's not that complicatedn abd it's guaranteed to work.

---

### Post by megamonk on 2010-07-02
> **Bachstelze said:**
> Then you can either find php 5.3 packages built for your sersion of Ubuntu, or install the Lucid packages if you're feeling lucky, or compile PHPH 5.3 from source.

Personally, I'd just compile from source. It's not that complicatedn abd it's guaranteed to work.

can you teach me how to do that? im still a newbie at installing lamp servers because im primarily just a plain php guy but since we dont have a systems admin now im left with the job of doing it. i dont want to mess things up. thanks

---

