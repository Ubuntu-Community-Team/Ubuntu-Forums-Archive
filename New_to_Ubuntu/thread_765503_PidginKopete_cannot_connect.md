---
title: "Pidgin/Kopete cannot connect"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by silbers on 2008-04-24
I'm having trouble with Pidgin and other IM clients in general.  I have both Pidgin and Kopete, both which won't sign on.  I just keep getting the message "Could not connect to authentication server: Connection refused" as I am trying to access my AIM screenname. This isn't a problem with internet connection, I can still get online, and I can use web-based apps like meebo to get into the service.

Anyone with similar problems/ suggestions?

---

### Post by silbers on 2008-04-24
This is after I have upgraded to 8.04

---

### Post by dyous87 on 2008-04-24
Can you try manually assigning a port for pidgin to use and opening up that port through your router or modems configuration utility. If using a linksys router or the like, you usually have to enter a number like 192.168.1.1 in your browser.

---

### Post by silbers on 2008-04-24
Yea I can definitely change the port. I'm not hooked into a router, and the port # i have there is something like 5170, whatever it was when i had gutsy gibbon.

---

### Post by dyous87 on 2008-04-24
Your isp should provide you with some kind of configuration tool to open up ports. Do you have any documentation from them?

---

### Post by dyous87 on 2008-04-24
Also what does the command:

```
netstat -an | grep "LISTEN "
```

while trying to connect with pidgin?

---

### Post by ben2talk on 2009-04-16
in my case:

tcp        0      0 0.0.0.0:2628            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN     

same as before launching pidgin . . .

---

