---
title: "assigning a .com domain to my server?"
date: 2007-04-13
forum: Programming Talk
---

### Post by nandasunu on 2007-04-13
A friend has paid for a dedicated server (not managed by the hosting company) and has bought separately a .com domain name. How can I assign the domain to his server? 

Unfortunately the server is running Windows 2003 server, does this make any difference to the setup?

Thanks

---

### Post by grogoreo on 2007-04-13
Hi

Well firstly you need a DNS server. I believe, generally, you shouldn't have the DNS server on the same machine and I think there are free alternatives. So then you would point your domain from whoever you have it managed by, say UKReg. Then you will have a DNS record on the DNS server which will translate the domain name into an IP address of your dedicated machine.
Maybe your friends dedicated server provider provides a name servers that mine does (though I only have a virtual machine from Bytemark).

Hope this helps,
Greg

---

### Post by nandasunu on 2007-04-14
Thanks, that clears it up.

---

### Post by grogoreo on 2007-04-14
No problem

---

