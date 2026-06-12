---
title: "Installation problem"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by Steelmesh on 2012-02-19
What happens is; my computer loads bios like normal, begins to boot from CD, goes  through the whole Ubuntu 5 dot loading thing with both CD and HD lights flashing,  then it changes to the Ubuntu background (purplish), having few tiny icons in  upper right, and in the middle is a loading animation with dots that  spin around, after 3 seconds it freezes forever. Then I started hitting ESC right when it started booting from the CD, then started playing with settings like noaipc and nomodeset...

I tried two different Ubuntu CDs using two different programs using a md5 checksum verified iso file to burn the CDs.  Versions used 11.10 and 10.04.4

So the install CDs should be ok.

My hardware:
DFI NF4X mobo
AMD socket 754 processor
[Two new SATA Hitachi 500GB hard drives]("http://www.microcenter.com/single_product_results.phtml?product_id=0349595"), planning on Raid 1 server with this system
[New SATA CD drive ]("http://www.microcenter.com/single_product_results.phtml?product_id=0372836")bought today

I tried it:

- with Raid 1 on, arrayed in NVRAID bios
google searching
- with no Raid enabled
google seaching
- with no Raid and APIC disabled bios
google searching
- with one HD plugged in, APIC enabled,
google searching
- with one HD plugged in, APIC disabled bios, (and tried new disc 10.04.4)
google searching
- with one HD plugged in, APIC disabled bios, acpi=off, checked noapic, checked nomodeset
-  checked disk for defects first / memtest ok, then with one HD plugged  in, APIC disabled bios, acpi=off, checked noapic, checked nomodeset

Keeps freezing seconds after the purple background shows.

---

### Post by tcofer on 2012-02-20
If you're planning to use it as a server then you might want to install Ubuntu server edition: [http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download) i would recommend 10.04 LTS, it is the most stable of the two releases. Also Ubuntu server edition is text based, if that proves to be too daunting, you can install the classic gnome desktop by passing this commands: 

# sudo apt-get update
# sudo apt-get install gnome-desktop

Hope this helps, good luck.

---

### Post by Steelmesh on 2012-02-20
> **tcofer said:**
> If you're planning to use it as a server then you might want to install Ubuntu server edition: [http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download) i would recommend 10.04 LTS, it is the most stable of the two releases. Also Ubuntu server edition is text based, if that proves to be too daunting, you can install the classic gnome desktop by passing this commands: 

# sudo apt-get update
# sudo apt-get install gnome-desktop

Hope this helps, good luck.

Thanks for finding this post tcofer!!  It looks like Server 11 install is working fine, got to the part where its setting up the disks for partitioning. It even used some [TP-Link TL-WN851ND wireless PCI card]("http://www.microcenter.com/single_product_results.phtml?product_id=0376778"), (recommended by google for ubuntu). I shut down the system at that point to plug both of my drives in for this RAID setup and to finish downloading server 10.04.

I may need the GUI, this is my first working with linux.  Also my first server too.  I learn best by doing, so here I am.


I hope to bring this server into work (50 mbps up/down) and use it to host websites, ftp server action, backup etc.  11 years with godaddy, I didn't pay the bill for less than 10 days overdue, they still formatted all my files.  I'm waiting to celebrate the day those rat bastards drive the company off a cliff.

---

