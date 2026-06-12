---
title: "Xubuntu network proxy settings"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by cortman on 2011-10-31
How can I change the proxy settings for my network connection? In Xubuntu 11.10.

---

### Post by Toz on 2011-11-01
Add the following to **/etc/environment**:
```

http_proxy="http://user:password@proxy:port"
https_proxy="http://user:password@proxy:port"
ftp_proxy="http://user:password@proxy:port"
export http_proxy https_proxy ftp_proxy
```

Log out and back in again for it to take effect,

---

### Post by cortman on 2011-11-01
I tried, it didn't work.
Is there no GUI way to do it in Xubuntu?

---

### Post by gsmanners on 2011-11-01
It isn't just Xubuntu. Linux as a general rule doesn't "proxy" anything. Certain applications (like Firefox) can set up a proxy connection, but I suspect that's not what you want either. If you have a VPN connection, you can easily configure that through the GUI (using the network applet).

---

### Post by Toz on 2011-11-01
> **cortman said:**
> I tried, it didn't work.
Is there no GUI way to do it in Xubuntu?

Okay. Just verified my settings here at work:
```
-rw-r--r-- 1 root root 296 2011-11-01 12:50 /etc/profile.d/proxy.sh

export http_proxy="http://user:password@proxyserver:port"
export https_proxy="http://user:password@proxyserver:port"
export ftp_proxy="http://user:password@proxyserver:port"

export HTTP_PROXY="http://user:password@proxyserver:port"
export HTTPS_PROXY="http://user:password@proxyserver:port"
export FTP_PROXY="http://user:password@proxyserver:port"

```
...You could also use /etc/environment, but the method is to put your scripts in /etc/profile.d. I just recently rebuilt and added them here this time.

For the apt tools to work, I also have:
```
$ -rw-r--r-- 1 root root 74 2011-10-26 10:09 /etc/apt/apt.conf.d/50proxy

Acquire {
Retries "0";
HTTP {
Proxy "http://user:password@proxyserver:port";
};
};

```

Naturally, I have the correct values in the files in place of the keywords "user" "password" "proxyserver" "port"

---

