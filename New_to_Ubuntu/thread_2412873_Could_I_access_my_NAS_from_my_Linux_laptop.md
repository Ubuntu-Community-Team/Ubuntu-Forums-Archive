---
title: "Could I access my NAS from my Linux laptop"
date: 2019-02-18
forum: New to Ubuntu
---

### Post by Odense on 2019-02-18
I am running the latest Ubuntu LTS version on my cheap Lenovo laptop.

I am considering buying a Zyxel NAS326 - but I would want to be able to access it also from the laptop.

Would that be possible even though Zyxel does not supply or support any Linux software?

Can it be done relatively easy or should I just accept that I need to use Windows or Android clients to use the NAS drive?

---

### Post by Holger_Gehrke on 2019-02-18
Take a close look at the technical data of the [Zyxel NAS326]("https://www.zyxel.com/de/de/products_services/nas326.shtml?t=p#productDetailTab4"). It supports NFS and CIFS for file sharing and has FTP and web-dav. All of these can be accessed through Ubuntu. Additionally it uses EXT4 for it's internal HDD format, so I think it's probably itself running some kind of Linux.

Holger

---

### Post by Odense on 2019-02-19
Thank you for the quick reply Holger_Gehrke,

I might not have been clear in my question - but by relatively easy I do not mean I need to make my own Linux apps or similar.

I was hoping there was some ready made apps that could be used - perhaps with a LITTLE BIT of modifications.

I want to be able to use the NAS drive as any other drive - in the same way the network drive works in the office. I guess FTP access would be tolerable but it would NOT be as good for me as "normal" access.

Does my Ubuntu Linux have the option of using the Zyxel NAS as a "normal" drive?

---

### Post by CatKiller on 2019-02-19
I suspect you misunderstand the answer. 

> **Odense said:**
> Does my Ubuntu Linux have the option of using the Zyxel NAS as a "normal" drive?

Linux doesn't have drives. Linux has a unified filesystem tree. You mount a filesystem, which might be on a partition of a hard drive, or a USB device, or some other machine somewhere accessed over the network, or whatever other method one might think of, to a point in the filesystem tree.

If your NAS exposes the files as NFS, that's probably the easiest, but other ways will work fine too, as you've been told already. You can have it automatically mounted at boot by editing /etc/fstab, or mount it only when you need to. It's up to you.

---

