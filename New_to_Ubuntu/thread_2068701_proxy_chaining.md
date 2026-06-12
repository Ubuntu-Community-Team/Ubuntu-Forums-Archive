---
title: "proxy chaining"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by proxy error on 2012-10-09
hi guys,
im having some trouble chaining proxies.  

i go into terminal then run

*nano /etc/proxychains.conf*

then add the list in like this

[I][ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
socks4  127.0.0.1 9050
socks5  59.21.114.99    5577[/I]

then open new tab and run

*proxychains firefox*

and all i get is

[I]ProxyChains-3.1 ([http://proxychains.sf.net](http://proxychains.sf.net))
mainuser@mainuser-VirtualBox:~$ [/I]

firefox opens but when i google my ip address its not what it says in the list

please help

thanks

---

### Post by proxy error on 2012-10-09
i am running ubuntu on a virtual machine, that is configured to access the internet throufg tor.

---

### Post by proxy error on 2012-10-10
**proxy chaining** 			
 			 			 		   		 		 		hi guys,
im having some trouble chaining proxies.  

i go into terminal then run

*nano /etc/proxychains.conf*

then add the list in like this

[I][ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
socks4  127.0.0.1 9050
socks5  59.21.114.99    5577[/I]

then open new tab and run

*proxychains firefox*

and all i get is

[I]ProxyChains-3.1 ([http://proxychains.sf.net](http://proxychains.sf.net))
mainuser@mainuser-VirtualBox:~$ [/I]

firefox opens but when i google my ip address its not what it says in the list

i am running ubuntu on a virtual machine that is configured to go through tor

please help

thanks

---

### Post by overdrank on 2012-10-10
Hi and welcome, please do not create multiple threads on the same issue. Threads merged.

---

