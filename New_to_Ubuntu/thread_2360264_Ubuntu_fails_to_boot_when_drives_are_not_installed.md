---
title: "Ubuntu fails to boot when drives are not installed"
date: 2017-05-02
forum: New to Ubuntu
---

### Post by ashtonian2 on 2017-05-02
Hello, 

I have a "headless" with ubuntu desktop installed. The fstab looks like: 

```

# 4TB Media
UUID=ea2e3faa-f963-4c5d-8073-60a8831b9b87       /media/Fitzroy  ext4    errors=continue 0       0
UUID=33d180de-0ffb-47d3-8518-4b8a391b0fe4       /media/Atlas    ext4    errors=continue 0       0
UUID=5ba0563f-c9fc-4cdf-bc2d-b7b0553b9e21       /media/Fontaine ext4    errors=continue 0       0

# 4TB Parity
UUID=7416a3ff-8d0e-4891-8e85-b96613dbb050       /media/Ryan     ext4    errors=continue 0       0

# 6TB Media

# 6TB Parity

# MergerFS
/media/Atlas:/media/Fontaine:/media/Fitzroy /media/Lutece fuse.mergerfs  direct_io,defaults,allow_other,minfreespace=200G 0 0
```

The desired behavior is that it will mount all the drives if everything is working, else it will continue to boot so I can get access to it remotely. Otherwise kind of kills the headlessness. What should I do ? Reading through the logs in the emergency console a systemd mount service is failing ?

---

### Post by QIII on 2017-05-02
Hello!

You might try adding nobootwait to the options.  This tells mountall not to hold up the boot process for any specified devices not present.

Let us know if that works for you.

---

### Post by ashtonian2 on 2017-05-02
thanks for the response - that does not work. EXT4-fs reports "Uncrecognized mount option "nobootwait" or missing value/.

---

### Post by Keith_Helms on 2017-05-03
Use option nofail.

---

### Post by QIII on 2017-05-03
Urg.  systemd.  Nobootwait doesn't work.

Nofail might be a pain because it has to time out.


[http://manpages.ubuntu.com/manpages/zesty/man5/systemd.mount.5.html](http://manpages.ubuntu.com/manpages/zesty/man5/systemd.mount.5.html)

---

