---
title: "Trouble with permissons and ipod touch"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Ch0chi on 2008-08-01
Ok.. so i've been trying to mount my ipod touch for a couple of days now. I've had no luck. I believe it has to  do with permissions issues. Whenever I do Sudo ipod-touch-mount it gives me fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

Any ideas?




                                                    -Thanks

---

### Post by superbenny on 2008-08-01
Try ipod-touch-mount -nonempty
That sounds like what it's trying to tell you. Iv'e never used this before, but 9/10 times doing what the error message says will work.

---

### Post by Ch0chi on 2008-08-01
Hmm, I tried that and it still gave me the same message...
Any ideas?

---

### Post by Ch0chi on 2008-08-01
bump

---

### Post by LowSky on 2008-08-01
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by Ch0chi on 2008-08-02
I fixed it. I just reformated ubuntu and it works like a charm!

---

