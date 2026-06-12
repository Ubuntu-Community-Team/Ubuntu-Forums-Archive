---
title: "&quot;Invalid signature&quot;message when trying to boot to windows from GRUB menu"
date: 2016-06-06
forum: New to Ubuntu
---

### Post by piansona on 2016-06-06
I have upgraded from my previous Ubuntu version to Ubuntu 14.04. With my previous GRUB menu I had a dual boot option between Ubuntu and Windows XP. After installing the new version of Ubuntu the new GRUB menu does not give me the option of booting my Windows programme. I have spent some time on the 'Ask Ubuntu' site trying to install a GRUB menu that will allow me the dual boot option but whatever values were place in the 40_custom file I continually received the error message "Invalid signature". I am a complete novice in the subject. I was helped to try to solve my problem by a very patient contributor on the 'Ask Ubuntu' site but unfortunately without success. Is anyone able to help me recover the pathway to my Windows installation?

---

### Post by yancek on 2016-06-06
The first thing to do is run:  sudo update-grub to see if xp is detected.  If that doesn't do the job or you've already done that unsuccessfully, get the boot repair software from the link below and run it from your Ubuntu.  Make sure you select the option to "Create BootInfo Summary" and post a link to the output here as that will provide detailed information on your system.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did you do an upgrade from an earlier version or a total new install?

---

### Post by piansona on 2016-06-07
Many thanks for your reply and for the link. The rescue software has done the job. i can now access my Windows programme. Very grateful

---

