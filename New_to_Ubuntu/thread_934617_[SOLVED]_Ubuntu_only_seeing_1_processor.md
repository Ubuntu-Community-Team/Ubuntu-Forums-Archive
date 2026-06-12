---
title: "[SOLVED] Ubuntu only seeing 1 processor"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by coolbrook on 2008-09-30
I just installed Hardy on the first system in my signature but for some reason it's only seeing one processor.  It's an SMP set up.  

What happened:
I had a hard drive failure so I got a replacement under warranty.  Because of my hardware I had to use a Dapper disc in order to upgrade to Hardy.  Prior to the hard drive failure I had no problem with the SMP set up.

Thanks in advance for your help.

---

### Post by Pro-reason on 2008-09-30
I've had this trouble too.  I found that changing to a different kernel fixed it.

---

### Post by coolbrook on 2008-09-30
Well I removed installed instances of linux-image-386, since the generic image was installed and that resolved the problem for SMP, but now my system doesn't want to work with my wireless adapter.  I can see it in lspci but the network manager applet says there are no network devices installed.

---

### Post by oldos2er on 2008-09-30
Dapper's pretty old, you might want to upgrade to Hardy.

---

### Post by coolbrook on 2008-09-30
I resolved the matter by re-installing the 386 kernel so I could get at the restricted modules for my wireless.  Once I did that I was able to connect to the internet and download the 'generic' kernel restricted modules.  I removed the 386 kernel and modules, rebooted and here I am connected with SMP working.

---

