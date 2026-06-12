---
title: "Alternate CD does not auto run"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by pardesi on 2008-04-25
hi i downloaded an alternate .iso cd via bittorrent...after writing it to the disc when i insert it does not auto run ...what do i do?

---

### Post by kamitsukai on 2008-04-25
1st question is your computer set to boot your cd/dvd drive first?
2nd question how did you burn the iso image to the disc? did you do it the proper way or did you just drag and drop like a data cd?

---

### Post by pardesi on 2008-04-25
yes it is set to boot the cd first but i didn't restart after i finished just inserted the cd first the pop up cam and then i chose the option to upgrade but sadly my net connection failed and i had to cancel the upgrade...so it said setting thing to original

as for ur second question i  rightclicked on the .iso image and clicked on write to disc..

---

### Post by Saya on 2008-04-25
> **pardesi said:**
> as for ur second question i  rightclicked on the .iso image and clicked on write to disc..
In what operating system? It might've burned it as a data CD automagically.

---

### Post by kpkeerthi on 2008-04-25
Make sure you burn at a speed not higher than 4x.

---

### Post by zvacet on 2008-04-25
@ **pardesi**


> yes it is set to boot the cd first but i didn't restart after i finished just inserted the cd first the pop up cam and then i chose the option to upgrade but sadly my net

Check if you still have Gutsy installed.No need to boot from CD if you want to upgrade.

> Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet. 

Download and burn the alternate installation CD. 

Insert it into your CD-ROM drive. 

A dialog will be displayed offering you the opportunity to upgrade using that CD. 

Follow the on-screen instructions. 

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 
gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2: 
kdesu "sh /cdrom/cdromupgrade"

---

