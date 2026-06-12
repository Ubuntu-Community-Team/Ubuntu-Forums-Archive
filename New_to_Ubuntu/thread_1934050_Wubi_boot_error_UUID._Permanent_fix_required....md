---
title: "Wubi boot error UUID. Permanent fix required..."
date: 2012-03-01
forum: New to Ubuntu
---

### Post by staticVoid89 on 2012-03-01
Greetings, 

Currently I am running a dual boot via the Wubi installer with Win7 and Ubuntu 11.10. After partitioning my hard drive I started experiencing difficulties booting into my Ubuntu system; however the windows system still remains unaffected and works perfectly. 

Selecting the Ubuntu option(via the windows boot-loader) presents me with my usual series of options, however when it begins to boot the system will halt and output "no such device" followed by an UUID number. After some investigating I found I was able to boot the system by pressing 'e' in the Grub menu and temporarily change the boot parameters to refer to the correct location of the boot image.

As a result the system started correctly and is currently running without a problem. Though my subsequent problem is make these changes permanent. 

After more research I was able to establish Wubi doesn't use Grub and updating the grub.cfg could make the problem worse, therefore I should resolve the issue in Windows; however the file I was referred to doesn't exist in my windows installation? Therefore I've come a little stuck as to how I could make these changes permanent as I don't think updating the grub will help in my situation.

Thank you for your time any help would be greatly appreciated...

Kind regards,

Matt.

P.S. I have also attached the result from a boot script to help provide some relevant information. Also to save any confusion the 'LINUX' partition is the new partition and not the one Ubuntu is currently installed on.  Also my apologies if this has already been resolved.

---

### Post by bcbc on 2012-03-01
Wubi does use grub and grub.cfg. There used to be some big grub/wubi problems but they have been solved for nearly a year).

```
sudo update-grub
```

---

### Post by staticVoid89 on 2012-03-01
Oh really? Brilliant :grin:, that's a relief. So should I just amend the grub-cfg file then run the update, or will the update automatically resolve this?

Kind regards

---

### Post by bcbc on 2012-03-01
Running update-grub will fix it automatically. You *can* edit it but it gets automatically updated e.g. when you update a kernel and this will overwrite any manual changes.

---

### Post by staticVoid89 on 2012-03-01
Excellent, worked perfectly!:D Thank you so much,  I appreciate the help.

Kind regards.

---

