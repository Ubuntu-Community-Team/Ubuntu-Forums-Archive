---
title: "Traceroute"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by Oweirdone on 2013-04-25
In Windows there is a command, as you probably know, called tracert <ip address> that logs the different gateways etc and can be used to help identify a connection issue. I have tried to google the Linux alternative but I was unable to understand any of it :\

Is it possible to have an explanation of how to use in laymans terms please? :)

Many thanks

Owe.

---

### Post by steeldriver on 2013-04-25
Yes traceroute has a lot of options, but at its simplest you can use it exactly the same as Windows tracert i.e.

```
traceroute *<ipaddress>*
```

However iirc traceroute is no longer installed by default - if you don't want to install it you can use tracepath instead

```
tracepath *<ipaddress>*
```

You can use [FONT=courier new]man tracepath[/FONT] to find out more

---

### Post by Oweirdone on 2013-04-25
Many thanks, this did exactly what I wanted it to :)

---

### Post by tripp98 on 2013-04-27
mtr <ip address> is also a great tool

---

