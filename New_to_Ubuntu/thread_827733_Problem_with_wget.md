---
title: "Problem with wget"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-13
When ever i tried to use wget i get this error.

```
raj@raj-workstation:~$ wget www.ethicaluniversity.com
Error parsing proxy URL http://:8080/: Invalid host name.
raj@raj-workstation:~$ 


```

one week ago i installed squid but i removed it later.

whats the error now and what should i change to get back.

---

### Post by iaculallad on 2008-06-13
Try to select "Direct Internet Connection" (If you have proxies configured) in your Network Proxy Preferences. System->Preferences->Network Proxy.

---

### Post by rraj.be on 2008-06-13
Thanks dude.I changed it.

But now i want to setup a good proxy to speed up my system a bit.
'Can u help me.

---

### Post by iaculallad on 2008-06-13
In any way dudes. Try setting up tinyproxy or [Oops]("http://zipper.paco.net/~igor/oops.eng/help.html") in your system. Both are available for download using Synaptics.

---

### Post by rraj.be on 2008-06-13
I installed Tiny proxy.Now how can i configure it?

---

### Post by iaculallad on 2008-06-13
Take a peek on this [thread]("http://ubuntuforums.org/showthread.php?t=122011").

---

