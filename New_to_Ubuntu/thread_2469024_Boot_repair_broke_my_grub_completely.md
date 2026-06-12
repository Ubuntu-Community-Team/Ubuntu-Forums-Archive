---
title: "Boot repair broke my grub completely"
date: 2021-11-17
forum: New to Ubuntu
---

### Post by HughQugh on 2021-11-17
I have an SSD disk where Xubuntu is installed. 

I also have a magnetic disk that I was using as storage but I had to create a partition and install Windows 7 on it. 

I completely removed the SSD disk during this whole process in order to avoid complications. 

After doing update-grub, grub picked up the Windows installation but it wasn't logging into Windows.

I read in a forum that I should run boot-repair. And that completely ruined everything (I think it moved the boot records to the magnetic disk).

Here is the[ log]("https://paste.ubuntu.com/p/4zy25K6Z4F/").

Basically, when I use my SSD as a boot device now, grub loads but no entry works (the error is grub_register_command_lockdown not found or sth like that). 

When I use my magnetic disk, it gets me into grub recovery console. Weirdly enough, if I go into the Bios and hit save and exit with the magnetic disk as the primary boot device, it works. But when the machine is restarted, I get thrown into the grub recovery console (it says that it can't find a device or something). So basically I need to get into bios and hit save every time in order to get a working grub.

I really have no clue what is going on here. Any help is greatly appreciated.

---

### Post by oldfred on 2021-11-17
Report says grub reinstalled without error?
Are you using LVM? Is it also encrypted? If so you often have to manually mount before running Boot-repair so grub does find LVM partitions.

Report does not show many details it normally does.
With both drives plugged in just run the Summary report, do not run any fixes. And then post link it gives.

---

