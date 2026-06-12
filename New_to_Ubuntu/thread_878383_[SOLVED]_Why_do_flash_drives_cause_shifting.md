---
title: "[SOLVED] Why do flash drives cause shifting?"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by IanVonSpeedfreak on 2008-08-02
I really don't understand what is going on here. I mean, I understand that my drives are being re-mounted each time I restart my computer, but why aren't the mount points static? I guess there's probably a way to edit the /etc/fstab file to do this, but why isn't this particular drive static by default? While it seems kinda minor, I am a little put off by the fact that my primary HD is being listed as sda instead of hda right now, and I'm not too thrilled that my swap partition may get effed up again in the near future because the drive keeps shifting and fstab can't keep up.

Also, I'm having trouble mounting my external floppy drive.  I got it working one time before, but I think I had to create a /dev/ entry for it.  In any case fd0 is gone now and there isn't any other fd entry, and I can't remember how to create a new one.  If there is any other solution I'm missing, please tell me.

Help on either of these issues would be greatly appreciated,
IVS

---

### Post by JillSwift on 2008-08-02
Right-click on the drive icon, then select "properties".
Go to the "mounting" tab and give it a specific mount point, plus any other options you need or like.

---

### Post by northern lights on 2008-08-02
> **IanVonSpeedfreak said:**
> I am a little put off by the fact that my primary HD is being listed as sda instead of hda right nowSince Feisty, all hdds are handled by 'libata' and as such mounted as sdx.

---

### Post by IanVonSpeedfreak on 2008-08-02
Damn, so obvious.

Thank you so very much for your help.

---

### Post by IanVonSpeedfreak on 2008-08-02
> **northern lights said:**
> Since Feisty, all hdds are handled by 'libata' and as such mounted as sdx.

That's a little odd, I don't think mine was mounted like that before today, and isn't that a little confusing?

In any case, I do appreciate your insight.

---

### Post by IanVonSpeedfreak on 2008-08-03
Okay, it now appears as if my computer will only allow one flash drive to be mounted at a time.  Also my external floppy mounts, but only when I insert the disk I made earlier.  I tried formatting another floppy to see if that would work, but I can't even seem to do that.

EDIT: [COLOR="Blue"]Solved problem no.1 by installing usbmount, solved problem no.2 by trying yet another floppy that worked (the one I was using must've been effed).  Thanks again to all who helped.[/COLOR]

---

