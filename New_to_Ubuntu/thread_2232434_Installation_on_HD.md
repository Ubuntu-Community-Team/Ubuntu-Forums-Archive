---
title: "Installation on HD"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by Aaron_Gergye on 2014-07-01
I installed ubuntu on my HD then rebooted. I see no evidence that it has installed. I see unknown partitions but nothing else. I've attached the HD partition list on c:

---

### Post by yancek on 2014-07-01
A default windows system is not capable of identifying a Linux partition which is why they show up as unknown from your windows.  You have a 57GB partition and a 2.93GB partition which might be where you planned to install but they both show as empty, from windows anyhow.  How did you try to install Ubuntu?  and which release, the 14.04 or an earlier one?  Also, you apparently did not install the Ubuntu bootloader correctly or modify the windows bootloader to boot it.  Posting which version of windows you are using is also pertinent information.  You could boot the Ubuntu installation medium again and open a terminal and enter the following command and post the output here:  sudo fdisk -l

---

