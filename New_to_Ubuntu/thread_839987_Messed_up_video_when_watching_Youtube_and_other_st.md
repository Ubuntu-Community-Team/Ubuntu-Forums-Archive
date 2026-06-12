---
title: "Messed up video when watching Youtube and other streamed feeds."
date: 2008-06-24
forum: New to Ubuntu
---

### Post by steve101101 on 2008-06-24
When i watch youtube on my laptop without any graphics card running ubuntu 8.04 it runs just as good as windows does. However my desktop running ubuntu 8.04 which has a Nvidia 8600GT displays youtube videos and others slowly. They look as if it is having trouble keeping up with the frame rate. I don't know how to fix this b/c i have updated my drivers with the command ...

```

envyng -t

```

How to i remedy this???

---

### Post by iaculallad on 2008-06-24
Try using GNASH instead of Adobe's proprietary flash player. GNASH is available in the repo.

```
sudo apt-get install gnash
```

---

### Post by steve101101 on 2008-06-24
its already installed, but does no better.

---

### Post by iaculallad on 2008-06-25
-My error: You'd used Envy-

---

### Post by steve101101 on 2008-06-25
the nvidia driver version is 173.14.05 i believe its the newest one.

---

### Post by iaculallad on 2008-06-25
What about using:

```
sudo nvidia-settings
```

or

```
sudo nvidia-xconfig
```

to reconfigure your NVIDIA setting.

---

### Post by steve101101 on 2008-06-25
and do what ...

---

### Post by steve101101 on 2008-06-25
i have typed both of them, but doesn't help

---

