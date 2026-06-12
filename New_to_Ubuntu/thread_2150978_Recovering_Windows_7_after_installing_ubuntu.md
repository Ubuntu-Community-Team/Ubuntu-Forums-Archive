---
title: "Recovering Windows 7 after installing ubuntu"
date: 2013-06-03
forum: New to Ubuntu
---

### Post by Sagar thakkar on 2013-06-03
Hello All,
Recently I installed ubuntu 12.04LTS on my 24GB SSD,After installing ubuntu I can not boot to the windows 7
Installed on one of the partition of  my regular 750GB HDD.I can see the windows installation files in the partition.
please help me out.


my laptop is  
Asus s46M ultrabook 
core i5  
nvidia geforce 635M 2GB 
750 HDD 
24 SSD 
optical drive  
3 USB ports (3.0)

Thanks in Advance.

---

### Post by Bucky Ball on 2013-06-03
Are you getting a list of kernels and Windows at boot? If not then try hitting the shift key directly after the BIOS screen at boot. That should get you to a list and Windows is probably already on that.If no joy, try this:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Or, when in Ubuntu, open a terminal and issue:

```
sudo update-grub
```

Keep an eye out and you should see the Win install added. Reboot.

---

### Post by MidnightGrey on 2013-06-03
Hi there.

We could use a bit more information, when you say you can see your Windows Installation files in a partition, did you mean you can see your Windows C-Drive? (ie: the common folders, Program Files, Windows, Users etc).
While i have no experience with the ASUS ultrabook, I am concerned because when laptops come with SSDs, they tend to install Windows in the solid-state drive (so windows loads faster).

I've attached a screenshot of my Windows Partition mounted in ubuntu. Does your partition look something like mine?

---

### Post by Mark Phelps on 2013-06-03
When you installed Ubuntu, it likely put GRUB  into the MBR so that Windows doesn't boot automatically anymore.  The terminal command that Bucky Ball mentioned will regenerate the GRUB config file to add an entry for Windows.  Then, when you reboot, you should see a GRUB menu.

---

