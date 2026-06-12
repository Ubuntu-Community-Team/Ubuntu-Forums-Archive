---
title: "HELP protected wireless home network recognized only by Root User"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by sarc on 2008-10-21
Hi I have an HP DV2000 and Hardy running and a Compaq nc6400 with Feisty.

My wireless AP has MAC address exclusion and is set to not broadcast SSID. 

Both computers can access under Windows and the nc6400 with Feisty worked flawlessly 1st time around.

But the DV2000 with Hardy will recognize the wireless network only under 2 circumstances: a) If I log in as root user or b) If I remove MAC address filtering and I broadcast SSID.

So why the Root can make wireless work and not other users?  I tried saving the configuration as root but on rebooting I'm back to non-root users being unable to access the wireless.  Could it be something with the new sudo scheme in Hardy?

I could not find similar cases by searching the threads... let me know if any help thanks!!

---

### Post by sarc on 2008-10-21
HULP!  HULLO!?!?!  Is this a bug in Hardy?  Is there some setting I need to change?

---

### Post by spiderbatdad on 2008-10-22
does the user account have permission to access wireless networks, under System>>Administration>>Users and Groups>><account>>>Privileges

---

### Post by sarc on 2008-10-23
Thanks I checked on User Accounts and there is no privilege called 'Wireless'... the closes thing is 'access the internet using a modem', and it is enabled for all users.

---

