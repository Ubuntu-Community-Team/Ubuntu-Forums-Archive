---
title: "Ubuntu client connected to Windows server"
date: 2009-05-11
forum: Philippine Team
---

### Post by jonardds on 2009-05-11
Is it possible to connect an Ubuntu client to Windows server? Please help

---

### Post by loell on 2009-05-11
by way of?

file/print sharing? http client/server?  or active directory?

---

### Post by cloud69 on 2009-05-12
Kong peer to peer lang, wala akong nakita bakit hindi. :popcorn:

---

### Post by kingkalag on 2009-05-12
i know pwedi kang maka connect, did it before when I was using win 03 enterprise dito sa bahay 3 years ago install ko uli ang win03server pag makahanap ako ng extra na HDD

---

### Post by leipogs23 on 2009-05-12
Isn't it possible using Samba????

---

### Post by loell on 2009-05-12
> **leipogs23 said:**
> Isn't it possible using Samba????

yes, but lets wait for the OP on elaborating more  at what he wants to achieve.

---

### Post by jonardds on 2009-05-14
[FONT=&#44404;&#47548;]Oops sorry po sa delayed reaction[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]here[/FONT][FONT=Arial]&#8217;[/FONT][FONT=&#44404;&#47548;]s the scenario[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]meron akong server running on Windows (sa Icafe ko) so I[/FONT][FONT=Arial]&#8217;[/FONT][FONT=&#44404;&#47548;]m planning to add computers but with Ubuntu OS. Pwede ko bang maiconnect yan sa Windows server and to function like a Windows client(s)[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]functions like internet connection, LAN games and etc. As of now kasi puro Windows XP pa ang mga pc ko[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]parang transition na rin to[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]pero hindi ko pa kayang i-all out na Ubuntu kasi baka maapektuhan ang business ko[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;] hope you can give tips and help[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]thanks[/FONT][FONT=Arial]&#8230;[/FONT]

---

### Post by leipogs23 on 2009-05-14
> **jonardds said:**
> [FONT=&#44404;&#47548;]Oops sorry po sa delayed reaction[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]here[/FONT][FONT=Arial]&#8217;[/FONT][FONT=&#44404;&#47548;]s the scenario[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]meron akong server running on Windows (sa Icafe ko) so I[/FONT][FONT=Arial]&#8217;[/FONT][FONT=&#44404;&#47548;]m planning to add computers but with Ubuntu OS. Pwede ko bang maiconnect yan sa Windows server and to function like a Windows client(s)[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]functions like internet connection, LAN games and etc. As of now kasi puro Windows XP pa ang mga pc ko[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]parang transition na rin to[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]pero hindi ko pa kayang i-all out na Ubuntu kasi baka maapektuhan ang business ko[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;] hope you can give tips and help[/FONT][FONT=Arial]&#8230;[/FONT][FONT=&#44404;&#47548;]thanks[/FONT][FONT=Arial]&#8230;[/FONT]

Haha. lucky guess. Read this:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by loell on 2009-05-14
> functions like internet connection, LAN games and etc. As of now kasi puro Windows XP pa ang mga pc ko…parang transition na rin to

i see you mean internet connection sharing, depending on how you structure your network say you have a router and swithces, you don't have to configure anything from you windows server to share connections, even lan based games in linux (native or in wine), you just point the game server from the linux boxes to the windows server. do tell us what your current network structure is, with windows.

---

