---
title: "Cannot access internet"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by The Pilot on 2008-06-21
I have taken the plunge and switched to Ubuntu. I am still working my way around it but one problem I cannot cure.
Probably something quite simple.
When I run Firefox and try to access Ubuntu or any other site, the progress bar stops halfway and the site will not load,  BUT when I try to access one of my bookmarked sites it loads fine and yet if I try to access another bookmark (e.g eBay)same problem progress bar stops halfway and cannot load the site.
Hope its something simple then I can feel really stupid.
Many thanks

---

### Post by kk0sse54 on 2008-06-21
Have you tried other Web browsers?

---

### Post by beachdrug on 2008-06-21
have you tried reinstalling firefox after saving your "favourites"

---

### Post by oilchangeguy on 2008-06-21
> **The Pilot said:**
> I have taken the plunge and switched to Ubuntu. I am still working my way around it but one problem I cannot cure.
Probably something quite simple.
When I run Firefox and try to access Ubuntu or any other site, the progress bar stops halfway and the site will not load,  BUT when I try to access one of my bookmarked sites it loads fine and yet if I try to access another bookmark (e.g eBay)same problem progress bar stops halfway and cannot load the site.
Hope its something simple then I can feel really stupid.
Many thanks

how are you connecting to the internet? dial-up, dsl, or cable?

---

### Post by linux6994 on 2008-06-21
1. go to System > Administration > Network Tools
2. Perform Netstat on routing tables, you should see your gateway IP.
   ping the gateway IP
3. Under lookup you should be able to see IP for any website ([www.abc.com](www.abc.com))
4. Ping [www.abc.com](www.abc.com)

---

