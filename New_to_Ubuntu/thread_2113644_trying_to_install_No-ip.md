---
title: "trying to install No-ip"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by 101kitty on 2013-02-07
i'm not sure how to install tar files, i'm trying to install this.

```
https://www.noip.com/downloads.php?page=linux
```

---

### Post by papibe on 2013-02-07
Hi 101kitty.

The package 'ddclient' is compatible with no-ip protocol. It is in the repositories and it is very easy to configure:
```
sudo apt-get install ddclient
```

This is from 'ddclient --help':
```
The 'No-IP Compatible' protocol is used to make dynamic dns updates
over an http request.  Details of the protocol are outlined at:
http://www.no-ip.com/integrate/

Configuration variables applicable to the 'noip' protocol are:
  protocol=noip                    ## 
  server=fqdn.of.service       ## defaults to dynupdate.no-ip.com
  login=service-login          ## login name and password  registered with the s
ervice
  password=service-password    ##
  fully.qualified.host         ## the host registered with the service.

Example ddclient.conf file entries:
  ## single host update
  protocol=noip,                                        \
  login=userlogin@domain.com,                                \
  password=noip-password                           \
  myhost.no-ip.biz 

```
Hope it helps. Let us know how it goes.
Regards.

---

