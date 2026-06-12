---
title: "BootSector (How can I boot up to a windows installation)"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by johnhouk on 2008-11-13
I  do have a bootable disc, just no way to boot from it. My laptops Hard Drive AND Floppy drive are no good. my bios dosn't support the usb port, but does have a network boot option.

I couln't get a windows installation going because the "FreeDOS" behind the "OSdeploy" software i was using would fail in the manipulation of it all* But I could get an ubuntu installation to go. ...PXE over TFTP and all.

ANYWAY now i'm here and i'm still looking for windows options.

What I want to know if is there a way to copy the files inplace to where windows setup is run on the next boot!

Thataway I could either follow the dual boot [instructions]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=4") or reinstall windows alltogeather.

I'll try and see if wine will allow me to run the setup.exe (win32 app). 
If not ill have to adapt to this kernel and virtualize the rest.


*It hits an an error conserning the himem or memdisc or something, I forget what it was exactly.

---

### Post by Kellemora on 2008-11-13
Hi JH

I'm not exactly understanding what your problem technically is here?

By no good, do you mean they are just not working or that they are broken?

Does your bios allow you to boot from a CD at all?

If so, use the GParted disk and install Ubuntu to get the bootloader (called GRUB) into the MBR, it should find your Windows installation and then you could boot into it.

TTUL
Gary

---

### Post by johnhouk on 2008-11-13
there broken.
there is no windows on this hard drive
ive got a usb drive and the oem disc, and others if needed.

---

### Post by johnhouk on 2008-11-13
The windows installation runs under wine but fails at inspecting current configuration. Then if i alt tab over theres a window that says its faild, has to close, and may be remedied by doing a dynamic update? I imagine there talking about the dl of updated install files not an update so dynamic it covers this. Well I'll watch for replies as I install that virtual application.

---

