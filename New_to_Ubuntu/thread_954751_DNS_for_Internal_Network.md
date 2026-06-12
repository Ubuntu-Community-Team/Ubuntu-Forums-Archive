---
title: "DNS for Internal Network"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by nixforme on 2008-10-21
I would like to setup my home network so when I ssh to a machine or browses the machine internally via the web, it resolves a name. I have no experience with Bind and am really confused from all the stuff I read about DNS and bind. Can some one point me the the right direction for this? How I would set it up? does it require a dedicated server?

---

### Post by Sarmacid on 2008-10-21
You could set up a dns server with bind but it'd have to be up any time you want it to resolve a name, so about the server being dedicated depends on your needs.

An easier approach would be to just add the ips and names of the machines to the /etc/host file.

---

### Post by Iowan on 2008-10-21
For a small (or) home network, check **dnsmasq**.  It (reportedly) ties DNS and DHCP together, so DHCP clients can be addressed by hostname. It's available as a (Synaptic) package for Gutsy - I suspect it's also available for Hardy.

---

