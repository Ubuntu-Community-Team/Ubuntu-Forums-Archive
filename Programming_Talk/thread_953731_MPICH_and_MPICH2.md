---
title: "MPICH and MPICH2"
date: 2008-10-20
forum: Programming Talk
---

### Post by Qtips on 2008-10-20
Hi, 

I need to install MPICH and MPICH2 on my Ubuntu box but i don't know how to do it! Can somebody help me to install and test the installation ?

Thanks !

---

### Post by rautamiekka on 2009-06-03
I found this -> [https://help.ubuntu.com/community/MpichCluster](https://help.ubuntu.com/community/MpichCluster) <- but haven't tested it myself yet, but am interested. Please let us know how your proceeding with the guide goes :)

---

### Post by monkeyking on 2009-06-04
I installed it 3 years ago on 8 ubuntuboxes.
It was absolutely hell.

I couldn use the loopback adr for the hosts themselves.

So i had to change my hosts from

```

mach1 127.0.01
mach2 192.168.0.1

```

to something like

```

mach1 192.168.0.15
mach2 192.168.0.1

```

---

### Post by rautamiekka on 2009-06-04
> **monkeyking said:**
> I installed it 3 years ago on 8 ubuntuboxes.
It was absolutely hell.

I couldn use the loopback adr for the hosts themselves.

So i had to change my hosts from

```

mach1 127.0.01
mach2 192.168.0.1

```

to something like

```

mach1 192.168.0.15
mach2 192.168.0.1

```Uhh, to me you sound like a single simple additional change gave it "hell" status, right ?

---

### Post by monkeyking on 2009-06-04
> **rautamiekka said:**
> Uhh, to me you sound like a single simple additional change gave it "hell" status, right ?

Well,
the hell status is not related to the simplicity of a fix,
but how annoying it is to track down.

---

