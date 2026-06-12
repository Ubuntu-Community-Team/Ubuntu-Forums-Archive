---
title: "HTTPS problems"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by jonnym2008 on 2008-06-19
I&#8217;m very new to Ubuntu, so please bear with me!

I installed Ubuntu 8.4 server edition. All went well, Mozzila worked great and i had no problems.

I updated every thing via the update manager and i can no longer view https websites. I get the error:
"Failed to Connect
the connection was refused when attempting to contact login.live.com" 

I can access the same page on my windows box, on the same network.

Any ideas?

thanks in advance

Jon

---

### Post by UltraMathMan on 2008-06-23
Do you have openssl and ssl-cert installed? Don't know if Ubuntu Server installs it by default or not.

```
sudo apt-get install openssl ssl-cert
```

-Hope this helps :)

---

### Post by vikramaditya on 2008-06-23
FF balked at secure websites for me, too.  So I d/l'ed & installed Opera 9.5 (from their site, not the ubuntu repos) and all is well!

---

