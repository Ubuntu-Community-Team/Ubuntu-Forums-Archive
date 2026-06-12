---
title: "I get &lt;initramfs&gt; window. Please help"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by prasaanth on 2008-07-09
I have the following problem.
 
I'm new to ubuntu and last week i bought a SATA harddisk of 250 gb in addition to my existing 80Gb harddisk for the same computer to use ubuntu in the new hdd. After fixing it, when i tried to boot from the cd it opens a <initramfs> prompt window and doesnt boot. My harddisk has been detected and was found healthy. I use windows xp in the 80gb harddisk and previously without the new harddisk the linux cd booted and i was able to run it.

Please help me.

Thanks in advance

---

### Post by OffAxis on 2008-07-09
> After fixing it
What do you mean by this?

Are you using the ubuntu drive as the primary drive?
Have you configured grub?
Were both drives attached when you installed ubuntu?

---

### Post by avtolle on 2008-07-09
[https://help.ubuntu.com/community/BootOptions#When%20installing](https://help.ubuntu.com/community/BootOptions#When%20installing) for help in adding a boot option. I'm going to suggest you try one not mentioned there, which is all_generic_ide first (it is added to the boot string as shown for another option in the example). Good luck.

---

### Post by prasaanth on 2008-07-10
Yes Offaxis

I use windows as my primary drive and i had both the harddrives connected when i tried installing ubuntu. I havent installed Grub--to be frank i duno what grub is... 'After fixing this' actually meant that after having installed my second harddisk when i tried booting linux from the cd it went to the <initramfs> window.. Please help

thanks

---

