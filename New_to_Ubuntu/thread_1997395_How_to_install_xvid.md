---
title: "How to install xvid?"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-05
Hi,

Due a tearing problem I am experiencing (more details in this [_post_]("http://ubuntuforums.org/showthread.php?t=1997387") )

I was thinking to install the latest xvid driver to see if it helps my issue.

From [_here_]("http://ftp.br.debian.org/debian-multimedia/pool/main/x/xvidcore/") I have downloaded ```
libxvidcore-dev_1.3.2-0.6_amd64.deb
```


When I double click on it the Software Center opens up and says 

```
Dependency is not satisfiable: libxvidcore4(=3:1.3.2-0.6)
```

What does that mean and what to do?

Many Thanks,
Houman

---

### Post by sanderj on 2012-06-05
Can you use VLC? It plays all formats.

---

### Post by Houmie on 2012-06-05
yeah I found the tearing problem. It can be set within Ati Control Center. Had nothing to do with Xvid as such. :)

Solution is within the link above...

But still it would be interesting to understand why I can't install the latest xvid.

---

### Post by brainwash on 2012-06-05
The -dev package only contains header files and other development stuff. You should install **libxvidcore4_1.3.2-0.6_amd64.deb** instead.[U]
[/U]

---

### Post by mastablasta on 2012-06-05
also you might need do it like this:
 
[INDENT]sudo dpkg -i package_file.deb[/INDENT]

---

### Post by Houmie on 2012-06-06
> **brainwash said:**
> The -dev package only contains header files and other development stuff. You should install **libxvidcore4_1.3.2-0.6_amd64.deb** instead.[U]
[/U]

Ahhh right. Thanks for pointing this out. SO I had chosen the wrong package. :)

---

