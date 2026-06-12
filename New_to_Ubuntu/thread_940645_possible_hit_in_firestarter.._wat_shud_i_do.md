---
title: "possible hit in firestarter..?? wat shud i do?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-10-07
hi all,

i have firestarter installed in my pc. suddenly, its icon in my tray changed to red and showed me "hit detected" . and it showed me an ip address. 
i dont have any network and i have just a simple pc with an ethernet device. thats all.how should i react to such events. ??
i am new to this firewall thing ... please help

---

### Post by Orange_and_Green on 2008-10-07
Hello :)

I assume that by "I don't have any network, [...]just[...]an ethernet device" you mean you don't have built a LAN at your home and you connect directly to the internet via ethernet, as asking this question about a PC physically disconnected to any network would be meaningless.

If this is correct, could you please post
1) The IP address in question
2) The packet protocol (FTP / UDP)
3) The service requested (telnet, http, ftp...)

(Remember, we don't have a crystal ball...) ;)

You should have this data in firestarter's logs.
Anyway, don't worry. Since firestarter detected the connection request, it means it blocked it.

---

### Post by Orange_and_Green on 2008-10-07
AARGH double post. Sorry. Don't know why it happened.

---

### Post by jerome1232 on 2008-10-07
Yeah it honestly is nothing to worry about, I'm surprised your not getting hits all day every day.

That being said if your not running anything on the computer to connect to then you have 0 worries. (default install doesn't have any services listening for connections from the outside world, so all incoming connections are dropped)

---

