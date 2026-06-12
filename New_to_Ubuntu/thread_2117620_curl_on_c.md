---
title: "curl on c"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by sachin0091 on 2013-02-19
heyy

i need to install Curl package on my machine 

i need to post something using Curl'

which all commands i have to type in order to get curl.h file so that my posting is done

lik sudo apt-get.......

any help o suggessions please

thanx...:lolflag:

---

### Post by schragge on 2013-02-19
> **sachin0091 said:**
> which all commands i have to type in order to get curl.h fileYou probably need one of the *libcurl4-*-dev* packages. Which one depends on what SSL provider you need.
```

[color=green]$[/color] apt-file -x search '/curl\.h$'
libcurl4-gnutls-dev: /usr/include/curl/curl.h
libcurl4-nss-dev: /usr/include/curl/curl.h
libcurl4-openssl-dev: /usr/include/curl/curl.h
libdiscover-dev: /usr/include/discover/curl.h
librheolef-dev: /usr/include/rheolef/curl.h

```

---

