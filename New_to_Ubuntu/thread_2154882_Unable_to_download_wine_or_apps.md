---
title: "Unable to download wine or apps"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by jd70 on 2013-06-16
Hi All,

This is my second attempt with running ubuntu, I have given up with Win 7 on this netbook.
Anyway, my problem is that I cannot download any apps, I did have an update issue as well with failed downloads but I did a quick search and ran the apt get update line and that seems to have sorted out the updates.

I want to install Wine, but this is the failure message I get;


```
nstallArchives() failed: Setting up libssl1.0.0 (1.0.1-4ubuntu5.9) ... 
Bad name after h' at /usr/share/perl/5.14/unicore/Heavy.pl line 2911, <GEN0> line 1. 
Compilation failed in require at /usr/share/perl/5.14/utf8_heavy.pl line 145, <GEN0> line 1. 
dpkg: error processing libssl1.0.0 (--configure): 
 subprocess installed post-installation script returned error exit status 255 
Setting up man-db (2.6.1-2ubuntu1) ... 
Bad name after h' at /usr/share/perl/5.14/unicore/Heavy.pl line 2911, <GEN0> line 1. 
Compilation failed in require at /usr/share/perl/5.14/utf8_heavy.pl line 145, <GEN0> line 1. 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 255
```

Can anyone point me in the right direction please? I really would appreciate it if I can get this fixed.
Also, compared to the last time I had ubuntu on this netbook it does seem to be running slower........

regards,

JD

---

### Post by user_of_gnomes on 2013-06-16
You say you had issues with the updates as well, did you do an integrity check of the data on the DVD you burned before installing and if so, did it pass?

---

