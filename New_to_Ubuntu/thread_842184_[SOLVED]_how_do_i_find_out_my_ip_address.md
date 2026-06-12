---
title: "[SOLVED] how do i find out my ip address?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by leemajors on 2008-06-27
in windows i use ipconfig /all

this tells me what the ip address of the machine i'm using.

what is the equivalent command in ubuntu?

---

### Post by jordanmthomas on 2008-06-27
```
ifconfig
```

---

### Post by iaculallad on 2008-06-27
> **leemajors said:**
> in windows i use ipconfig /all

this tells me what the ip address of the machine i'm using.

what is the equivalent command in ubuntu?

On your terminal:

```
ifconfig
```

---

### Post by squaregoldfish on 2008-06-27
ifconfig is the tool for this. It will list all your network interfaces, and the second line starts with 'inet addr:', which is your IP address.

Steve.

---

### Post by sevanovg on 2008-07-15
Go to [http://smart-ip.net/en/](http://smart-ip.net/en/)
u can find ur IP there

---

### Post by halitech on 2008-07-15
> **sevanovg said:**
> Go to [http://smart-ip.net/en/](http://smart-ip.net/en/)
u can find ur IP there

nice site but that would only work if the person is looking for their external IP address and is behind a router. ipchicken.com is another one.

---

