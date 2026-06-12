---
title: "Privoxy config"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Ntweat on 2008-09-13
I have 2 net connections... one is via a DHCP and the other is through a proxy i have installed on another computer


the privoxy is using the net which is via the DHCP but i want it to use the net through the proxy how to configure it?? thanks

---

### Post by Squish on 2008-09-13
in firefox, You go to Edit>Preferences>Advanced>Network
and click on the connections settings.
Then you can configure the proxies or whatever

---

### Post by acidsolution on 2008-09-14
open your .bashrc file and add line 
```
export http_proxy=http://proxyaddress:port
```

if your proxy needs authentication than write 
```
export http_proxy=http://username:password@proxyaddress:port
```

type bash to reload bash config

---

