---
title: "Tor"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by LastDino on 2014-05-07
So, here came a chance for me to use Tor (I don't use it that to often) but it suddenly stopped being able to make connection to tor network.

> glen@Maxwell:~$ tor
May 07 20:03:54.796 [notice] Tor v0.2.4.20 (git-0d50b03673670de6) running on Linux with Libevent 2.0.21-stable and OpenSSL 1.0.1f.
May 07 20:03:54.796 [notice] Tor can't help you if you use it wrong! Learn how to be safe at [https://www.torproject.org/download/download#warning](https://www.torproject.org/download/download#warning)
May 07 20:03:54.796 [notice] Read configuration file "/etc/tor/torrc".
May 07 20:03:54.800 [notice] Opening Socks listener on 127.0.0.1:9050
May 07 20:03:54.800 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 07 20:03:54.800 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
May 07 20:03:54.800 [err] Reading config failed--see warnings above.

It is asking me if Tor is open or not, but it isn't open. How do I approach this? Any ideas?

---

### Post by jdeca57 on 2014-05-07
You could start with:
ps ax | grep Tor
(or tor)
simply to see if there is nothing that started automatically... and if so, kill it.

---

### Post by LastDino on 2014-05-07
> **jdeca57 said:**
> You could start with:
ps ax | grep Tor
(or tor)
simply to see if there is nothing that started automatically... and if so, kill it.

> glen@Maxwell:~$ ps ax | grep Tor
 4357 pts/1    S+     0:00 grep --color=auto Tor


Hmm?

---

### Post by LastDino on 2014-05-07
Solved by old hard method of uninstalling the thing and installing again. Though it would be nice to know what actually went wrong.

---

### Post by rburkartjo on 2014-05-07
last i also had error messages when i tried to download the newest version. had to do the same thing you did and now works fine.

---

### Post by LastDino on 2014-05-07
> **rburkartjo said:**
> last i also had error messages when i tried to download the newest version. had to do the same thing you did and now works fine.

I can confirm this, I managed to replicate the problem. After running updates Tor isn't working again. This time I would like to know whats causing it before I go for  uninstall and installation once again.

---

### Post by newbie2244 on 2014-05-09
Here's what i get on my system when I enter **127.0.0.1:9050** in the url space:
```
Tor is not an HTTP Proxy

It appears you have configured your web browser to use Tor as an HTTP proxy. This is not correct: Tor is a SOCKS proxy, not an HTTP proxy. Please configure your client accordingly.

See https://www.torproject.org/documentation.html for more information. 
```    

NEXT, when I ran the tor command, I got the following:
```
 jmorhead@jmorhead-HP-Pavilion-17-Notebook-PC:~$ tor
May 09 12:19:08.278 [notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
May 09 12:19:08.280 [notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
May 09 12:19:08.280 [notice] Opening Socks listener on 127.0.0.1:9050
May 09 12:19:08.280 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 09 12:19:08.280 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
May 09 12:19:08.280 [err] Reading config failed--see warnings above.

```

Any chance that tor on your system is also not configured correctly?

---

### Post by LastDino on 2014-05-09
> **newbie2244 said:**
> Here's what i get on my system when I enter **127.0.0.1:9050** in the url space:
```
Tor is not an HTTP Proxy

It appears you have configured your web browser to use Tor as an HTTP proxy. This is not correct: Tor is a SOCKS proxy, not an HTTP proxy. Please configure your client accordingly.

See https://www.torproject.org/documentation.html for more information. 
```    

NEXT, when I ran the tor command, I got the following:
```
 jmorhead@jmorhead-HP-Pavilion-17-Notebook-PC:~$ tor
May 09 12:19:08.278 [notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
May 09 12:19:08.280 [notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
May 09 12:19:08.280 [notice] Opening Socks listener on 127.0.0.1:9050
May 09 12:19:08.280 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 09 12:19:08.280 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
May 09 12:19:08.280 [err] Reading config failed--see warnings above.

```

Any chance that tor on your system is also not configured correctly?

That's what I checked first as well, but I've direct wire connection. No proxy has been setup nor there is any controlled traffic.   I even had my firewall turned off to check that. 
Funnily enough though, it is working again after I ran updates and did restart.

---

