---
title: "Swapon on startup"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by sayakb on 2008-04-25
Hello all
I am using Gutsy amd64
I have a 4GB swap partition. I once deleted it and formatted it to ext3. I again formatted it to linux-swap format, but the swap is not automatically made active when the system boots . How to make it active on boot? (the partition is /dev/sda1)

---

### Post by sdennie on 2008-04-25
I think if you add this to /etc/fstab, it will automount the swap at boot time:

```

/dev/sda1 none swap sw 0 0

```

---

