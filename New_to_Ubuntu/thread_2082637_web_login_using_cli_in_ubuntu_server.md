---
title: "web login using cli in ubuntu server"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by termvrl on 2012-11-10
hi all,
i just want to ask,
how we can login web proxy using cli. i need to login user/passwd for acces internet.

Thanks.

---

### Post by HiImTye on 2012-11-10
if you mean that you need to log in to a rich web page using a text based console, you can try lynx

```
sudo apt-get install lynx
```

---

### Post by jerome1232 on 2012-11-10
[http://askubuntu.com/questions/47379/how-to-use-a-proxy-on-the-command-line](http://askubuntu.com/questions/47379/how-to-use-a-proxy-on-the-command-line)

Essentially you need to modify an environment variable
You put it in /etc/environment for a system wide settings ~/.pam_environment for a per user setting.

add a line like this, modifying for real values

```

export http_proxy="http://username:password@proxyaddress:port"
```

---

### Post by Lars Noodén on 2012-11-10
The two main web proxies are [squid](http://www.squid-cache.org/) and [varnish](https://www.varnish-cache.org/).  Which one are you using?

---

### Post by termvrl on 2012-11-10
hi all,
im using a hp procurve.
so my lan and wifi will go through this device.
so i need to login.

thanks.
i will try the solution first.

---

