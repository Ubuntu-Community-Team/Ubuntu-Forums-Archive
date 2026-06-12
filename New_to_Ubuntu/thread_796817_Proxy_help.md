---
title: "Proxy help"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by DMzda on 2008-05-16
To access the internet, I need a proxy server. When I use Firefox with the configured system settings, it just asks me for authentication, and it works.

The problem comes when I try to install a package, using both the terminal and the "Add/Remove..." program. When i reload in Synaptic, it comes up with a 407 Proxy Authentication required... error.

I have searched the forums and tried various methods, but the problem remains.

Any help will be much appreciated.:)

---

### Post by Monicker on 2008-05-16
Is it an ISA proxy?  If so, this thread should help:

[http://ubuntuforums.org/showthread.php?t=589854]("http://ubuntuforums.org/showthread.php?t=589854")

Read through it carefully.  You will need to install ntlmaps and modify some configuration settings.

---

### Post by DMzda on 2008-05-16
Thanks for the quick reply.

Yes, I think it is an ISA proxy. I have followed the steps there, but the problem remains ](*,).

---

### Post by DMzda on 2008-05-16
Sigh...

---

### Post by TroyDowling on 2008-05-16
Have you tried setting up System > Preferences > Network Proxy?

---

### Post by DMzda on 2008-05-16
Yes. That was the first thing I tried.

---

### Post by TroyDowling on 2008-05-16
I see. I wasn't sure if you meant those settings when you said "System Settings" or the ones in Firefox. A silly question now that I think about it. Try this command, obviously substituting in your real info:```
export http_proxy=http://myuname:mypass@myproxy:myport
```

EDIT (Incomplete):

That will work for at least the terminal session. According to this thread, you may need to get a little fancy if your proxy uses NTML authentication. Read up on that here: [http://ubuntuforums.org/showthread.php?t=96802#9](http://ubuntuforums.org/showthread.php?t=96802#9)

---

### Post by DMzda on 2008-05-16
I don't understand that script.
A little help here?

---

### Post by TroyDowling on 2008-05-16
```
export http_proxy=http://myuname:mypass@myproxy:myport
```

'export' takes the value and assigns it to the HTTP_Proxy variable. After 'export http_proxy' type your username, a colon, and your password, at symbol, then the proxy's address wether it's an IP (###.###.###.###) or a domain (proxy.company.com), then another colon, and finally the port that the proxy operates on. If you need more information, you'll probably have to ask your administrator for things like your credentials or the proxy address/port.

Example:

```
export http_proxy=TroyDowling:mypassword@127.0.0.1:7364
```

---

### Post by DMzda on 2008-05-17
Thanks for the help.

I tried the above, but it didn't work. When i type *apt-get update*, it comes up with a long list of 407 errors.

---

