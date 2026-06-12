---
title: "Minimal BASH-like line editing is supported"
date: 2017-12-18
forum: New to Ubuntu
---

### Post by zxy..zxy on 2017-12-18
I have a laptop that dual boots between ubuntu 16.04 and windows 10. It used to work before.

However,now I am getting an prompt "Minimal BASH-like line editing is supported"

I am following troubleshooting steps from here[ https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Here is the url [http://paste.ubuntu.com/26212303/](http://paste.ubuntu.com/26212303/)

Thank you in advance

---

### Post by yancek on 2017-12-18
Were there any changes made just prior to this problem to your software?  Any power loss or power surge?

Your boot repair doesn't show much.  It shows the various partitions on the SSD but there is no sign of any of the files for EFI or for Grub outside the 4GB flash drive you are using.  Apparently you left windows hibernated or fastboot on as boot repair was unable to run ntfsfix on your windows partition.  IT also shows only 1 OS and that is windows although it does show several Linux partitions in addition to the windows partitions.  

You could try mounting the first partition on the SSD to see if your EFI files are there.  Also, maybe try running boot repair again to see if you get more detailed output.  One wouldn't expect such a problem if no changes were made to software unless there was a serious hardware failure.

---

### Post by zxy..zxy on 2017-12-19
There were no specific changes made to the software. But the battery was low when I logged into Windows by typing exit in the grub> window.  And fastboot was on.

Can you explain more about the EFI files? I do not know much about them.

Thanks!

---

