---
title: "New to Dual booting , query, where is grub?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by philinux on 2008-05-08
Got ubuntu hardy on disk one. Thought I'd give another distro a go. Pclinux failed to run so did OpenSuse. Anyway installed Mint to empty disk 2. 

It said grub got installed to HD0 but I've got menu.lst on both drives. But the one on disk 2 has the mint and ubuntu boot kernels.

---

### Post by gn2 on 2008-05-08
You're not alone: [http://forum.micromart.co.uk/Topic284882-22-1.aspx](http://forum.micromart.co.uk/Topic284882-22-1.aspx)

The posts from wyliecoyoteuk may explain why it has happened.

---

### Post by philinux on 2008-05-08
Ah, maybe more clarification needed.

The system boots no problem. I can choose mint or ubuntu Hardy.

What I need to know is if I'm on Hardy and there's a kernel update what will happen. If I decide to just use the mint drive, disk2,  as storage and format it will the system boot from disk 1.

(No windows in sight)

---

### Post by gn2 on 2008-05-08
The easy way to find out would be to disconnect the drive2 with Mint on and see if it will boot from drive1.

You *can* have Grub on both drives, if there is a kernel update of the Ubuntu installation on drive1 I think it will update Grub on drive1 because it hasn't been told about the instance of Grub on drive2?

In any event you could re-install Grub from a Live CD or from a SuperGrub CD.

---

### Post by philinux on 2008-05-08
I have a feeling Mint is going to get hosed as it cant see my internet connection. So i might just delete everything on disk two and see what happens.

---

### Post by philinux on 2008-05-08
Mint got hosed - supergrub sorted my ubuntu out.

Mint both gnome and kde failed to recognise my wired connection.
Pity.

---

