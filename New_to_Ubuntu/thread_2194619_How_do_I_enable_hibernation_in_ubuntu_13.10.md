---
title: "How do I enable hibernation in ubuntu 13.10"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by wpbdry on 2013-12-19
Hi All,

I am new to ubuntu and I recently installed ubuntu 13.10 on my Dell inspirion laptop alongside the already installed Windows 8.1 64-bit.

I do not know how to hibernate ubuntu so that I can reboot into windows and come back to ubuntu and carry on where I left off. Hibernation works fine in windows (I don't know if the two are linked). When I click on the power icon in the top right corner of the screen it only lists "Logout..., Suspend, Restart...., Shut Down...." Having both Restart and Shut Down is pointless because they both bring up a choice to either restart or shut down. So I want it to say "Logout..., Suspend, Hibernate..., Shut Down. Is this possible?

I have searched the web and found the same answer to this problem on many different forums:
Open a terminal and type
```
[FONT=Ubuntu Mono]sudo gedit /var/lib/polkit-1/localauthority/50-local.d/hibernate.pkla[/FONT]
```
Update the file to
```
[FONT=Ubuntu Mono][Re-enable Hibernate]
[/FONT]Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
[FONT=Ubuntu Mono]ResultActive=yes[/FONT]
```
Reboot system

I did that but it didn't work. I have no idea why.

I understand that hibernation uses the swap space and that if ubuntu is not mounting the swap 'drive' at boot it could cause problems. So I opened **/etc/fstab **and checked that there is a line
```
[FONT=Ubuntu Mono]UUID=code none            swap    sw              0       0[/FONT]
```
where code is the UUID code of my swap partition.

If anyone has any other ideas I would be very grateful!

Thanks.

---

### Post by philinux on 2013-12-19
That .pkla file needs a bit more info according to this.

[http://askubuntu.com/questions/361734/hibernation-is-still-missing-from-menu-in-13-10-after-enabling-via-polkit-how-t](http://askubuntu.com/questions/361734/hibernation-is-still-missing-from-menu-in-13-10-after-enabling-via-polkit-how-t)

---

### Post by wpbdry on 2013-12-19
Great, thanks! That worked perfectly.

---

### Post by philinux on 2013-12-19
Glad that worked. Please mark as solved using the Thread Tools drop down menu.

---

### Post by Resistent on 2013-12-19
I don't use hybernation and now I have an SSD harddisk.
So I think I will not use hybernation. That would mean more writing on the harddisk. Right?

---

### Post by ceciliasp on 2013-12-20
HI, tried another way to hibernate and totally screwed my dual boot system (I believe Windows 8 had a lot to do with it).
Now I see there is this option.
My pm-hibernate worked, though I took  while for the system to become alive again...My swap partition is 3.89 Gb and my RAM is 4 GB. Should I re-size my swap partition?
Is this a "safe" procedure? (I ended up wiping my disc and started all over with 13.10 and ):P Windows 8 that was a pain in the back anyway)

Thanks

---

### Post by Randall_Quinn on 2014-03-10
I have tried both of the methods on this page, however the hibernate option doesn't appear consistently. It appears in the power options in the top right corner at logon, but not once I am logged in, rendering it effectively useless! Could anyone shed some light on this?

---

