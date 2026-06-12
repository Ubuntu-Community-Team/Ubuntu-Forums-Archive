---
title: "Can't start bzr inet/xinet smart server"
date: 2008-06-05
forum: Programming Talk
---

### Post by mitchy_g on 2008-06-05
Hi,
Im trying to get bzr running as an inet or xinet service. (I'm running Fiesty)

I have added a new file into /etc/xinet.d/bzr. This file contains:
```

service bzr
{
        socket_type = stream
        protocol = tcp
        wait = no
        user = bzr
        server = /usr/bin/bzr
        serverargs = serve --verbose --inet --directory=/home/bzr/code/
        port = 4155
        disable = no
}

```

Then I issue the restart command for xinet:
```
sudo /etc/init.d/xinetd restart
```

However I cannot connect and using netstat I cannot see any ports listening.

Any suggestions would be appreciated
Mitch

---

