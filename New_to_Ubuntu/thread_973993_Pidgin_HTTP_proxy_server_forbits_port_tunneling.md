---
title: "Pidgin: HTTP proxy server forbits port tunneling"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by abcuser on 2008-11-07
Hi,
on Ubuntu 8.10 laptop computer I use Pidgin 2.5.2. I have three accounts: Google, Yahoo and MSN. At home Pidgin is working well, but at office company is using proxy server that forbids some ports.

1. MSN reports error:
Connection error from Notification server:
Unable to connect

2. Yahoo reports error:
Could not establish a connection with the server:
Access denied: HTTP proxy server forbids port 5050 tunneling.

3. Google reports error:
Could not establish a connection with the server:
Access denied: HTTP proxy server forbids port 5222 tunneling.

For MSN I have set "Use http method" and problem solved. But I can't find out any simiral option in Pidgin for Yahoo and Google. Does Yahoo and/or Google support http method?

Regards,
Abcuser

---

### Post by B34ST1Y on 2008-11-07
are you running through a proxy, or a direct connection to the internet? If you're running through a proxy, it may very well be blocking the ports those programs connect to their servers on

---

### Post by jago25_98 on 2008-11-07
Yeah, he knows that. He's looking for a setting in Pidgin to use http method.

I don't think Pidgin can do that. aMSN might be able to though

---

### Post by abcuser on 2008-11-07
@B34ST1Y, sorry for not be clear enough. At home I use Pidgin to directly connect to internet without proxy, but at office company is using proxy server witch blocks several ports including Yahoo and Google messaging ports. To get around this limitation I used http method for MSN, but there is no http method in Pidgin for Yahoo and Google.

BTW, if using http method can http admin see what I amd writing to my friends with Pidgin? Is it using http or https? Probably it is using 80 port which is http.

---

### Post by abcuser on 2009-01-16
> **jago25_98 said:**
> aMSN might be able to thoughaMSN is only for MSN protocol. I need http for Google Talk.

If I use Google Talk inside Firefox web browser it works fine, but I need to have browser opened. I would like to have http for Google Talk in instant messenger program to notice new contact.

---

### Post by abcuser on 2009-01-25
Hi,
I have filed a idea to Brainstorm:
[http://brainstorm.ubuntu.com/idea/17659/](http://brainstorm.ubuntu.com/idea/17659/)

If you also would like to have this feature implemented, please vote.
Regards

---

### Post by kevdog on 2009-01-26
Have you contacted the developers on #pidgin on irc.freenode.net to make sure this feature is definitely not implemented?  They usually respond in a timely manner to such questions (within minutes).

---

### Post by abcuser on 2009-01-26
Hi,
I have contacted developers in IRC (irc.freenode.net) at #pidgin, but got no answer after 10 minutes, so I quit IRC and filed idea to Brainstorm.
Regards

---

### Post by abcuser on 2009-01-28
Hi,
I have tried one more time in IRC and got answer that http tunneling for Google Talk account is not possible in Pidgin.
Regards

---

### Post by cacedilla on 2010-10-04
set the global **proxy** in 
 Pidgin's preferences must be set to "No **proxy**"

check this link
[http://old.nabble.com/Re%3A--496%3A-Yahoo-will-not-work-through-HTTP-proxy-which-only-allows-80-and-443-td26963252.html](http://old.nabble.com/Re%3A--496%3A-Yahoo-will-not-work-through-HTTP-proxy-which-only-allows-80-and-443-td26963252.html)

---

