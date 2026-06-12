---
title: "HOWTO: Fastest way to get connected to your office PC - MS VPN, pptp-linux, rdesktop"
date: 2007-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by robajz on 2007-10-22
```

# sudo apt-get update
# sudo apt-get install pptp-linux ppp rdesktop
(positive answers)

```

```

# sudo nano /etc/ppp/chap-secrets

(type: )
myusername PPTP mypassword *

(press <F3> <Enter> <F2>)

```
(bewere that if you use a domain this needs to be escaped and in format: DOMAIN\user ... what is the escape sequence?)


```

# sudo nano /etc/ppp/peers/myvpn

(type: )
pty "pptp mypptp.server.net --nolaunchpppd"
name myusername
remotename PPTP
require-mppe-128
file /etc/ppp/options.pptp
ipparam myvpn

(press <F3> <Enter> <F2>)

```

```

# sudo pppd call myvpn

```

```

# sudo route add -host 192.168.555.555 dev ppp0

```

```

rdesktop 192.168.555.555

```

You can find this tutorial for Ubuntu: [HOWTO: Connect to a Microsoft PPTP VPN]("http://ubuntuforums.org/showthread.php?t=91249")

And better [another one for ubuntu and fedora]("http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html")

Use the later one as an explanation.

---

