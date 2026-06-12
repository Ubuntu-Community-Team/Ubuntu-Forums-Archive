---
title: "Grub hanging at Error 22 - Relp!!!"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-05-08
I wanted to reinstall Hardy in my dual-boot with Vista &#8211; I had messed it up by removing essential packages.  So I went into Vista, cleared the Hardy part of the disk and then removed the partition. When I re-booted, I expected a plain Vista reboot, I did not expect Grub to still be in charge.

Anyway, it&#8217;s hanging now at Stage 1.5, Error 22.

I&#8217;ve ordered System Recovery CD in the post. **_I can&#8217;t download ISOs or burn CDs._** Ideally I&#8217;d have liked to get Supergrub sent in the post, but can't find a vendor for it.

I don't have a Vista Recovery disk either.

I saw here

[http://www.neowin.net/forum/lofiversion/index.php/t405091.html](http://www.neowin.net/forum/lofiversion/index.php/t405091.html)

that repartitioning with GPart (using System Recovery CD) and reinstalling Hardy Heron will fix it.

Any thoughts anyone?

 I want to keep my Vista as I have Blu-Ray on my laptop.

Thanks in advance.



.

---

### Post by sy88 on 2008-05-08
Reinstalling Hardy should fix your problem, yes.

---

### Post by Sealbhach on 2008-05-08
Thanks. I was hoping it might, but because Grub is now the Boot Manager I thought perhaps the installation disk might not detect the presence of Vista and write over it. If that makes sense?

If I got a second opinion I'd feel a little bit more assured. :-k



.

---

### Post by kirios on 2008-05-08
sy88 is right. 

Make sure you reinstall to the free space. 
 
> **Sealbhach said:**
> Thanks. I was hoping it might, but because Grub is now the Boot Manager I thought perhaps the installation disk might not detect the presence of Vista and write over it. If that makes sense?

If I got a second opinion I'd feel a little bit more assured. :-k



.

---

### Post by Sealbhach on 2008-05-09
Sorry to be a bit difficult, can you just confirm?

Do you mean I choose the option:

**Use maximum free space.**


Scares me a little to see my lovely Vaio unable to boot up, so just want to get it right.


.

---

### Post by ironclaw on 2008-05-09
Yes, 'Use maximum free space' should be fine.

The reason for the GRUB error is because GRUB was written to the master boot record and overwrote the Windows one. It is trying to load the next stage of GRUB, which should be located in the Hardy partition, which you deleted :).

Reinstalling Hardy on the maximum free space would also install GRUB again, and it should automatically detect all your other operating systems fine.

So just install Hardy like the last time you installed it, and it should be fine.

---

### Post by Sealbhach on 2008-05-09
Wonderful, thank you all!!



.

---

