---
title: "proxy problems"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by Atryxx on 2011-10-27
I've got linux 10.4 lts lucid lynx running behind a proxy at work,
believe me i've been trying everything to get apt-get and synaptic to work but i keep getting:
- 404 not found
- 407 authentication error

I'm now seriously out of options, can somebody tell me if there is some backdoor way to get this working???

already editted the apt.config
and synaptic preferences
and also tried ntlmaps, none of them works.

---

### Post by taseedorf on 2011-10-27
Try this...
If you’re using Synaptic

Open up your Synaptic package manager (usually as root), go to Settings-> Preference -> Network. Enter your proxy server details like : username:password@proxyserver.net, and put the proxy server port (usually 8080).
If you’re using command-line apt-get

Edit your /etc/bash.bashrc file as root.

Put these line at the end of your /etc/bash.bashrc file :

export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/

You can omit the username:password, if your proxy server has no password.

---

