---
title: "Getting Hardware Info"
date: 2010-07-15
forum: Programming Talk
---

### Post by MughalShahzad on 2010-07-15
Hi :)

I want to get hardware information like serial number of hard drive, mother board etc. using Java.

If some one has any idea/piece of code/web link please share with me.

Thanks & Regards
Shahzad

---

### Post by oldfred on 2010-07-15
No idea about Java. Can Java make system calls?

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
 udevadm info --export-db > file.txt

sudo dmidecode >bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

