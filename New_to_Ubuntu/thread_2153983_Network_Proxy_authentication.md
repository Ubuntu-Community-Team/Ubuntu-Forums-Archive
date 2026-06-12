---
title: "Network Proxy authentication"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by rahbz on 2013-06-13
I have added these lines in /etc/apt/apt.conf
Acquire::http:: proxy "http://intern:intern@192.168.1.18:3128/";
Acquire::ftp:: proxy "ftp://intern:intern@192.168.1.18:3128/";
Acquire::https:: proxy "https://intern:intern@192.168.1.18:3128/";
Acquire::socks:: proxy "socks://intern:intern@192.168.1.18:3128/";

(here : p is without space used just before proxy)

even after adding I am gettin this 404 error while apt-get update
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz)  404  Not Found
E: Some index files failed to download, they have been ignored, or old ones used instead.

Thanks,

---

### Post by _0R10N on 2013-06-13
If this is only for getting apt-get to work, you might try the following.

```

# [COLOR=#333333]export http_proxy=http://user:password@proxy_server:port
[/COLOR]# apt-get update

```

If this should be a permanent solution, consider adding it to your .bashrc file.

---

### Post by rahbz on 2013-06-21
Hi, 
I have added the same and also exported in bash
Even though I am getting 404 Not Found error while apt-get update

---

