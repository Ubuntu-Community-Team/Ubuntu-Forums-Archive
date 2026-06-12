---
title: "Intall hangs on Format Swap space"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by JeremyR on 2008-07-22
I have tried to install Ubuntu Desktop on my laptop to duel boot with WinXP.  I started the installer in windows, rebooted and continued until it hung up on the part that says it formatting swap space (or swap partition). I let it sit for maybe an hour last night and it never finished.

Any ideas on why it's doing this?

---

### Post by hyper_ch on 2008-07-22
you try to manually encrypt swap upon installation?

---

### Post by JeremyR on 2008-07-22
This was my first attempt at installing it.  I'm not sure how i'd manually encrypt the swap like you are asking.

I've since done a clean install on a separate box with no problems.

---

### Post by hyper_ch on 2008-07-22
well, did it freeze when you tried to manually encrypt swap?

---

### Post by JeremyR on 2008-07-22
I dont know how to manually do anything yet.  this was just in the installer process.

Would doing that part manually fix it?

---

### Post by hyper_ch on 2008-07-22
well, it is a known bug that it hangs upon manually assinging a random key for swap encryption. Hence my questions. Besides that, it should not hang. Did you check the cd for defects?

---

### Post by JeremyR on 2008-07-22
I started the installer from a mounted ISO inside WinXP then it rebooted me to the installer. Should I try again by booting to the a CD?

---

### Post by hyper_ch on 2008-07-22
run it from inside XP? Is that possible at all?

Boot from the cd.

---

### Post by JeremyR on 2008-07-22
Yes, it copies the necessary files to the HD and configures the boot menu to give you the option of windows or ubuntu.

After it does that, it asks you to reboot and at the boot menu if you select ubuntu it will continue the installer.

---

### Post by hyper_ch on 2008-07-22
oh, that's how the wubi installer works... I'd rather suggest to do a real install ;)

can't help you much with wubi... I try to avoid is as much as possible ;)

---

### Post by JeremyR on 2008-07-22
ha ha okay, i'll give it a whirl and see if I can't get it to work.

---

### Post by hyper_ch on 2008-07-22
just two things:

(1) you need to partition so defrag windows 2-3 times

(2) upon installtion - especially the partitioning part - just don't press "ok", "ok", "ok"... have a read ;)

---

### Post by mandelbro on 2009-03-05
I have had the same problem...both with ubuntu and kubuntu
after I converted my fat32 fs to ntfs
because with fat32 the kernel cannot update

---

