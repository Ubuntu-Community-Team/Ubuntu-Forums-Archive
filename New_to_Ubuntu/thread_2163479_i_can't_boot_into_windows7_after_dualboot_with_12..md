---
title: "i can't boot into windows7 after dualboot with 12.04"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by michaa on 2013-07-18
i decided to do the dual boot option when i installed ubuntu 12.04 amd64 on my toshiba satelite t135d with windows 7.
I split my 300 gb harddrive half and half. Then it installed and i turned of the computer so i could boot into windows 7. 
i tried the first windows option on grub 2 and it started the startup and restarted, so i tried it again and it restarted again. 
Next i tried the second windows option and it restarted by itself again. So i looked up the problem and i found out that i 
had to change windows to the default so i went to the terminal and typed "sudo gedit /etc/default/grub" (w/o parentheses)
i changed the GRUB_DEFAULT=0 to GRUB_DEFAULT=4 and then saved it and ran 'sudo update-grub' in the terminal. 
i re-booted and tried to get into windows and it restarted. 
when i do 'sudo update-grub' this pops up "/usr/sbin/grub-mkconfig: 1: /etc/default/grub: m#: not found"
i did the boot repair and i got this. [http://paste.ubuntu.com/5887697/](http://paste.ubuntu.com/5887697/) 
i have not tried to go into windows recovery, because i do not want windows to destroy ubuntu.

Thanks in advance for any answers

---

### Post by fantab on 2013-07-18
Try Windows recovery. Then later you can use boot-repair from Ubuntu LiveDVD/USB to reinstall Grub.
It appears that some Windows boot file may have got corrupted.

---

### Post by michaa on 2013-07-18
@fantab
Thank you for re-assuring me that windows recovery was going to fix it. It is fixed and i can now switch between ubuntu and windows.

---

