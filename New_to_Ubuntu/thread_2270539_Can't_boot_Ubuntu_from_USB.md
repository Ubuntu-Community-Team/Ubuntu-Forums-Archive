---
title: "Can't boot Ubuntu from USB"
date: 2015-03-23
forum: New to Ubuntu
---

### Post by Mike_Hill on 2015-03-23
Hi folks,

- I've verified my USB and all seems good.
- My laptop is set to legacy boot with 'boot from USB' as the #1 boot option.

The laptop contains a corrupt Ubuntu install (I did silly things) and I need to reinstall, however, the machines always tries to boot from the hard drive, even if I interrupt the boot sequence and select the USB option. Because the current install has issues it gets to the login screen and dies. I really need to make the USB boot work.

Can anyone help?

Many thanks
Mike

---

### Post by Rex Bouwense on 2015-03-23
Hey Mike.  Check the hard drive in the BIOS.  Your laptop may be recognizing the flash drive as another hard drive.  If that is the case merely move it ahead of the real hard drive, save and exit.

---

### Post by Mike_Hill on 2015-03-23
Thanks very much Rex, I'll try that tonight and check back in.

Mike

---

### Post by Mike_Hill on 2015-03-24
Rex I'm pretty sure the computer was recognising and ignoring the USB. The good news (GREAT) is that I found my original install disk and that worked perfectly.

I shall explore USBs at my leisure now the "aarrgh, no computer" phase has passed.

Thanks
Mike

---

### Post by Bucky Ball on 2015-03-24
Good news. Please mark as solved (see the second link in my signature) and post a new thread with a descriptive title for any further problems. Good luck.

---

### Post by Rex Bouwense on 2015-03-24
> **Mike_Hill said:**
> Rex I'm pretty sure the computer was recognising and ignoring the USB. The good news (GREAT) is that I found my original install disk and that worked perfectly.
Well that may be correct but there are some computers (like mine) that recognizes the flash drive as another hard drive.  Great news about your success.

---

### Post by ptn107 on 2015-03-24
I've seen the greatest success booting the usb only after I started to use *ddrescue* to write disk images.  Unetbootin, startup disk creator, and the like have all had problems booting even though they formatted the usb correctly.

```
ddrescue -d -D --force ubuntu-14.04.2-desktop-amd64.iso /dev/sdx
```

Replacing *ubuntu-14.04.2-desktop-amd64.iso* with your image of choice and replacing */dev/sdx* with your usb drive.

*ddrescue* is available from the *gddrescue* package.

---

