---
title: "Error while installing libcurl package"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by brohit on 2012-02-04
can any one help me regarding the installation of libcurl package:
when i started installing synaptic manager or thru sudo apt-get install it is showing an error as:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-updates/main libcurl3 i386 7.21.3-1ubuntu1.3
  404  Not Found
-Mine Network settings are fine but still it is showing like this.
I tried for sudo apt-get upgrade there also same issue
I am doing all this for the installation of virtual box 
can any one help me in that

---

### Post by cavh on 2012-02-04
Try

```
sudo apt-get update && apt-get install libcurl
```

---

