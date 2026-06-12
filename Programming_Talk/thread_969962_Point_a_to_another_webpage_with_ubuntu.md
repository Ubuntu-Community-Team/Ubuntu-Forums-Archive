---
title: "Point a to another webpage with ubuntu"
date: 2008-11-03
forum: Programming Talk
---

### Post by oneadvent on 2008-11-03
Is there anyway to setup a way to say MYCOMPUTERSIPADDRESS:50001 goes to another internal webpage, but on another server?

That way I could have one at 192.168.1.252 as MYCOMPUTERSIPADDRESS:50001 and 192.168.1.253 as MYCOMPUTERSIPADDRESS:50002 for the purpose of setting up AJAX, (who does not like different domains.)

Thanks for any answers on how to do this.

---

### Post by CptPicard on 2008-11-04
Hmm... apache proxying perhaps?

---

### Post by oneadvent on 2008-11-04
how do i do that?

---

### Post by CptPicard on 2008-11-04
[http://httpd.apache.org/docs/2.0/mod/mod_proxy.html](http://httpd.apache.org/docs/2.0/mod/mod_proxy.html)

---

### Post by oneadvent on 2008-11-04
awesome, that looks like it will do nicely.

One question though, will it allow for POST to be forwarded?

---

### Post by CptPicard on 2008-11-04
No idea, but I see no reason why not...

---

### Post by oneadvent on 2008-11-04
Alrighty sounds like what I need to make this happen, thanks.

---

