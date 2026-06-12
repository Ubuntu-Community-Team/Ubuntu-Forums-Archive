---
title: "How to enable default SSH?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-07-23
Hi,
Please could someone briefly just tell me what SSH is, and how to enable it for remote access? If there is no default, I am quite happy trudging through a more complete resource to find answers.. ;]
Good morning~

---

### Post by Oldsoldier2003 on 2008-07-23
> **hungryOrb said:**
> Hi,
Please could someone briefly just tell me what SSH is, and how to enable it for remote access? If there is no default, I am quite happy trudging through a more complete resource to find answers.. ;]
Good morning~

Are you trying to enable remote users to ssh into your machine? if this is the case

```
sudo apt-get install openssh-server
```

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by Joeb454 on 2008-07-23
Morning :)

It's a Secure Shell basically. To enable it for remote access in another location, you would need to dabble in port-forwarding with some routers etc.

You need the "openssh-server" package installed on the remote machine too :)

---

### Post by hungryOrb on 2008-07-23
Thanks very much. =)

---

### Post by Portmanteaufu on 2008-07-24
Once you've got openssh-server installed on the machine you're going to be trying to SSH to, you can log in to that machine by using the command: 

ssh username@ipaddress

or 

ssh ipaddress -l username

If the computer you're trying to reach is behind a router, you'll have to forward port 22 to the right machine. If you go to 

[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

They provide free, router-model-specific instructions on how to forward a port.

---

### Post by Joeb454 on 2008-07-24
It might be better to change the port, but that may be getting a little advanced ;)

---

### Post by bodhi.zazen on 2008-07-24
See thses links :

[uwiki]SSHHowto[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

---

