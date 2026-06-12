---
title: "Plug-in speakers don't work but laptop speakers do"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-04-29
Hi,

On Hardy Heron, the inbuilt laptop speakers work, but the ones I plug in don't.

Probably something simple. They're logitech speakers.

Could anyone help?

Thanks.

---

### Post by hermes0710 on 2008-04-29
Execute ```
sudo dmesg -c
```

then plug in the speakers and post the results of these commands:

```
sudo dmesg
```
```
sudo lsusb
```

---

### Post by Sealbhach on 2008-05-05
Well, I installed some updates recently and now the headphone output works, so speakers and headphones work, so that's cool.

I'm very happy, thanks for all your help everyone.:)

---

