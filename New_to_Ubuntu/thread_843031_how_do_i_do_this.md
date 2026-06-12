---
title: "how do i do this?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by T2manner on 2008-06-27
i was wondering if i could download some driver files and put them on a flashdrive. then, on another os, use the files to install the driver.

---

### Post by defrex on 2008-06-27
Drivers are OS-specific.

---

### Post by st33med on 2008-06-27
If you mean downloading the driver files from Ubuntu and installing on Windows via USB, then yes. Just make sure you have the correct PC module.

---

### Post by luisito on 2008-06-27
I don't think you can do what you are trying to do.

---

### Post by T2manner on 2008-06-27
what i'm trying to do is download the driver files for my wireless internet driver and use the files to install the driver on Open Solaris or OpenSuse

---

### Post by st33med on 2008-06-27
> **T2manner said:**
> what i'm trying to do is download the driver files for my wireless internet driver and use the files to install the driver on Open Solaris or OpenSuse

Yes, it should work.

---

### Post by T2manner on 2008-06-27
okay.. so how do i do it?

---

### Post by wdaniels on 2008-06-27
> **T2manner said:**
> what i'm trying to do is download the driver files for my wireless internet driver and use the files to install the driver on Open Solaris or OpenSuse

The driver files are usually just source code like normal text files - there's nothing special about them that you need to consider for copying them to another machine so long as you don't try to compile them until they are on the target system.

---

### Post by T2manner on 2008-06-27
well i have to have them, because i can't access the internet on the other machines.

---

### Post by st33med on 2008-06-27
That part is easy. Just download the correct files for OpenSUSE or whatnot and move it onto the USB. Example from the terminal with the file already downloaded to the Desktop:
```
cd ~/Desktop
cp <driver_install_file> /media/<USB-Name>
```

You will have to follow the instructions to install the file on the distro. It could be as easy as a double click.

---

### Post by T2manner on 2008-06-27
where do i get the driver files?

---

### Post by wdaniels on 2008-06-28
> **T2manner said:**
> where do i get the driver files?

That depends on the make and model of the wireless card. Do you know this already or do you need help to identify it?

---

### Post by T2manner on 2008-06-28
Well, when i go to the hardware drivers, it says Broadcom B43 Wireless Driver

---

