---
title: "Trouble with Adept / apt-get in Dapper"
date: 2006-06-06
forum: Repositories &amp; Backports
---

### Post by ignatsk on 2006-06-06
I've recently switched from SuSE to Kubuntu to see what all the hype was about so I installed it at home and it worked seamlessly; Adept worked perfectly with the default repositories enabled.  When I installed it on a desktop at work, it cannot connect to the repositories and just sit at "waiting for headers".  Does anyone know if Adept uses certain ports or protocols that might be blocked, because apt-get in SuSE worked only a day before.

Thanks.

---

### Post by localzuk on 2006-06-06
If your workplace uses any form of proxy, this will need to be configured.

---

### Post by ignatsk on 2006-06-06
Yea, IT claims they don't use any proxies, and I've never had to configure one before.  It's just strange that apt-get worked in SuSE, but in Ubuntu/Kubuntu it doesn't.

---

### Post by localzuk on 2006-06-06
Can you connect to any websites and/or ping them/resolve them from the console?

Try running 'ping google.com' and see what happens.

---

### Post by ignatsk on 2006-06-07
After looking the configuration of another apt-get version that still works on our network here I noticed that the new version of Kubuntu's apt.conf file has "Acquire::http::Proxy "false" as default.  After deleting that line it works.  Thanks for your help.

---

### Post by handy on 2006-06-10
It was the only line in the **apt.conf** file, I deleted it, but it made no difference?

---

