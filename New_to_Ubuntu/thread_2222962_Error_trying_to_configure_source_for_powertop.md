---
title: "Error trying to configure source for powertop"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by papa.jinzu on 2014-05-08
Hello,

I am running into a problem when trying to install powertop 2.5 I get this error always:

```
configure: error: libnl and libnl-genl are required but were not found
```

I did this 
```
sudo apt-get install libnl-dev
```

and
```
sudo apt-get install libnl-genl-dev
```

but still the same error messages after the previous two finished installing.

How to get ./configure to work?

---

### Post by papa.jinzu on 2014-05-08
Got it to work by going here 
```
http://www.ubuntuupdates.org/package/core/trusty/main/base/powertop
```
and clicking on apt install

I still would like to know about why I could not install it via source if anyone has any answers. Thanks.

---

