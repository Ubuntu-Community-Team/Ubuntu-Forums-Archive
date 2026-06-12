---
title: "Limiting internet access to only a few IPs"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by siddharth007 on 2012-09-10
How do i limit my internet connection to access only a bunch of ip addresses while blocking/disabling others ?

---

### Post by iponeverything on 2012-09-10
this is a function of your wireless router and how will be specific to the type of wireless router you have.

---

### Post by newb85 on 2012-09-10
> **iponeverything said:**
> this is a function of your wireless router and how will be specific to the type of wireless router you have.

That's not necessarily true.

While I don't have any personal experience with it, I would recommend OpenDNS based on what I've read.

---

### Post by mcduck on 2012-09-10
Setting up a firewall would be the most common solution... You could give Gufw a try, it's rather neat and simple tool for configuring Ubuntu's firewall, just create a rule to block all connections and then add rules to allow connections to the IP addresses you want.

edit: You'll find Gufw in the Software Center, and here's a guide to using it: [https://help.ubuntu.com/community/Gufw]("https://help.ubuntu.com/community/Gufw")

---

### Post by iponeverything on 2012-09-10
> **newb85 said:**
> That's not necessarily true.

While I don't have any personal experience with it, I would recommend OpenDNS based on what I've read.

its always nice when someone chooses to honor your choice of DNS servers..

---

### Post by iponeverything on 2012-09-10
> **mcduck said:**
> Setting up a firewall would be the most common solution... You could give Gufw a try, it's rather neat and simple tool for configuring Ubuntu's firewall, just create a rule to block all connections and then add rules to allow connections to the IP addresses you want.

edit: You'll find Gufw in the Software Center, and here's a guide to using it: [https://help.ubuntu.com/community/Gufw]("https://help.ubuntu.com/community/Gufw")

works wonderful if everything is going trough your box..

---

### Post by mcduck on 2012-09-10
> **iponeverything said:**
> works wonderful if everything is going trough your box..
If you want to have control over multiple machines, you'll of course have to configure the firewall in your router instead.

---

