---
title: "USB will not mount"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by seattle vic on 2008-05-24
Under Gutsy, I'd plug in my usb memory card and it would pop right up as I recall.  Under Hardy, it appears in Places/Kingston, but clicking on it will not mount the device.

Do I need to mount it manually?  If so, what device would I reference using the sudo mount command?

---

### Post by saj0577 on 2008-05-24
Right click/ Mount.

Should work.

Saj

---

### Post by seattle vic on 2008-05-25
> **saj0577 said:**
> Right click/ Mount.

Should work.

Saj

Thanks for the reply.

If you mean pull down the "places" menu and right click on the entry for "kinston" (the name of the memory card that it has identified), that does not work.  It treats it the same as a left click and does nothing.

I will add that I'm running virtual box, and although usb on both of my clients are disabled, they have been enabled in the recent past.

Vic

---

### Post by sayakb on 2008-05-25
Mount it manually via CLI:
```
sudo mkdir /media/disk1
sudo mount -t /dev/sdc1 /media/disk1
```

Replace /dev/sdc1 with whichever applicable for you.

---

