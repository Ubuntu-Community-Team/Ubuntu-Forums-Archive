---
title: "[SOLVED] mount permission drive"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by king leoric on 2008-07-17
A newly installed ubuntu required password input when mounting internal drive (e.g. windows partion, or other linux partition.) Just observe that yesterday, mount ubuntu doesnt ask anymore password. And I can't remember if I tick the remember password or not.

How can I put back that password requirement again. It would be nice so no other people can access my other partition.

Thank you very much in advance

---

### Post by iaculallad on 2008-07-17
> **king leoric said:**
> A newly installed ubuntu required password input when mounting internal drive (e.g. windows partion, or other linux partition.) Just observe that yesterday, mount ubuntu doesnt ask anymore password. And I can't remember if I tick the remember password or not.

How can I put back that password requirement again. It would be nice so no other people can access my other partition.

Thank you very much in advance

What about removing those drives you want protected from your /etc/fstab file so that it will not automount on startup?

---

### Post by king leoric on 2008-07-17
I'm not so familiar with my fstab and I have never touch the fstab file as far as I can remember. The drives I'm saying is not automounted automatically. I have edited nautilus before for automounting external drives using gconf-editor but It doesnt affect the one I am stating now.

---

### Post by mc4man on 2008-07-17
If you d. clicked on an internal drive icon (not auto mounted, not ntfs) you would have been prompted as to whether you wanted to grant _yourself_ 'Explicit Authorization to mount file systems from internal drives'. (actually a very useful new feature) It won't extend to other users. (unless you want)
look in system -> admin -> Authorizations -> storage and you'll see if you did

---

### Post by samrat1985 on 2008-07-17
Does this 'password not required'  works only for mounting or have you
manually specified it at sudoers file? & which version of ubuntu arte you using?

---

### Post by samrat1985 on 2008-07-17
ah forget it "mc4man" aanswer should work fine

---

### Post by king leoric on 2008-07-17
> **mc4man said:**
> If you d. clicked on an internal drive icon (not auto mounted, not ntfs) you would have been prompted as to whether you wanted to grant _yourself_ 'Explicit Authorization to mount internal drives'. (actually a very useful new feature) It won't extend to other users. (unless you want)
look in system -> admin -> Authorizations -> storage and you'll see

not so familiar with the autorizations but I will take a look now.

@samrat- i'm using hardy 8.04

---

### Post by king leoric on 2008-07-17
for additional, this is what I am talking about. This window authentication when I'm mounting drives

---

### Post by king leoric on 2008-07-17
Thanks mc4man and also others. I have solved under autorizations, editing on the storage...many thanks guys

---

### Post by mc4man on 2008-07-17
That's it, I reasonably sure it only extends to you, there is also a means to block users IIRC (on win box atm)
The first one is also useful for those rare times when a filesystem is mounted by root (when you have an unmounted usb flash drive and run gksudo nautilus is one I'm aware of)

---

