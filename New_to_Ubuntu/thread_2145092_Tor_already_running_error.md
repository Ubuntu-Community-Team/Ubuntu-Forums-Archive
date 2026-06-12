---
title: "Tor already running error"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by Deezid93 on 2013-05-14
I saw this error in other places, tried running Tor in terminal as root. Got this error: 

May 14 16:03:06.565 [notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
May 14 16:03:06.565 [notice] Opening Socks listener on 127.0.0.1:9050
May 14 16:03:06.565 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 14 16:03:06.567 [notice] Opening Control listener on /var/run/tor/control
May 14 16:03:06.567 [notice] Closing partially-constructed listener Control listener on /var/run/tor/control:0
May 14 16:03:06.568 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
May 14 16:03:06.568 [err] Reading config failed--see warnings above.


then I did::~$ ss -aln | grep 9050
LISTEN     0      128               127.0.0.1:9050                     *:*  

9050 is highlighted in red.

Any clues on what this error means?

---

### Post by Frogs Hair on 2013-05-14
Hello and Welcome

It is not advisable to run any browser as root . Try the following in the terminal and report any errors.
 
```
killall tor
``````
 tor
```

---

### Post by Deezid93 on 2013-05-14
Done. This is what it showed:
May 14 19:35:21.498 [notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
May 14 19:35:21.499 [notice] Opening Socks listener on 127.0.0.1:9050
May 14 19:35:21.499 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 14 19:35:21.499 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
May 14 19:35:21.499 [err] Reading config failed--see warnings above.
deniz@deniz-TOSHIBA-NB255:~$ ss -aln | grep 9050
LISTEN     0      128               127.0.0.1:9050                       *:*

---

### Post by Frogs Hair on 2013-05-14
It looks like you already found the Ubuntu documentation so, you may have to wait for a tor user. I had tried the Tor Browser Bundle on 12.04  which installed FF nightly at that time and it started automatically with no command line requirements to open the browser.
 
 [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

---

