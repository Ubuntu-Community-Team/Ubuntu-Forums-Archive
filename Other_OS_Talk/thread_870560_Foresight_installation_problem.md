---
title: "Foresight installation problem"
date: 2008-07-25
forum: Other OS Talk
---

### Post by guber112 on 2008-07-25
I wanted to know if anyone else beside me that had a problem with Foresight. When I installed Foresight, my window xp partition wouldn't load. I tried installing it with both Grub and foresight bootloader. But it seems that Foresight corrupt my xp boot.ini.

---

### Post by melrom on 2008-08-05
please tell me the contents of

```

sudo vim /etc/bootman.conf

```

and

```

sudo vim /boot/extlinux/extlinux.conf

```

You can use gedit if you do not prefer vim.

Nevermind. I can see from the foresight forums that you are using grub and are being assisted there.

---

