---
title: "Shutdown does not work as intended"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2011-12-27
[Ubuntu 11.04]

Hi,

Shutdown using the Shutdown Button works. But when i use the shutdown command using the Terminal, Ubuntu wont shut down (i.e. shutdown 15). It automatically tries to shutdown the system when the time is running out but than freezes showing the Ubuntu Logo with the 5 Points

Similar Picture i found using google:
([http://1.bp.blogspot.com/_4B7ZWQHqMpk/TMcEEwqP88I/AAAAAAAAAEc/uVUzQyc32Ik/s1600/boot1.png](http://1.bp.blogspot.com/_4B7ZWQHqMpk/TMcEEwqP88I/AAAAAAAAAEc/uVUzQyc32Ik/s1600/boot1.png))

Thanks

---

### Post by westie457 on 2011-12-27
What happens if you try the -h option
```
sudo shutdown -h 15
```

---

