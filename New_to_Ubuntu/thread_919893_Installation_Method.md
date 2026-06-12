---
title: "Installation Method"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by cantlin on 2008-09-14
Hiya. I am terribly new. I need to install Ubuntu on a tiny laptop I recently acquired. It has no CD or floppy drive - though I do have an external USB CD drive which I can access but not boot from - and no internet connectivity. The machine is currently running a Kubuntu distribution that I would like to replace.

Is [InstallationFromLinux](https://help.ubuntu.com/community/Installation/FromLinux) the best method? If so, could someone recommend a way of doing it without gpacked (which I can find no trace of), or provide an idiot-proof explanation of how to get gpacked up and working on there? I'd be very grateful for any insights you can offer.

---

### Post by doctorbighands on 2008-09-14
Would [this]("https://help.ubuntu.com/community/Installation/FromUSBStick") be an option for you?

I've never attempted an installation from within Linux, so I can't comment on that.

---

### Post by Gannon8 on 2008-09-14
If you cannot boot from a USB CD drive I doubt you can boot from a USB Hard drive/stick. Try a network install.

---

### Post by doctorbighands on 2008-09-14
Could booting from USB simply be a matter of changing settings in BIOS? Something to check, anyway.

Information on a network install: [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by cantlin on 2008-09-14
> **doctorbighands said:**
> Would [this]("https://help.ubuntu.com/community/Installation/FromUSBStick") be an option for you?

Possible. Little cynical about the chances of it working (considering USB CD drive doesn't), but it might be my only option.

> **Gannon8]Try a network install.[/quote]

No ethernet either!  said:**
> Could booting from USB simply be a matter of changing settings in BIOS?

Boot order looks right. Anything I should check besides that?

---

### Post by halitech on 2008-09-14
only other option I can think of is to put the drive in a laptop with a working cdrom or internet connection and install it on there then move it back to the original laptop

---

### Post by doctorbighands on 2008-09-14
> **cantlin said:**
> Boot order looks right. Anything I should check besides that?

It isn't necessarily a matter of the boot order (although that makes a difference, of course). With some BIOS, you have to hunt through and enable an option along the lines of "allow boot from USB device." Depending on the age and complexity of your BIOS, you may or may not have this option.

---

