---
title: "USB/Firewire"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by ghyelde on 2008-09-19
i have read the documentation and am still confused.  Portable running XP - is installing ubuntu to a firewire or usb hard drive straight forward or is it a problem?

---

### Post by compiledkernel on 2008-09-19
Are you wanting to install Ubuntu to a portable drive so that you can then subsequently boot from that portable drive? 

If so, yes its fairly straight forward.

---

### Post by elmoosecapitan on 2008-09-19
In stead of choosing your C: drive as your main drive you will choose your E: drive, or whatever port represents your usb drive.

cheers

---

### Post by Harisz750 on 2008-09-19
ok.. but what about grub? where should it be loaded? in c drive or in usb? then.. is the usb drive needed to be plugged in when system boots or it can boot in XP without any errors?

---

### Post by compiledkernel on 2008-09-19
When booting from a USB device, Grub (as far as I know at least) doesnt even play a role. 

So yes, you should be able to boot without any relative issue.

---

### Post by timcredible on 2008-09-19
> **compiledkernel said:**
> When booting from a USB device, Grub (as far as I know at least) doesnt even play a role. 

you always have grub, or you can't boot (it's not just for dual-booting). if you're booting from a usb drive, make sure you install grub on that drive.  ubuntukids.org has a tutorial for doing this - you have to tell the installer to install grub on disk 1 (or something like that, i forget).  then you have to go into that disk and change the /boot/grub/menu.lst file to point to the usb drive to boot from also.  and of course, you have to tell the pc to boot from usb when it powers on.  i ran a desktop off a usb drive like this for a while, it worked fine.

---

