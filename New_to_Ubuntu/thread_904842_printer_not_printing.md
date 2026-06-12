---
title: "printer not printing"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by gotanothergrot on 2008-08-29
Ive downloaded ubuntu yesterday (new to Linux) so giving it a try for the first time, however i cant get my hp 1020 printing.

The system automatically found the hardware and now has a few test pages to print but nothing happening with the printer so any advice would be great..

---

### Post by spiderbatdad on 2008-08-29
Not familiar with this specific printer, however if you enter```
localhost:631
```into the address bar of your browser, that will take you to the printer driver configuration page. From there you can try to select another driver or configure your printer, or find more information on available drivers.

---

### Post by gotanothergrot on 2008-08-29
Hewlett packard lazerjet 1020 to be precis.

Im running ubuntu alongside windows xp, the printer has always worked fine on the other op.

---

### Post by hansdown on 2008-08-29
Hi gotanothergrot.

I hope this helps. [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)

---

### Post by Sef on 2008-08-29
> The system automatically found the hardware and now has a few test pages to print but nothing happening with the printer so any advice would be great..

It should  work out of the box (ootb.)  Since it is not, download from Add/Remove HPLIP.  (Applications > Add/Remove > Search: HPLIP > click on the box next to HPLIP > apply changes > apply > close.  There is a diagnostic tools on it.  See if one of them can detect your problem.

---

### Post by gotanothergrot on 2008-08-30
> **Sef said:**
> It should  work out of the box (ootb.)  Since it is not, download from Add/Remove HPLIP.  (Applications > Add/Remove > Search: HPLIP > click on the box next to HPLIP > apply changes > apply > close. 

I followed the above, cheers for that.

However i now have 14 test print jobs, is there any way i can clear everything and start over? as i feel im clogging things up.

---

### Post by gotanothergrot on 2008-08-30
> **hansdown said:**
> Hi gotanothergrot.

I hope this helps. [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)



On the link handsdown provided there is a warning, here 


[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) 

 saying

 * DON'T USE the foo2zjs package from:
     	Ubuntu, 

This is what i might have already done. If so i think i might have to start over.

---

### Post by gotanothergrot on 2008-08-30
Also, why cant i just use the installation cd that came with my printer to get thing running?

---

### Post by Rhubarb on 2008-08-30
I have had some brief experience with a similar model consumer hp laser printer.
The problem is that the printer when turned on is as functional as a brick (it's useless).
To make the printer know that it's a printer, it's firmware (or brains) must be uploaded to it, before it can do any printing.

Unfortunately I can't quite remember how exactly I had solved the problem.
I read up on a lot of foo* open source printing engines, and had installed the newest hplip software.
When it works, you should see a line indicating that firmware has been uploaded to the printer in your system logs (when you turn the printer on).

I'm sorry I can't give you much more assistance, as it took me 2 hours to get it working, and my approach to get it working wasn't very methodical.
I also don't have that printer here myself to help figure it out properly for you.

---

