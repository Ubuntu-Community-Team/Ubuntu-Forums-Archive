---
title: "Error when upgrade from 11.04 to 11.10"
date: 2011-06-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by miguelpires on 2011-06-18
Hi,
I'm traying to join the fun but when i try to update i get this error message:
Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/pool/main/g/gmp4/libgmp3c2_4.3.2+dfsg-2ubuntu1_amd64.deb](http://pt.archive.ubuntu.com/ubuntu/pool/main/g/gmp4/libgmp3c2_4.3.2+dfsg-2ubuntu1_amd64.deb) 403  Forbidden
and everithing stop.
Anyone now how i can pass this?
Regards
Miguel

---

### Post by coffeecat on 2011-06-18
Hi. I notice that you're using the Portuguese (pt) server. I tried your URL and got the same 403 error. But when I substituted other country servers, those that I tried allowed me access. There's probably a (hopefully temporary) mis-configuration on the Portuguese server. Try changing your download server in Synaptic. Settings > Repositories > Ubuntu Software tab > Download from.

**EDIT**: by the way. The "fun" includes considerable breakage at this point of developement. Don't try to update your main system. It's always advised to keep a stable version of Ubuntu running for your routine use, and to install a development version to a spare partition or separate machine.

But, above all, have fun! :)

---

### Post by miguelpires on 2011-06-20
Thank you coffecat!!
I change the server for updates and work's. Now time to dig and learn how to do thing's and have fun!!
Regard's
Miguel

---

