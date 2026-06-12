---
title: "Problem with guest additions in virtualbox"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by ahurd on 2008-10-18
I am using Sun xVM with Kubuntu 8.04 linux host and win2000 guest. When I click on Install Guest Additions under Devices, nothing happens. What am I missing and what should I do?

---

### Post by stephanvaningen on 2008-10-18
The only thing Virtual Box does then is 'mounting' an .iso with installation-programs for the guest-additions. If your windows is set not to automatically run CD-ROM's AUTORUN.INF, then nothing will happen.
After clicking 'Install Guest Additions', go to your CD-ROM in Windoze and look for the WindowsGuestAdditions.exe (<- exact name I don't remember anymore :-/)
==> Is this what you were looking for?

---

