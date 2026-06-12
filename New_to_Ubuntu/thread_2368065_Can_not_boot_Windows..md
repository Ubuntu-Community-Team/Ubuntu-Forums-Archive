---
title: "Can not boot Windows."
date: 2017-08-06
forum: New to Ubuntu
---

### Post by bluelightermighter on 2017-08-06
[Http://paste.ubuntu.com/25255512/](Http://paste.ubuntu.com/25255512/)

I cannot boot windows 7. I'm retarded. Please be gentle.

---

### Post by vasa1 on 2017-08-06
You might find this helpful: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by yancek on 2017-08-06
Your boot repair output shows 3 windows partitions, two with vista or win 7 and 1 with windows 8.  Is that what you have?  You have syslinux code in the MBR which often will work but your best option to repair your windows system is to use windows software, that would be the installation DVD from windows using the Repair option.  You might be able to download software to use to repair the "windows" code in the MBR.  If that doesn't work, I would definitely suggest you post at a windows forum.

There are quite a few members here who also use windows so you might be able to get help but you would need to post more info such as which windows you have and how the were installed (which first?) and whether the system ever worked if you had both 7 and 8 installed.

---

### Post by travis-falkenberg on 2017-08-06
You really need to provide more info on how it got to this situation.

sda1 is your windows recovery partition.

sda2 is a small partition so is probably for UEFI booting.

sda3 is your Windows OS partition which boot repair says is in an inconsistent state or the hardware is faulty. An inconsistent state may mean there are file system errors or maybe even a hibernation file present. 
You should attempt to fix this from a Windows install disk perhaps using chkdsk to attempt to repair the file system. I would suggest that this should be done when this is the only hard drive present in the computer. 
There are plenty of tutorials on how to do this in Windows related forums and web sites.

---

